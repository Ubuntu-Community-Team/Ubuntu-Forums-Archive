---
title: "Application Install Issue"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by pdoukas on 2007-09-08
I'm a new linux user but not a total idiot. Please bear with me. I am trying to install an application called dcm4che (located here: [http://www.dcm4che.org/](http://www.dcm4che.org/)). 

I am running ubuntu 6.x LAMP version with the ubuntu desktop so I can better make sense of things. My understanding was that I need a tar.gz to install using synaptic. However, after downloading the applications I noticed they were standard .zip files. I know of other organizations that have used ubuntu and and installed dcm4che but I'm hoping someone here can point me in the right direction over the course of the weekend.

Thanks!

Pete

---

### Post by dwhitney67 on 2007-09-08
Unzip the .zip file.

[FONT="Courier New"]$ gunzip <file>[/FONT]

where <file> is the name of the file you downloaded.  Then you can proceed from there.

---

### Post by Beggar on 2007-09-08
"My understanding was that I need a tar.gz to install using synaptic."

Dwightney is correct. Just wanted to clarify something, synaptic will install .deb (debian packages) not tarballs (this as you mentioned is just a compression scheme).

---

### Post by pdoukas on 2007-09-08
iI thought I had unzipped the file, rather "extracted" it to the desktop. i am using the gui, and nothing occurs after I "extract" it to the desktop other than it being extracted from the zip.

Pete

PS I also did what you said to do in a terminal session, this is the output:

administrator@telestorpacs:~$ gunzip /home/administrator/Desktop/dcm4chee-standalone-mysql-2.11.0.zip
gunzip: /home/administrator/Desktop/dcm4chee-standalone-mysql-2.11.0.zip: unknown suffix -- ignored
administrator@telestorpacs:~$

Pete

---

### Post by Beggar on 2007-09-08
Alright, a little more explanation is needed I guess. The file which you downloaded is just a compressed file, it has no installer like a deb, etc. So, after you extract the files (using either the command line, or the gui) navigate into the folder where you extracted the files and then you are going to need to install it. A little digging showed this as a java app so it should be relatively easy to setup. The best thing to do is look for a readme file in the extraction dir and follow any instructions you find.

---

### Post by pdoukas on 2007-09-08
would this be it....looks like it to me. Problem is this looks like all cmd line to me...any suggestions?

I have to go for the night I will take all options 

Pete

INSTALL INSTRUCTIONS FOR DCM4CHEE ARCHIVE:

=========================================



Minimum System Requirements

JDK 1.4.2 or higher. JDK 5 is required for upgrade of the 

  Audit Record Repository component to v3.0-SNAPSHOT

512 MB RAM

100 MB hard disk space (additional to archive storage disk space)  

400 MHz CPU



Supported Databases

PostgreSQL 8.1.x

MySQL 4.1+

Oracle 9i/10g

SQL Server

DB2 8.1+dcm4che



For image compression/decompression, dcm4chee 2.8.x utilize Sun's Java Advanced

Imaging Image I/O Tools 1.0_01. The binary distribution packages of dcm4chee

2.8.x already includes necessary JARs and native libraries for Windows and

Linux i586. For Solaris, you have to download the SW package from Sun

[[http://java.sun.com/products/java-media/jai/downloads/download-iio-1_0_01.html]](http://java.sun.com/products/java-media/jai/downloads/download-iio-1_0_01.html])

yourself and replace the Linux version of libclib_jiio.so in DCM4CHEE_DIST/bin/

from the JAI Image IO package for Solaris.



Installation Procedure:



1. Extract the binary distribution package of dcm4chee for the database

of your choice. Avoid using a directory that has a name that contains spaces

as installation directory.



2. Install the Database SW - if not already done. You also have to copy an

apropriate JDBC Driver for the Database to DCM4CHEE_DIST/server/default/lib/

- except for MySQL and PostgreSQL, which binary distribution packages of

dcm4chee already contains a JDBC driver. Also ensure, that DB access via

TCP/IP socket is enabled. E.g. PostgresSQL:



$PGDATA/pg_hba.conf:

# IPv4 local connections:

host    all         all         127.0.0.1/32          trust



3. Initiate the archive database instance: pacsdb using create DDL script

DCM4CHEE_DIST/sql/create.xxx.



E.g.: PostgreSQL

> export PGUSER=postgres

> createdb pacsdb

> psql pacsdb -f DCM4CHEE_DIST/sql/create.psql



E.g.: MySQL

> mysql -uroot

mysql> create database pacsdb;

mysql> grant all on pacsdb.* to 'pacs'@'localhost' identified by 'pacs';

mysql> \q

> mysql -upacs -ppacs < DCM4CHEE_DIST/sql/create.mysql



4. Adjust the Database connection configuration (host, port, DB name, user

password) of the archive:



DCM4CHEE_DIST/server/default/deploy/xxxx-ds.xml



according your Database configuration. 



5. Set environment variable JAVA_HOME to JDK location.



6. Adjust maximum allocation of heap memory: 

[Windows]: DCM4CHEE_DIST/bin/run.bat:

rem Sun JVM memory allocation pool parameters. Modify as appropriate.

set JAVA_OPTS=%JAVA_OPTS% -Xms128m -Xmx512m

[Linux/Unix]: DCM4CHEE_DIST/bin/run.conf

# Specify options to pass to the Java VM.

JAVA_OPTS="-server -Xms64m -Xmx200m -Djava.awt.headless=true ..



according available RAM and memory requirements of other processes on this node. 

E.g.: if only 512 MB RAM are available, you should decrease the default

value -Xmx512m on Windows to (e.g.) -Xmx300.



7. [Optional] At default configuration, all DICOM services are provided with

"DCM4CHEE" as Application Entity Title. Although it is possible to change the

default configuration later on the running application using the web interface,

it is more efficient and reliable, to replace "DCM4CHEE" by "YOUR_AET" in

DCM4CHEE_DIST/server/default/conf/xmdesc/*.xml using any utility provided by

your platform. E.g. GNU Linux:



> find DCM4CHEE_DIST/server/default/conf/xmdesc -exec \

           sed -i s/DCM4CHEE/YOUR_AET/g '{}' ';'

           



8. To test your installation, move to the DCM4CHEE_DIST/bin directory and 

execute the run.bat or run.sh script, as appropriate for your operating system.

Your output should look like the following and contain no error or exception 

messages:

 

=========================================================================



  JBoss Bootstrap Environment



  JBOSS_HOME: /home/gunter/dcm4chee-standalone-psql-2.8.2



  JAVA: /usr/java/j2sdk1.4.2_08/bin/java



  JAVA_OPTS: -server -Xms64m -Xmx200m -Djava.awt.headless=true 

   -Djava.library.path=. -Dprogram.name=run.sh



  CLASSPATH: /home/gunter/dcm4chee-standalone-psql-2.8.2/bin/run.jar:

    /usr/java/j2sdk1.4.2_08/lib/tools.jar



=========================================================================



10:28:10,301 INFO  [Server] Starting JBoss (MX MicroKernel)...

10:28:10,319 INFO  [Server] Release ID: JBoss [Zion] 4.0.3SP1 (build:

        CVSTag=JBoss_4_0_3_SP1 date=200510231054)

:

10:30:43,326 INFO  -> [JkMain] Jk running ID=0 time=0/83  config=null

10:30:43,352 INFO  -> [Server] JBoss (MX MicroKernel) [4.0.3SP1 (build:

        CVSTag=JBoss_4_0_3_SP1 date=200510231054)] Started in 2m:32s:823ms



9. Connect to the Web Interface at [http://localhost:8080/dcm4chee-web/](http://localhost:8080/dcm4chee-web/)

of the archive using any Web Browser (most tested are Mozilla-Firefox and

Microsoft Internet Explorer v6.x). You should get the User Login Screen.

Login in using default Administrator account 'admin', with password 'admin'.



10. Connect to JBoss's JMX Console at [http://localhost:8080/jmx-console/](http://localhost:8080/jmx-console/) and

login using also the Administrator account 'admin', with password 'admin'.



Follow the link "service=FileSystemMgt" to the configuration page for 

File System Management service under the "dcm4chee.archive" heading.



Invoke the operation addOnlineFileSystem(), with argument dirPath specifying

the directory, where the archive shall store received objects/images.



(If no Storage File System is configured, the archive will auto-configure

DCM4CHEE_DIST/server/default/archive as Storage File System, when receiving

the first object/image)



11. [Optional] At default configuration, received images are stored as received

- in particular, no compression is performed. Lossless compression of received

uncompressed images can be activated by attribute "CompressionRules" in the

configuration page for the Storage SCP Service (service=StoreScp). E.g. set it

to "JLSL", to compress all type of images received from any Storage SCU using

JPEG-LS Lossless codec.



12. [Optional] The directory used for caching generated JPEG representations

of archived images requested by Web Access to DICOM Persistent Objects (WADO)

can be specified by attribute "CacheRoot" in the configuration page for

the WADO Service (service=WADOService). 

Default: DCM4CHEE_DIST/server/default/wadocache.



The directory used for caching generated PDF representations of archived

Structured Report Documents requested by IHE Retrieve Information for Display

(RID) Services can be specified by attribute "CacheRoot" in the configuration

page for the RID Service (service=RIDService). 

Default: DCM4CHEE_DIST/server/default/ihe_rid_cache.



13. Send some object/images to the archive's Storage SCP, e.g. by using the 

send utility of the dcm4che 2.0 core package available at Sourceforge

([http://www.sourceforge.net/projects/dcm4che](http://www.sourceforge.net/projects/dcm4che)). E.g:



> dcm4che-2.0.6/bin/dcmsnd DCM4CHEE@localhost:11112 ~/mesa/storage/modality/MR



Refresh the Web Interface ([http://localhost:8080/dcm4chee-web/](http://localhost:8080/dcm4chee-web/)), which shall 

now show the the list of received studies.



Expand one study row to show contained series. Expand one of these series

to show contained instances. In the case of images, you can follow the image

icon on the right, to invoke a http WADO request for a JPEG presentation of

this image, which will be displayed in a separate browser window.



14. To test object retrieval, you need an external Storage SCP acting as

Move Destination, e.g. by using the receiver utility of the dcm4che 2.0 core:



> dcm4che-2.0.6/bin/dcmrcv 11113

13:55:14,782 INFO   - Start listening on 0.0.0.0/0.0.0.0:11113

Start Server listening on port 11113



You also need to configure an additional Application Entity Title identifying

this Move Destination using "AE Management" function of the Web Interface.

E.g. new AET

AE Title: DCMRCV

Hostname: localhost

Port:     11113



Switch back to the Study List ("Folder"), mark studies to retrieve using the

check box on the right, select "DCMRCV" as send destination in the combo box

above and click on the send button left from it.



15. If that works, you may stop the archive by Ctrl+C in the console you have

started it, and 

[Windows]: install it as Windows service executing install_service.bat

or 

[Redhat Linux]: copy the init script dcm4chee_init_redhat.sh to /etc/init.d/

and adjust it according your installation location of the archive and the JDK

and under which user the archive application shall run.



UPGRADE TO AUDIT RECORD REPOSITORY v3.0.1:

================================================

ATTENTION: Audit Record Repository v3.0.1 requires JDK 5. Java 1.4.2 is NOT

sufficient!



Upgrade Procedure:



1. Move to the installation directory of dcm4chee (DCM4CHEE_DIST) and extract

the binary distribution package for the upgrade of the Audit Record

Repository (upgrade-dcm4chee-arr-<DB>-3.0.1.zip).



2. Move to the DCM4CHEE_DIST/bin directory and execute the

uninstall-dcm4chee-arr-old.bat or uninstall-dcm4chee-arr-old.sh script.



You will find a DDL script for extending the DB schema with tables used by

dcm4chee-arr-3.0-SNAPSHOT at DCM4CHEE_DIST/sql/dcm4chee-arr-DB_NAME.dll. You

do NOT need to execute that manually. Needed tables will be automatical created

at first startup of the application with deployed dcm4chee-arr-3.0-SNAPSHOT. 



UPGRADE TO RFC-3881/DICOM Suppl95 AUDIT LOGGER v3.0.1:

===========================================================

ATTENTION: Upgrade to RFC-3881/DICOM Suppl95 Audit Logger requires to also

upgrade the Audit Record Repository to v3.0.1!



Upgrade Procedure:



1. Move to the installation directory of dcm4chee (DCM4CHEE_DIST) and extract

the binary distribution package for the upgrade of the Audit Logger

(upgrade-dcm4chee-auditlog-<DB>-3.0.1.zip) in the installation.



2. Move to the DCM4CHEE_DIST/bin directory and execute the

uninstall-dcm4chee-auditlog-old.bat or uninstall-dcm4chee-auditlog-old.sh

script.

---

### Post by Sef on 2007-09-08
> gunzip: /home/administrator/Desktop/dcm4chee-standalone-mysql-2.11.0.zip: unknown suffix -- ignored

Try this way - ```
gunzip: /home/administrator/Desktop/dcm4chee
```

See if that works.

---

### Post by pdoukas on 2007-09-09
tried the gunzip again with no luck.

I have it extracted on the desktop but i cannot figure out how to install it.

Pete

---

### Post by dwhitney67 on 2007-09-09
Then this has nothing to do with luck.... it seems that you were able to extract from the .zip.  Why don't you attach the zip file you have, and then tell us what the instructions say to do with it (or should I say the contents).

---

### Post by pdoukas on 2007-09-09
I cannot attach the file as the contents of the folder are 32MB uncompressed.

The .zip for DCM4CHE can be downloaded here:  [http://downloads.sourceforge.net/dcm4che/dcm4chee-standalone-mysql-2.11.0.zip?modtime=1183558108&big_mirror=0](http://downloads.sourceforge.net/dcm4che/dcm4chee-standalone-mysql-2.11.0.zip?modtime=1183558108&big_mirror=0)

Lastly, there was an installation readme that I will post as an attachment but I also posted it earlier in this thread.

I'd love to do this without using the GUI but I thought that it was easier doing it this way due to my lack of experience using linux. I'm very flexible and willing to try to install it the most efficient way.

Thanks for everyone's assistance.

Pete

---

### Post by schorsch on 2007-09-09
Don't use "gunzip" but "unzip" as it is a .zip file and not a .gz file. Have you already installed the package "unzip"?
```
sudo apt-get install unzip
```

---

### Post by pdoukas on 2007-09-09
I have already extracted the contents to the desktop, do I really need to get the "unzip"?

Pete

Also, since everyone is telling me to do things cmd line should I get out of the GUI?

---

### Post by schorsch on 2007-09-09
> **pdoukas said:**
> I have already extracted the contents to the desktop, do I really need to get the "unzip"?
Well if you have a folder called "dcm4chee-standalone-mysql-2.11.0" on your desktop right now you do not need to install this package as it seems you have it already installed. Change into this folder and then into the subfolder "doc" where you can get some infos how to setup the application. As it is a precompiled java app you do not have to do anything like "make".....

---

### Post by pdoukas on 2007-09-09
This is where I am stuck at, I have gone into the folder, pulled out the readme, and I am completely lost from there. I even posted it earlier in hopes someone would hold my hand a little bit nd walk me through it because I have to be honest, it's rather confusing to me. I've been an avid windows user for 15 years (as I duck from the hoards of bricks that have just been tossed at me!!)

Pete

---

### Post by schorsch on 2007-09-09
Uhm ... now you reached the point where you have to leave the GUI and take a step into the miracles of the CLI a.k.a. as terminal :-) Sorry, I have no idea how the instructions in the INSTALL file can be realized by using a GUI, but, hey, once you get used to to CLI you will work with it much faster than with the GUI so why not start now?
Let's first check if you meet the mentioned requirements. As far as I can see you need a JDK and a database server. As I do not know anything about postgres I will choose mySQL. Please check with the following commands:
```
dpkg -l | grep -i jdk
dpkg -l|grep mysql
```
If you want to use postgres just substitute "mysql" with "postgres" (I will not mention this in the future again :-) ).
If you get not output from the commands above you can install the software via synaptic:
```
sun-java6-jdk
mysql-server
```
After that we will go to the next steps ....

---

### Post by pdoukas on 2007-09-09
Hi Schorsch,

I want to continue using you for assistance! I can do this command line, I am not afraid :).

While I have been waiting on replies I have been teaching mself somethings so here is waht I found:

1) I can use cmd line to "wget" the .zip file in question. I have also learned how to get the unzip utility and unzip the contents. Please correct me if I am wrong but do the contents go into the tmp folder?

I want to learn how to do this all cmd line, so I am going to be away for about an hour install the LAMP version of the ubuntu server without the gui. 

I can do this, I know I can do this :)

tchuss

Pete

(I used to live in Nurnberg for 5 years but my German is bad these days!)

---

### Post by dwhitney67 on 2007-09-09
I downloaded the .zip file.  Why it was slapped into /tmp (as opposed to my chosen download directory) is a mystery.

Anyhow, I copied the zip file to a directory of my choosing.  Then

$ unzip dcm4chee-standalone-mysql-2.11.0.zip
$ cd dcm4chee-standalone-mysql-2.11.0/doc

- This is optional.  I normally use 'vi' to read files.
$ dos2unix INSTALL

Then follow the instructions for Linux (ignore those for Windows and Solaris).

Step 1:  Unpack the zip.  Done already
Step 2:  Install a database.  Presumably you already have mySQL installed.
Step 3:  Create pacsdb database within mySQL.  Us the SQL statements given as a hint on how to create the database.
Step 4:  Edit ../server/default/deploy/mysql-ds.xml (this step might not be needed)
Step 5:  Add JAVA_HOME environment variable as indicated to your ~/.bashrc; then source ~/.bashrc
Step 6:  ../bin/run.conf
Step 7:  Optional
Step 8:  sh ../bin/run.sh

I hope that clarifies things.  IMO, this dcm4chee product seems crappy in the sense that the installation instructions are not written clearly and that there are too many configuration steps which leaves the reader scratching his head.  I hope this product meets your needs.  I for one would not bother with it because it almost seems like a "beta" release.

---

### Post by schorsch on 2007-09-09
Hi Pete,

If you unzip a zip-file on your desktop with a double-click you have the option where to unzip it to. if you unzip some zip-file via the command line it gets uncompressed in your current directory. There is a command option which tells the unzip command in a terminal that you want to extract the files to another directory, too.
Well, if you install a LAMP version of Ubuntu right now you choose the mysql way ... 
If you want to use a GUI on top of the server install (just to make things easier at the start ...) install the package "ubuntu-desktop". 

Tschüss

schorsch

---

### Post by pdoukas on 2007-09-09
Schorsch - I have reinstalled ubuntu server 6.x and no gui. I will be using mysql version and i am about begin download and then unzip.

Dwhitney - Yes then I was correct, it also forced me to download into tmp directory. I will follow your examples as well and post results as soon as something occurs or craps out. 

Pete

---

### Post by schorsch on 2007-09-09
Don' t get me wrong here: There is nothing wrong about a GUI! And I really doubt you will be able to run a java app without a GUI ..... The installation might work although ....

---

### Post by pdoukas on 2007-09-09
Ok here we go. I was able to download the app using wget and it downloaded into my top level directory. What I mean by that is I have given myself the name admin and it is in that directory.

I assume I should move it to another directory. What is the best directory to move it to and then, what is the best directory to extract into. Or is this something that is etched into my head due to being a windows user?

Pete

---

### Post by schorsch on 2007-09-09
As this an application that is not maintained by the OS but by an user you could leave it in your home directory. Another place would be "/usr/local". As long as not system dirs as /usr, /bin, /sbin or something like this are involved you are pretty free where to put it. I would leave the zip file in your home directory and extract it to /usr/local/dcm4chee-standalone-mysql-2.11.0 ... or something like that.

---

### Post by pdoukas on 2007-09-09
Ok, I have it extracted at /usr/local/dcm4chee-standalone-mysql-2.11.0

I now need to go to step 3. I have found the create.mysql file but I am unsure as to how to make the changes or continue. Am I to use vi to edit the file?

Pete?

---

### Post by schorsch on 2007-09-09
Remember, I had no experience with this app before .....
I guess you don't have to edit the file. Is your mysql server up and running? If not:
```
sudo /etc/init.d/mysql start
```
The default installation of mysql has no password but we can change it afterwards.
Then just type the commands nearly as mentioned in the INSTALL file:
```
mysql -u root
mysql> create database pacsdb;
mysql> grant all on pacsdb.* to 'pacs'@'localhost' identified by 'pacs';
mysql> \q
mysql pacsdb -upacs -ppacs < /usr/local/dcm4chee-standalone-mysql-2.11.0/sql/create.mysql
```
There are some errors in the INSTALL file which I corrected (?) to meet your environment. The leading "mysql>" shows that you are connected to the database server. Otherwise when the line starts with "mysql" this is a command.

---

### Post by pdoukas on 2007-09-09
Ok now I am on step 4.

Mentioning step 3. I don't want you to think I am just doing everything you say and not understanding what I am doing. Essentialy in the last step I created the DB using the mysql editor. after I left the editor I issued a myssql command specifying "something" in the pacsdb I had just created. As I am going alone I am writing all of this down in terms that someone not familiar with any linux could understand. 

Regarding step 4  I hoestly do not understand what that means.

Pete

---

### Post by dwhitney67 on 2007-09-09
> **pdoukas said:**
> Ok now I am on step 4.

Mentioning step 3. I don't want you to think I am just doing everything you say and not understanding what I am doing. Essentialy in the last step I created the DB using the mysql editor. after I left the editor I issued a myssql command specifying "something" in the pacsdb I had just created. As I am going alone I am writing all of this down in terms that someone not familiar with any linux could understand. 

Regarding step 4  I hoestly do not understand what that means.

Pete

Neither do I, other than the part within the instructions that say to ensure that everything is "correct" within the file.  Since the instructions do not provide any hints as to what is considered "correct", I think you should assume that the contents are ok and continue on with Step 5.

---

### Post by schorsch on 2007-09-09
> **pdoukas said:**
> Ok now I am on step 4.

Mentioning step 3. I don't want you to think I am just doing everything you say and not understanding what I am doing. Essentialy in the last step I created the DB using the mysql editor. after I left the editor I issued a myssql command specifying "something" in the pacsdb I had just created. As I am going alone I am writing all of this down in terms that someone not familiar with any linux could understand. 

Regarding step 4  I hoestly do not understand what that means.

Pete

Hey, that's great! And I didn't want to offend you! But in the past I got the experience that many users just do a simple copy-paste without knowing  what the commands will do and are happy if it works afterwards without knowing WHAT has done the work. So I apologize for that ....
I checked the file mentioned in step 4: If you entered the default values as mentioned in the INSTALL file there should be no need to edit this file. Just go to the next step ...

Unfortunately I have to leave now so perhaps someone else will pick up this thread ... or we will meet another day ;-)

---

### Post by schorsch on 2007-09-09
.... but I was able to connect to the app via a browser window after following the next steps so it should have worked on your side, too. But you need a GUI to do this ......

---

### Post by pdoukas on 2007-09-09
Schorsch - Sorry to see you go, thank you and dwhitney for getting me here. 

dwhitney, sorry took so long but i was looking at the xml file to see if I could find the parameters or and statements verifying that both you and schorsch were saying that I shouldn't make any changes.

I am moving onto 5
... it looks confusing I need to google what it means by setting environment variale.   looks simple enough though.

Pete

I've read ahead and I can finish this up, but I am stuck at step 5 in understanding what this means. (Set environment variable JAVA_HOME to JDK location. 
   Add JAVA_HOME environment variable as indicated to your ~/.bashrc; then source ~/.bashrc)

After that everything else makes since to me. I need to adjust the memory and do not want to change my ae title.

Pete

---

### Post by pdoukas on 2007-09-09
Ok I am definitley stuck at the folowing stage:

Set environment variable JAVA_HOME to JDK location. 

Add JAVA_HOME environment variable as indicated to your ~/.bashrc; then source ~/.bashrc

Those two items are the same concept, I know. I'm trying to do the following (1) locate the correct directories to add said variable to the correct .bashrc files, but I cannot find them.

I'm sure there is a simple step I am missing.

Pete

---

### Post by dwhitney67 on 2007-09-09
> **pdoukas said:**
> Ok I am definitley stuck at the folowing stage:

Set environment variable JAVA_HOME to JDK location. 

Add JAVA_HOME environment variable as indicated to your ~/.bashrc; then source ~/.bashrc

Those two items are the same concept, I know. I'm trying to do the following (1) locate the correct directories to add said variable to the correct .bashrc files, but I cannot find them.

I'm sure there is a simple step I am missing.

Pete

The .bashrc file is a hidden file and it is located in your home directory.  That is why I preceded the file name with the ~/.  Thus run this command to edit the file:

[FONT="Courier New"]$ gedit ~/.bashrc[/FONT]

Then insert a line similar to the following:

[FONT="Courier New"]export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun[/FONT]

After saving the file, run this command:

[FONT="Courier New"]$ source ~/.bashrc[/FONT]

You can confirm the setting for JAVA_HOME by running this command:

[FONT="Courier New"]$ env | grep JAVA_HOME[/FONT]

I hope this helps.

---

### Post by pdoukas on 2007-09-09
ok if I run that command from my "admin" directory i get the following:

bash: gedit: command not found.

However, I can open it in vi?

These are the commands I used:

admin@telestorpacs:~$ gedit ~/.bashrc

and 

admin@telestorpacs:~ gedit .bashrc

Also, is that the only bash location I need to make that change to or is there a global environment variale bashrc file somewhere I need to look for as you suggested earlier.


~/.bashrc and source ~/.bashrc   and I assume the source ~/.bashrc is actually /usr/local/dmc4chee-standalone-mysql-2.11.0  but i cant find a bashrc file at that level.

Thanks,

Pete

---

### Post by dwhitney67 on 2007-09-09
Sorry.  Had I know you know vi I would have suggested that in lieu of gedit.  I'm surprised though that gedit is not included on your system.  A topic for another day.

If you want to provide the JAVA_HOME to all users, then I believe you can include the "export" statement in the **/etc/bash.bashrc** file.  Just slap the statement in at the end of the file.

You can then confirm it is automagically sourced in by logging into another account by verifying the setting of JAVA_HOME.

---

### Post by pdoukas on 2007-09-09
I don't know vi, just learned a little bit today and yesterday but feel comfortable using it as a text editor.

So my assumption is that I will do the following:

sudo vi .bashrc and then insert the following:

export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun

then follow the rst of your instructions.

Thanks,

Pete

---

### Post by pdoukas on 2007-09-09
after i tried that and tried to run it I got this in the output:


run.sh line 172; JAVA: COMMAND NOT FOUND

dI i NEED TO INSTALL JAVA......and if so where do I do a wget to get it?

Pete

---

### Post by dwhitney67 on 2007-09-09
Test to see if java and javac are on your system:

[FONT="Courier New"]$ which java
$ which javac[/FONT]

They both should reside in /usr/bin.  Before jumping to conclusions as to whether you have them or not, please check your PATH environment variable to ensure that /usr/bin is in your path.

[FONT="Courier New"]$ env | grep PATH[/FONT]

If you determine that you do not have them, then get them and other Java related stuff using this command:

[FONT="Courier New"]$ sudo apt-get install sun-java5-jdk sun-java5-plugin sun-java5-fonts[/FONT]

If the answer is yes, that is you do have java and javac, then perhaps, and this is a stretch, all that is needed is to adjust your JAVA_HOME to point to:
[FONT="Courier New"]
export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun/bin[/FONT]

---

### Post by pdoukas on 2007-09-11
dwhitney - 

I was out of town yesterday, sorry for a late reply.

This is the output of what you had me do:

root@telestorpacs:/# cd usr/bin
root@telestorpacs:/usr/bin# which java
root@telestorpacs:/usr/bin# which javac
root@telestorpacs:/usr/bin# su admin
admin@telestorpacs:/usr/bin$ which java
admin@telestorpacs:/usr/bin$ which javac
admin@telestorpacs:/usr/bin$ env | grep PATH
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
admin@telestorpacs:/usr/bin$ cd ..
admin@telestorpacs:/usr$ cd ..
admin@telestorpacs:/$ sudo apt-get install sun-java5-jdk sun-java5-plugin sun-java5-fonts
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jdk
admin@telestorpacs:/$


I have 2 options, we can continue trying this where i could actually learn something........if you have patience. OR, I've been told that a developer is finishing up the deb packages for the application and they will be available this weekend for me to install. 

Pete

---

### Post by schorsch on 2007-09-11
Hi Pete

I am back again, too .. :-)

To install the java packages you have to enable the multiverse repos. You still have no GUI  installed, right?
Then try:
```
sudo nano /etc/apt/sources.list
```
and remove the leading "#" from every line that has multiverse in it. After that do
```
sudo apt-get update
```
and the java packages should be available for installation. BTW ... on my machine I installed java6 to test the installation of your software but please don't ask me which should be the preferred one ... ;-)

---

### Post by pdoukas on 2007-09-12
Schorsch and Dwhitney - 

I want to thank you for your assistance. I have been able to get the application to install and run. I want to close this thread, but before I do, I have learned a few things and will continue to do so.

Thanks,

Pete

---

### Post by dwhitney67 on 2007-09-12
That's great.  I have friend that will be pulling his fingernails out this weekend with an equally complicated install... he wants to install Oracle.

Personally, I would have given up long ago.  Kudos for your perseverance.

---

