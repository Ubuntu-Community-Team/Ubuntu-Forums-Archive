---
title: "Open-Xchange and Ubuntu??"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by Absolute Zero on 2006-05-16
Hello all, 
    I'm not rightfully sure if this is the proper place to be posting this topic but here goes.  I'd like to preface this post with the fact that I have been a Windows Sysadmin/programmer for the better part of 10 years and am moving over to Linux (half out of necessity and half out of frustration with windows)

I downloaded and installed Breezy without a problem, logged into X reset the root password and downloaded all available updates (about 160 or so).  I then went to the open X-Change website and read their howto on compiling and installing OX on Breezy so I began the process of installing postgre, apache, ant, tomcat, etc.  

Now I get all of these packages installed w/o error.  The next step of the process is to download OX, unpack it, configure it and make the install.  After following the suggested ./configure settings I recieve an: Unknown '--run' option and a suggestion to view missing --help followed by WARNING 'missing' script is too old or missing.

Now the process goes through and checks for all the necessary packages i then get an error saying Unable to locate tools.jar and that it should be in /usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/lib/tools.jar Buildfile: OX_COMPILE_CHECK.xml  (There is a copy of this file in my filesystem in /usr/lib/j2sdk1.5-sun/lib but, if i copy the jar file from there to the aforementioned directy, I get a java verify error)

This is then directly followed by "Unable to find a java c compiler; com.sun.tools.javac.Main is not on the classpath." Perhaps JAVA_HOME does not point to the JDK" i edited the root profile to this 

```
echo 'JAVA_HOME=/usr' >> /root/.profile
//tomcat, ant, ox, catalina home here
echo 'PATH=$PATH:$JAVA_HOME/bin:$CATALINA_HOME/bin:$ANT_HOME/bin:$OX_HOME/sbin' >> /root/.profile
echo export PATH JAVA_HOME CATALINA_HOME TOMCAT_HOME ANT_HOME OX_HOME >> /root/.profile
```

Does java home need to point, instead, to the JavaSDK? (/usr/lib/j2sdk1.5-sun)

Finally the install stops with rm: cannont remove 'OX_COMPILE_CHECK.class': No such file or directory.

I am stuck as to what to do, I had posted in the OX forums but no one seemed to have the answer to the problem =\

I have almost come to wits end with this as going through different Linux chats I was flammed to death for using Ubuntu (and subsequentially noone could/would point me in any good direction) (That's Irony for you isn't it? Windows users get flammed by Linux users because it is superior then you get a windows user to switch to Linux and then you get flammed because its a "gay" distro)

I am not asking for someone to give me a complete answer as to how to get this up and running, if all you can provide is a FAQ or a document thats ok I learned to read for a reason (though if you want to post the solution I wont complain =])  

In closing I hope I find these forums more helpful then the other sources I have sought out. =]

---

### Post by nalmeth on 2006-05-16
Jeez, what a sad state that when looking for help you get flamed for your distro of choice. Discraceful display of Zealotism. I suppose it's not entirely suprising, but you'll find it refreshing how toned down the zealotism is here.

I think your problem is that you don't have the essential compiling tools.

In the terminal, install them with:
sudo apt-get install build-essential

or since you have setup root already, if you're logged in you can exclude the sudo.

Root is disabled by default so that users can use sudo to gain admin priviledges instead, but you naturally, can do whatever the heck you want!

Hope this helps as a start anyway!

---

### Post by nalmeth on 2006-05-16
bump 
my reply isn't showing in forum, just want to show that a reply has been made.

My reply, in case it's not visible:
> Jeez, what a sad state that when looking for help you get flamed for your distro of choice. Discraceful display of Zealotism. I suppose it's not entirely suprising, but you'll find it refreshing how toned down the zealotism is here.

I think your problem is that you don't have the essential compiling tools.

In the terminal, install them with:
sudo apt-get install build-essential

or since you have setup root already, if you're logged in you can exclude the sudo.

Root is disabled by default so that users can use sudo to gain admin priviledges instead, but you naturally, can do whatever the heck you want!

Hope this helps as a start anyway!

---

### Post by Absolute Zero on 2006-05-18
nalmeth,
    Thank you for your reply!  When I first installed Ubuntu I downloaded all of the updates that were available ~161 or so files and restarted.  I logged back in and in the terminal I did
```
sudo apt-get update
sudo apt-get upgard
```

After I read your post I did as you suggested but there were only 3 packages that were updated and I still got the same error saying a Compiler could not be found.

I am trying to be proactive in learning how Ubuntu and its underlying systems work which is why I have taken so long to reply (You don't learn anything if you have somoene hold your hand the entire way) as such I did 
```
sudo gedit /root/xchange/open-xchange-0.8.0-6/INSTALL.xml
```

I looked over this file but, based on what I had added to the /root/.profile, all of the paths appeared to be correct.  Which leads me into this question, .profile is a config file nearest I can tell but what purpose does it serve to the operating system?

Also, the Install HOWTO that I am following enables the root account (which is obvious from my previous post) while on the IRC channel lastnight most users emplored me to use SUDO instead of su-, the HOWTO assumes that you are executing commands as root and, as such, all of your install files are downloaded to /root/xchange and one package is driectly installed there (the actual Xchange program directory)

Is the /root/ directory the equivelant to [systemdrive]\windows\system?  Do I need to place these files here for the system to work or could they be placed somewhere else?

...I am just going to stop typing now because this is becoming a long winded post and each question I ask poses another question!  Thanks in advance to anyone that can help =]

---

### Post by Khaine on 2006-05-19
There is a guide here you can follow:

[http://www.fantoma.it/extras/ubox_1.0/u510_oxc0806_en.html](http://www.fantoma.it/extras/ubox_1.0/u510_oxc0806_en.html)

---

### Post by oxy86 on 2006-08-02
Absolute Zero,

I had the same issue when installing OX in Dapper. 

All I did to fix that, was to remove the package gcj and all its dependencies using Synaptic (it is installed by default but it is not needed once you install Sun Java) and then I issued the following command:

ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/lib/tools.jar usr/local/ant/lib/

to link the missing tools.jar onto the lib directory of Ant. The last command is needed from Ant, as I read in its manual, and it presupposes that you use Sun Java 1.5.06 from the Dapper repositories, as I did. 

The first configuration messages about missing were of no importance. Disregard them. The compilation and installation went OK and now I am configuring PostgreSQL. 

For your information, I follow the instructions in the Linux Format 81 (actually translating them, because I work in the Greek Linux Format) combined with the more detailed ones in the page:
[http://www.fantoma.it/extras/ubox_1.0/u510_oxc0806_en.html](http://www.fantoma.it/extras/ubox_1.0/u510_oxc0806_en.html)

mentioned by another user earlier.

Cheers!

---

