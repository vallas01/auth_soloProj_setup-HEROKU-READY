# auth_soloProject (set up Ready!)

FIRST: mirror this repository (DO NOT EDIT)

1. Open Git Bash.  
2. Create a bare clone of the repository.  
$ git clone --bare https://github.com/exampleuser/old-repository.git  
3. Mirror-push to the new repository.  
$ cd old-repository.git  
$ git push --mirror https://github.com/exampleuser/new-repository.git  
4. Remove the temporary local repository you created earlier.  
$ cd ..  
$ rm -rf old-repository.git  



  
  
SECOND:
npm install  

THIRD: Set up Heroku

Navigate to your application's Heroku dashboard.

Under the "Resources" tab in your new application, click "Find more add-ons" and add the "Heroku Postgres" add-on with the free Hobby Dev setting.

Login to Heroku in your terminal by running the following:
    heroku login

Add Heroku as a remote to your project's git repository in the following command and replace <name-of-Heroku-app> with the name of the application you created in the Heroku dashboard.

    heroku git:remote -a <name-of-Heroku-app>

Under "Settings" there is a section for "Config Vars". Click the Reveal Config Vars button to see all your production environment variables. You should have a DATABASE_URL environment variable already from the Heroku Postgres add-on.

Add environment variables for JWT_EXPIRES_IN and JWT_SECRET and any other environment variables you need for production.

You can also set environment variables through the Heroku CLI you installed earlier in your terminal. See the docs for Setting Heroku Config Variables.

Push your project to Heroku.
    git push heroku

MAKE SURE TO MIGRATE DB AND SEED BEFORE TESTING!!!

To migrate the production database, run:
    heroku run npm run sequelize db:migrate

To seed the production database, run:
    heroku run npm run sequelize db:seed:all
