---
title: "[SOLVED] java not working; conflicting info on which version I have"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by jfehribach on 2007-12-28
When I go to web address
 [COLOR="Red"]http://java.com [/COLOR]
and click on: 
[COLOR="Red"]Do I have Java? [/COLOR]
 then after a minute my browser window reports:
	   [COLOR="Red"]Verifying Java Version

Oops! You don't have the recommended Java installed.
Your Java version is 1.4.2. Please click the button below to get the recommended Java for your computer. [/COLOR]


If I use a terminal window and key:
[COLOR="Red"]java -version[/COLOR]
then it reports:
[COLOR="Red"]java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)[/COLOR]


When I specify:
 [COLOR="Red"]about:plugins[/COLOR]
in my Firefox address box, it includes two entries that seem to involve java.

The first is:
[COLOR="Red"]GCJ Web Browser Plugin 0.92

    File name: libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.[/COLOR]

The second is:
[COLOR="Red"]Java(TM) Plug-in 1.6.0_03-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_03
[/COLOR]


What most annoys me is that when I visit web site:
[COLOR="Red"]http://radar.weather.gov/radar.php?rid=ILN&product=N0R&overlay=11101111&loop=yes[/COLOR]
I see no radar, instead of the looping radar images I can see on my Windows PC.  The bottom of the window says:
[COLOR="Red"]Java is necessary for radar looping and is best optimized using Java version 1.4.2 or higher.[/COLOR]

I know very little about java, so I'm pretty lost.  I searched the Absolute Beginner Talk and applied various java-related fixes that were mentioned, but nothing solved my problem.  It's a guess, but is GCJ plugin interfering, and, if so, how do I get rid of it?

Any help is appreciated.

Thanks.

Jerry Fehribach

---

### Post by buckykat on 2007-12-28
you might try removing libgcjwebplugin.so from /usr/lib/firefox/plugins and restarting firefox.

---

### Post by PeterJS on 2007-12-28
> **buckykat said:**
> you might try removing libgcjwebplugin.so from /usr/lib/firefox/plugins and restarting firefox.

Yeah, GCJ is the java extensions for gcc and was designed to be used to compile java programs in to native linux programs. Which presents several problems when trying to use it as a browser plugin, first as you noticed it still stuck at java 1.4 compatibility, and secondly and more problematic is that it's designed to be a compiler unlike every other java implementation there is, so it runs slowly because it's designed to only be used once per program, not every time you load the program. GCJ has it's place (if they can keep current), but the browser isn't it.

---

### Post by Sef on 2007-12-28
How did you install Java?  If you used Synaptic or Add/Remove, I would use the same tool to remove it.   

What you want is Sun Java 6.   Do a search in Add/Remove or Synaptic to find it.  In Add/Remove it is the top option.  

If you can't get it, then you need to open the repositories, in Add/Remove, just click on the top right box and set it to "All Available Application".

---

### Post by eyezdk on 2007-12-29
I have the same problem. But I am new to Ubuntu as well. 
you sad something removing the plug-in from firefox, but how do i do that? 
I am loged in as admin. and i should have all right to delete things, but i get an error message 
Tanks for the help so fare.

Edit: my error 
Cannot move "/usr/lib/fir...ebplugin.so" to the trash because you do not have permissions to change it or its parent folder

---

### Post by billgoldberg on 2007-12-29
I had the same thing. Just follow this [guide]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html").

extract:
First you need to check multiverse repository enabled or not after that open a terminal window. Since you are going to be installing the JRE and the web browser plug-in, you’ll be using the following command from a terminal

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by eyezdk on 2007-12-29
Nope. Nothing there. 

I just removed all java i had with synaptik.

Run the sudo. and the version and got 

thomas@thomas-desktop:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
thomas@thomas-desktop:~$

When i use [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

It will say i have 1.4.2 and i cant se the moving logo (mean no java) 

I got it to work once last night... (so i know i works) but this mornig... lol.. nothing.

EDIT: 
Ok, i have now removed libgcjwebplugin.so.
Now the web site tells me i have 1.5.0 version. (but no logo, so looks like no java detection yet. ) strange...

ops! You don't have the recommended Java installed.
Your Java version is 1.5.0. Please click the button below to get the recommended Java for your computer.  

thomas@thomas-desktop:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing
-------

---

### Post by rkd on 2007-12-29
Edit: I see you edited your post at the same time I was posting, so it seems you don't need this one any more.

eyezdk:  I think you misunderstood something when you said you were logged in as admin. 

The term for the all-powerful user in Linux is root, not admin. And unless you do something out of the ordinary, you cannot login as root on an Ubuntu system.  There is a way to do that, and maybe you found those steps somewhere and followed them.  If you did, something about it didn't work, otherwise you wouldn't have seen the error message you posted.  So you might find it helpful to read a little more about managing Ubuntu.

Meanwhile, one way to solve the problem you asked about is to open a terminal (from the Applications menu, choose Accessories, then Terminal). Copy the following command and paste it into the Terminal window and press the Enter key:
```
sudo rm /usr/lib/firefox/plugins/libgcjwebplugin.so
```
It will prompt you for your password (the password for the userid you are currently logged in as).  When you type your password, nothing will echo, so you might think something isn't working, but it is seeing the characters you type. Push the Enter key after the last character of your password.  If you entered the password correctly, the terminal then will switch to the root user to perform the command that follows the sudo. That command will delete the file given after the rm (rm = remove).  As soon as the command is done, the terminal returns to your normal userid.

Edit: I see you edited your post at the same time I was posting, so it seems you don't need this one any more.

---

### Post by eyezdk on 2007-12-29
Thanks rkd! 

Yes, i looked around the froum abit. (and when file is owned by root, you need do somthing more then just push delete.)
I found the Alt + F2 and then run "gksu nautilus" that gave me right to dele the file. But thx alot for your poste, now i know how i can do it abit faster next time. 

But removing the plugin did not solved my broblem yet, so am am working on it. 

Thanks for the help.

---

### Post by erfahren on 2007-12-29
> **eyezdk said:**
> Thanks rkd! 

Yes, i looked around the froum abit. (and when file is owned by root, you need do somthing more then just push delete.)
I found the Alt + F2 and then run "gksu nautilus" that gave me right to dele the file. But thx alot for your poste, now i know how i can do it abit faster next time. 

But removing the plugin did not solved my broblem yet, so am am working on it. 

Thanks for the help.
it looks like you have sun-java5 installed as well as sun-java6 (if java.com is showing you have Java 5.0)

go to the Synaptic Package Manager and search for "sun-java" - the only ones that should be installed is sun-java6-bin, sun-java6-jre and sun-java6-plugin

you can also see what the output of this is:
```

sudo update-alternatives --config java

```
you should see something like:
```

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```
(if you only have one version it'll say so and say there's nothing to configure)


--- be careful using "gksudo nautilus" - you can inadvertently delete system file(s) permanently and without any confirmation.

---

### Post by eyezdk on 2007-12-29
Ok, Thx erfahren. 

When i look in Synaptic no java 5 installed. (i can see them on the list, but they are not cheked)
When i run 

sudo update-alternatives --config java

I get this

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.1
          3    /usr/bin/cacao
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java
*         5    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 

Looks like i have things install i dont realy need. 

ps. thx on the tip on "nautilus" not good thing to use for new users :D

---

### Post by jfehribach on 2007-12-29
> **buckykat said:**
> you might try removing libgcjwebplugin.so from /usr/lib/firefox/plugins and restarting firefox.

I am a happy camper.  Thanks!  

When I go to [COLOR="Red"]java.com[/COLOR] and click [COLOR="Red"] Do I have Java?[/COLOR]   I now get
	    
[COLOR="Red"]Verified Java Version

Congratulations!
 
You have the recommended Java installed (Version 6 Update 3). [/COLOR]

When I visit a favorite website that requires java:
[COLOR="Red"]http://radar.weather.gov/radar.php?rid=ILN&product=NCR&overlay=11101111&loop=yes[/COLOR]
then I get the looping radar images that previously did not work.

Here is a summary of what I did in terminal to fix it (line numbers shown are from 'history' command):
[COLOR="Red"]  478  cd /usr/lib/firefox/plugins
  481  sudo mv libgcjwebplugin.so jxfRENAMElibgcjwebplugin.so
  484  sudo mv jxfRENAMElibgcjwebplugin.so $HOME[/COLOR]

Just renaming the file as I did in line 481did not fix it, so in line 484 I moved it to a different directory.  I try to avoid using the 'rm' command in situations like this so I can easily restore, but the brave person could do it all with just:
[COLOR="Red"]sudo rm /usr/lib/firefox/plugins/libgcjwebplugin.so[/COLOR]

Thanks again to all who posted here, but especially to buckykat who had a simple solution I used successfully.

Jerry Fehribach

---

### Post by eyezdk on 2007-12-29
cool. not bad. 
now...this only means i am just a nOOb to this :D
more reading to go...

EDIT: 

Ok... nvm... 
we all know... if it does not work... Reinstall. 

Looks like my firefox had old and new plugins.. and it mixed em good up. 
I just tried to remove Firefox in synaptic, and install it.

Worked like a charm! have the newest version. 

Tanks for the help to all.

---

