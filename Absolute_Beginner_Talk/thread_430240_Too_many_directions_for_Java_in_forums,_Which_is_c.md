---
title: "Too many directions for Java in forums, Which is correct?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by stevenrushing on 2007-05-01
I have found so many different instructions for installing java.  Which am I supposed to use to make it work?

I have seen instructions for using the add/remove dialog box, for using synaptic.  I have seen instructions for using the command line.  

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/java.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/java.html)

That is there.  

Which of all these is correct?  I am running 6.10.  Could someone please point me in the right direction?

---

### Post by starcraft.man on 2007-05-01
Easiest way to install latest java is just from Repos.

Run this in the terminal (Terminal is in Applications > Accessories > Terminal):
```

sudo aptitude install sun-java6-bin sun-java6-jre 

```

If you haven't added all the extra repos, you will have to do so first. Read [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") please. 

I assume your running feisty, if your on edgy or dapper use links in my sig. 

Hope that helps and read the guide for more info in general.

---

### Post by Sef on 2007-05-01
Easy way to install Java on Feisty Fawn:

Applications > Add/Remove > Set top right bar to 'All Available Applications' > Search > type sun java 6 > click on top choice "Sun Java Web Start' > click apply > click apply > follow directions to finish.

> If you haven't added all the extra repos, you will have to do so first. Read here please.


The repos, Universe and Multiverse, are open by default in Feisty.

> Run this in the terminal (Terminal is in Applications > Accessories > Terminal):
Code:

sudo aptitude install sun-java6-bin sun-java6-jre



First type code this in the terminal:

```
sudo aptitude update
```

first.

---

### Post by stevenrushing on 2007-05-02
I followed the instructions and this was my output:

ubuntu@ubuntu:~$ sudo aptitude update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]             
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release [57.2kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [32.4kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Fetched 89.6kB in 2s (38.7kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo aptitude install sun-java6-bin sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  gsfonts-x11 java-common libltdl3 odbcinst1debian1 unixodbc 
The following packages have been kept back:
  update-manager update-manager-core 
The following NEW packages will be installed:
  gsfonts-x11 java-common libltdl3 odbcinst1debian1 sun-java6-bin 
  sun-java6-jre unixodbc 
0 packages upgraded, 7 newly installed, 0 to remove and 2 not upgraded.
Need to get 33.1MB of archives. After unpacking 94.8MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main java-common 0.25ubuntu2 [76.9kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main libltdl3 1.5.22-4 [168kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main odbcinst1debian1 2.2.11-13 [64.1kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main unixodbc 2.2.11-13 [269kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse sun-java6-bin 6-00-2ubuntu2 [26.2MB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse sun-java6-jre 6-00-2ubuntu2 [6324kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main gsfonts-x11 0.20build1 [10.6kB]     
Fetched 33.1MB in 3m49s (144kB/s)                                               
Preconfiguring packages ...
Selecting previously deselected package java-common.
(Reading database ... 91545 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.25ubuntu2_all.deb) ...
Selecting previously deselected package libltdl3.
Unpacking libltdl3 (from .../libltdl3_1.5.22-4_i386.deb) ...
Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-13_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-13_i386.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-00-2ubuntu2_i386.deb) ...
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package gsfonts-x11.
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.20build1_all.deb) ...
Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

Setting up gsfonts-x11 (0.20build1) ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

Setting up sun-java6-jre (6-00-2ubuntu2) ...

Setting up sun-java6-bin (6-00-2ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java6-bin (6-00-2ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 sun-java6-bin
ubuntu@ubuntu:~$ 



Any Ideas?

---

### Post by fakie_flip on 2007-05-02
The best way to install Java is by using the packages in the repos. The instructions you found were for installing Java before Java became available in the repos. It is much easier to install the packages of Java using Synaptic or apt-get. There is more than one way to install Java, but I prefer to install it the easy way by getting it from the repos. Do not forget to enable the Universe repository first, or else you will be unable to install Java from apt-get or Synaptic.

---

### Post by fakie_flip on 2007-05-02
I searched the forums, and found two other threads of people having the same error as you. There are no solutions yet, but you should subscribe to those threads, so you will be notified by email when someone replies with a solution. This may be a bug in Feisty that will be fixed soon. Here are the threads you should subscribe to.

[http://ubuntuforums.org/showthread.php?t=429189&highlight=libjli.so+java](http://ubuntuforums.org/showthread.php?t=429189&highlight=libjli.so+java)

[http://ubuntuforums.org/showthread.php?t=414851&highlight=libjli.so+java](http://ubuntuforums.org/showthread.php?t=414851&highlight=libjli.so+java)

---

### Post by fakie_flip on 2007-05-02
You should try installing libjline-java, and then reinstall Java.

```
sudo aptitude install libjline-java

sudo aptitude reinstall sun-java6-bin sun-java6-jre
```

Next time you only need to type this and the bin package will be installed automatically.

```
sudo aptitude intall sun-java6-jre
```

---

### Post by stevenrushing on 2007-05-02
Thank you, I have subscribed to the threads...
When I tried to install via synaptic, this is what I got... 

E: sun-java6-bin: subprocess post-installation script returned error exit status 127
E: sun-java5-bin: subprocess post-installation script returned error exit status 2
E: sun-java5-plugin: dependency problems - leaving unconfigured


Also, there is text that I can't figure out how to copy in this picture... 

[IMG]http://rushingaround.com/pictures/error.jpg[/IMG]

---

### Post by stevenrushing on 2007-05-02
ubuntu@ubuntu:~$ sudo aptitude install libjline-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  update-manager update-manager-core 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up sun-java5-bin (1.5.0-11-1ubuntu2) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-11-1ubuntu2); however:
  Package sun-java5-bin is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
Setting up sun-java6-bin (6-00-2ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 sun-java5-bin
 sun-java5-plugin
 sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java5-bin (1.5.0-11-1ubuntu2) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-11-1ubuntu2); however:
  Package sun-java5-bin is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
Setting up sun-java6-bin (6-00-2ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 sun-java5-bin
 sun-java5-plugin
 sun-java6-bin
ubuntu@ubuntu:~$

---

### Post by fakie_flip on 2007-05-02
This has got to be a bug with Feisty. You are using Feisty right? You could check if this bug has been reported at Launchpad or create your own bug report and the developers will respond by email. Usually when they find out about these things, a bug fix will come in the updates, and the problem will be gone.

---

### Post by fakie_flip on 2007-05-02
Everything is working here, but that's probably because I already had java installed before I upgraded to Feisty. I did not install from a Feisty cd. I just upgraded Edgy to Feisty and already had java working. Here is what I get.

```
chris@ubuntu:~$ sudo apt-get install sun-java6-jre
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@ubuntu:~$ java
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client       to select the "client" VM
    -server       to select the "server" VM
    -hotspot      is a synonym for the "client" VM  [deprecated]
                  The default VM is client.
                  
    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                    see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image
chris@ubuntu:~$ 
```

---

### Post by abeverley on 2007-06-04
With regards to the error "while loading shared libraries: libjli.so: cannot open shared object file" error message, I got round this by:

cd /lib
ln -s ../usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/jli/libjli.so libjli.so

It's probably not the correct way to fix it, but it worked for me.

---

