---
title: "n00b here"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by spin1078 on 2005-11-10
Ok so I could search all day long for each problem Im running into.  Fact is Im a windows vet, but dont know dick about Linux.  I installed Ubuntu bout 3 days ago, and have picked up little, but not enough.  Lets face it, I feel like a retarded kid in calculus.  Fact is the gui parts all easy, how dumb ya have to be not to figure it out.  Thing is the Terminal, or bash as I may mistakingly call it.  Its driving me insane.  I was a DOS vet as well.  Started out in version 3.0 so Im used to nonGUI, but damn, its like relearning everything you know pretty much.  Just cause DIR works doesnt mean things are the same.

So blah blah, here it is, can you give me somewhere to look for Ubuntu ways of doing things.  Ive noticed things dont work the same way in each distro.  For 9instance, I downloaded Limewire, just as a test to install.  I get the package and everything open but I need Java2 1.4.x or higher.  So I get java, and chmod +x the file, ./the file, it goes through an unpacking (and install I guess) and puts a bunch or stuff in a folder.  Now with all of this, does nothing.  Limewire still sits like a parapalegic in the pool saying it needs java. 

So n00b major question 1.  
what do you do after you get a tarball, gzip or bin file all expanded and you have just a bunch of folders that start with /usr?  do they go somewhere?  what?

2nd I expanded the Java pkg originally as root.  now its on my desktop in a folder and I cant delete the folder.  its locked, permission denied.  the Chmod chown is driving me nuts, and there no gui way to do root tasks THAT I KNOW OF.

i mean seeing that i never touched Linux til 3 days ago, id say i have learned alot.  Im still an infant here though.  I have a little Mac experience which has kept me sane and patient but I just give up.  I have to ask for help.

and hello btw, Im Brad

---

### Post by Kapre on 2005-11-10
[QUOTE=spin1078]So n00b major question 1.  
what do you do after you get a tarball, gzip or bin file all expanded and you have just a bunch of folders that start with /usr?  do they go somewhere?  what? [/quote]

First of all, Welcome to Ubuntu (Linux)!!! I'm not a linux guru but I know a tiny bit about it so I would try to help you out.

The tarball,gzip are compressed files (much like winzip, pkzip, winrar). It depends on what these files are (apps, add-ons, pics, icons, etc)

> 2nd I expanded the Java pkg originally as root.  now its on my desktop in a folder and I cant delete the folder.  its locked, permission denied.  the Chmod chown is driving me nuts, and there no gui way to do root tasks THAT I KNOW OF. 

My approach on this one is going root (which I know is not the best thing to do) - there will be others who can give you a better idea.

> i mean seeing that i never touched Linux til 3 days ago, id say i have learned alot.  Im still an infant here though.  I have a little Mac experience which has kept me sane and patient but I just give up.  I have to ask for help.
and hello btw, Im Brad

We are all in this community and we try to help each other out. Just post and help is on the way.

BTW, for a list of command in Terminal, you can click on my signature (helpful bash(.

K

---

### Post by mlomker on 2005-11-10
[How-to for installing java]("http://www.ubuntuforums.org/showthread.php?t=70428").

---

### Post by n0ah420 on 2005-11-10
Since root has no password by default you may want to stick to the sudo command.  In Ubuntu you can use sudo to execute a single command as root (also safer this way).  For example:

```
sudo rm -r /home/n0ah/Desktop/folder/
```

It will ask you for your password.  You can also use rmdir instead of rm if the directory is empty.  My main suggestion for new users in bash is to get used to the man command.  man rm will tell you the rm syntax options.  Hope that helps

---

### Post by nrwilk on 2005-11-10
This is a pretty good introduction to basic shell use:
```

http://ubuntuforums.org/showthread.php?t=73885

```

---

### Post by spin1078 on 2005-11-10
ok, I have already changed the root password.  I use the sudo -s for working as root.
I know how to unpack tarballs and gzipped tarballs.  I also have figured out how to execute the bin for java.  now i have a folder of all kinds of files.  So i assume its loaded. 

ok to start off I wanted to try installing something.  I like music so i picked limewire.  A.) if theres something better and easier for linux im down to try it.  b.) i still would rather learn how to install Limewire rather that skip it for something easy.  i think it will help for experince.  

when I converted the limewire RPM to a DEB, i unpackage it and get a folder with a bunch more folders in it.  /usr in it are /lib, /bin, and something else, im not lookin at it im lazy.  now i found the SH file runLime.sh, when i execute it ./runLime.sh i get all these things sayin i need java 2 1.4.x or higher.  I installed 1.5.0.05

Now what?

as for root, i can be root, but the chmod, chown, and rmdir arent working for that wrong directory.  rmdir says directory not empty, and im not going to attempt to delete all that crap one at a time.

also, there a usual place you like to store all your stuff.  i made a folder in the home/<profile> folder called 'files' and the case sensitive thing drives me insane as does the thing where a folder on my desktops called 'My Stuff' but is in the bash as My\ Stuff


as for basic shell use, i went on Linux.org and went thorugh the beginners course.  thing is there is no course for learning specific distros.  from what i see no one is really 100 percent alike.

---

### Post by nrwilk on 2005-11-11
[QUOTE=spin1078]as for basic shell use, i went on Linux.org and went thorugh the beginners course.  thing is there is no course for learning specific distros.  from what i see no one is really 100 percent alike.[/QUOTE]

As I understand it, there aren't very many differences between distros when using the same shell.  The big differences come from the different command-line programs and utilities (such as apt in debian/ubuntu, yum in RH/Fedora/Yellow Dog)

About the directory names with backslashes before the spaces.  This is because bash interprets spaces as blank space, which seperates commands from their options and the arguments you give them.  So a space in a filename would cause the bash shell to misinterpret your command.  the backslash tells the shell that the next character is to be taken as a part of a continuous string (this isn't exactly what it is, but I don't know how else to explain it) instead of a spacer between seperate elements of a command.  To get around this, just use something other than spaces in filenames.

---

### Post by mlomker on 2005-11-11
[QUOTE=spin1078]So i assume its loaded. [/quote]

If you followed the instructions that I provided, then try this:

```

mlomker@mlomkernote:/$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

```

If it doesn't work then do a search to find java:

```

sudo updatedb
locate java

```

---

### Post by spin1078 on 2005-11-13
well the first didnt work, but it located it all in a a folder in my home directory.

I made a folder /home/bradd/files to store my stuff.  Yeah Im Bradd, its actually brADD, my DJ name.  Anyways so i put the package in that directory, ran it, it installs a big list of files.  see:

I took out half the list cause it was long


/home/bradd/files/java2/jre1.5.0_05/lib/zi/Pacific/Galapagos
/home/bradd/files/java2/jre1.5.0_05/lib/zi/WET
/home/bradd/files/java2/jre1.5.0_05/lib/zi/ZoneInfoMappings
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.properties.src
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.RedHat.properties.src
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.RedHat.9.0.properties.src
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.RedHat.8.0.properties.src
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.RedHat.2.1.properties.src
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.RedHat.3.properties.src
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.Sun.properties.src
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.Sun.2003.properties.src
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.Turbo.properties.src
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.Turbo.8.0.properties.src
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.SuSE.properties.src
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.bfc
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.RedHat.bfc
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.RedHat.9.0.bfc
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.RedHat.8.0.bfc
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.RedHat.2.1.bfc
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.RedHat.3.bfc
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.Sun.bfc
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.Sun.2003.bfc
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.Turbo.bfc
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.Turbo.8.0.bfc
/home/bradd/files/java2/jre1.5.0_05/lib/fontconfig.SuSE.bfc
/home/bradd/files/java2/jre1.5.0_05/lib/cmm
/home/bradd/files/java2/jre1.5.0_05/lib/cmm/sRGB.pf
/home/bradd/files/java2/jre1.5.0_05/lib/cmm/GRAY.pf
/home/bradd/files/java2/jre1.5.0_05/lib/cmm/CIEXYZ.pf
/home/bradd/files/java2/jre1.5.0_05/lib/cmm/PYCC.pf
/home/bradd/files/java2/jre1.5.0_05/lib/cmm/LINEAR_RGB.pf
/home/bradd/files/java2/jre1.5.0_05/lib/deploy.jar
/home/bradd/files/java2/jre1.5.0_05/lib/management
/home/bradd/files/java2/jre1.5.0_05/lib/management/management.properties
/home/bradd/files/java2/jre1.5.0_05/lib/management/snmp.acl.template
/home/bradd/files/java2/jre1.5.0_05/lib/management/jmxremote.password.template
/home/bradd/files/java2/jre1.5.0_05/lib/management/jmxremote.access
/home/bradd/files/java2/jre1.5.0_05/lib/im
/home/bradd/files/java2/jre1.5.0_05/lib/im/indicim.jar
/home/bradd/files/java2/jre1.5.0_05/lib/im/thaiim.jar
/home/bradd/files/java2/jre1.5.0_05/lib/jsse.jar
/home/bradd/files/java2/jre1.5.0_05/lib/javaws
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/miniSplash.jpg
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/messages.properties
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/messages_zh_TW.properties
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/messages_de.properties
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/messages_es.properties
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/messages_fr.properties
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/messages_it.properties
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/messages_ja.properties
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/messages_ko.properties
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/messages_sv.properties
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/messages_zh_CN.properties
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/messages_zh_HK.properties
/home/bradd/files/java2/jre1.5.0_05/lib/javaws/Java1.5.ico
/home/bradd/files/java2/jre1.5.0_05/lib/charsets.jar
/home/bradd/files/java2/jre1.5.0_05/lib/plugin.jar
/home/bradd/files/java2/jre1.5.0_05/lib/rt.jar
/home/bradd/files/java2/jre1.5.0_05/CHANGES
/home/bradd/files/java2/jre1.5.0_05/COPYRIGHT
/home/bradd/files/java2/jre1.5.0_05/Welcome.html
/home/bradd/files/java2/jre1.5.0_05/README
/home/bradd/files/java2/jre1.5.0_05/LICENSE
/home/bradd/files/java2/jre1.5.0_05/THIRDPARTYLICENSEREADME.txt
/home/bradd/files/java2/jre1.5.0_05/man
/home/bradd/files/java2/jre1.5.0_05/man/man1
/home/bradd/files/java2/jre1.5.0_05/man/man1/java.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/keytool.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/rmid.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/rmiregistry.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/tnameserv.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/servertool.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/orbd.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/policytool.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/pack200.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/unpack200.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/javaws.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/kinit.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/klist.1
/home/bradd/files/java2/jre1.5.0_05/man/man1/ktab.1
/home/bradd/files/java2/jre1.5.0_05/man/ja
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/java.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/keytool.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/rmid.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/rmiregistry.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/tnameserv.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/servertool.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/orbd.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/policytool.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/pack200.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/unpack200.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/javaws.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/kinit.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/klist.1
/home/bradd/files/java2/jre1.5.0_05/man/ja_JP.eucJP/man1/ktab.1
/home/bradd/files/java2/jre1.5.0_05/plugin
/home/bradd/files/java2/jre1.5.0_05/plugin/i386
/home/bradd/files/java2/jre1.5.0_05/plugin/i386/ns7
/home/bradd/files/java2/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so
/home/bradd/files/java2/jre1.5.0_05/plugin/i386/ns7-gcc29
/home/bradd/files/java2/jre1.5.0_05/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/home/bradd/files/java2/jre1.5.0_05/plugin/desktop
/home/bradd/files/java2/jre1.5.0_05/plugin/desktop/sun_java.png
/home/bradd/files/java2/jre1.5.0_05/plugin/desktop/sun_java.desktop
/home/bradd/files/java2/jre1.5.0_05/javaws
/home/bradd/files/java2/jre1.5.0_05/javaws/javaws
/home/bradd/files/java2/jre1.5.0_05/.systemPrefs
/home/bradd/files/java2/jre1.5.0_05/.systemPrefs/.system.lock
/home/bradd/files/java2/jre1.5.0_05/.systemPrefs/.systemRootModFile
bradd@ubuntu:~$

---

### Post by spin1078 on 2005-11-13
am i just missing where i should intall things from.  i mean, where do you install stuff too.  is there a similar thing to windows Program Files?

---

### Post by nrwilk on 2005-11-13
[QUOTE=spin1078]am i just missing where i should intall things from.  i mean, where do you install stuff too.  is there a similar thing to windows Program Files?[/QUOTE]

It took me a long time to figure this out, too.

Usually stuff installs in /usr/...
/usr/share is very common

I'm still not very clear on all the other places, or WHY the data is stored where it is.
could someone else let us know other places and also the resons things are stored where they are?

---

### Post by steve.horsley on 2005-11-14
[QUOTE=spin1078]am i just missing where i should intall things from.  i mean, where do you install stuff too.  is there a similar thing to windows Program Files?[/QUOTE]

The most usual places to put stuff you install yourself ie either /opt or /usr/local for stuff that everyone will use, or somewhere in a user's home directory if it's just for that one user. Note that you myst have root access rights to scribble outside your home folder, so you put "sudo" in front of the command.

For you java stuff, I suggest you do the following. 

First copy the java directory you unpacked over to /opt, like this:
```
sudo cp -r /home/bradd/java2/jre1.5.0_05 /opt
```

Now you can delete the unpacked directory in your home folder - don't get this wrong!:
```
rm -rf /home/bradd/java2
```
Note that the reason I copied and then deleted rather than just moving the folder was that by copying, the file ownership in the copy will be root, even if the files in your directory are owned by you.

Make sure it works with ```
/opt/jre1.5.0_05/bin/java -version
```

Next, see if there is a java already installed, with 
```
ls -l /usr/bin/java
```
If it exists, it is probably a link that points to /etc/alternatives/java, and if that exists then it almost certainly doesn't point to the java 1.5 that you just installed. The reason for going through /etc is that /etc/ contains most configuration info - a bit like the registry (ducks quickly), so it makes sense to say which java version you use from there.

So if /usr/bin/java doesn't exist, make the link to alternatives:
```
sudo ln -s /etc/alternatives/java /usr/bin/java
```

If /etc/alternatives/java already exists but points to the wrong place, rename it:
```
sudo mv /etc/alternatives/java /etc/alternatives/java-original
```

Now create the right alternative link:
```
sudo ln -s /opt/jre1.5.0_05/bin/java /etc/alternatives/java
```

Now you should be able to just say ```
java -version
``` and get the right one.(/usr/bin is always in your PATH).

Hopefully limewire will now work. I've never used it so can't help there.

Steve

---

