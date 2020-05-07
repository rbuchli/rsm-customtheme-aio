# Alfresco RSM Custom Theme AIO Project - SDK 4.1

This is an All-In-One (AIO) project for Alfresco SDK 4.1.
It creates a new Theme (rsm-customtheme), removes some Menu Items for non-admins and sets a new background image for the login-page.

Run with `./run.sh build_start` or `./run.bat build_start` and verify that it

 * Runs Alfresco Content Service (ACS)
 * Runs Alfresco Share
 * Runs Alfresco Search Service (ASS)
 * Runs PostgreSQL database
 * Deploys the JAR assembled modules
 
All the services of the project are now run as docker containers. The run script offers the next tasks:

 * `build_start`. Build the whole project, recreate the ACS and Share docker images, start the dockerised environment composed by ACS, Share, ASS and 
 PostgreSQL and tail the logs of all the containers.
 * `build_start_it_supported`. Build the whole project including dependencies required for IT execution, recreate the ACS and Share docker images, start the 
 dockerised environment composed by ACS, Share, ASS and PostgreSQL and tail the logs of all the containers.
 * `start`. Start the dockerised environment without building the project and tail the logs of all the containers.
 * `stop`. Stop the dockerised environment.
 * `purge`. Stop the dockerised container and delete all the persistent data (docker volumes).
 * `tail`. Tail the logs of all the containers.
 * `reload_share`. Build the Share module, recreate the Share docker image and restart the Share container.
 * `reload_acs`. Build the ACS module, recreate the ACS docker image and restart the ACS container.
 * `build_test`. Build the whole project, recreate the ACS and Share docker images, start the dockerised environment, execute the integration tests from the
 `integration-tests` module and stop the environment.
 * `test`. Execute the integration tests (the environment must be already started).

# Installing the Module
## Installing Alfresco Platform Module
* stop tomcat
* cd /usr/share/tomcat/webapps
* rm -rf alfresco
* cp alfresco.war alfresco.war-SAVE
* mkdir tmp
* cp alfresco.war tmp
* unzip alfresco.war
* cd WEB-INF/lib
* add the jar file generated here for platform
* cd ../..
* rm -f alfresco.war
* zip -r alfresco.war *
* mv alfresco.war ..

## Installing Share Module
* stop tomcat
* cd /usr/share/tomcat/webapps
* rm -rf share
* cp share.war share.war-SAVE
* mkdir tmp
* cp share.war tmp
* unzip share.war
* cd WEB-INF/lib
* add the jar file generated here for share
* cd ../..
* rm -f share.war
* zip -r share.war *
* mv share.war ..

OR: use the amps ...
systemctl start tomcat