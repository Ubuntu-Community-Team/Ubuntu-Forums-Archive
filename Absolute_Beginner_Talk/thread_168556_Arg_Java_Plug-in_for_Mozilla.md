---
title: "Arg: Java Plug-in for Mozilla?"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-04-30
Okay, I hunted about, visited a ton of sites, did what loads of other people were told to do. Don't point me towards easy-ubuntu anyone, I will simply ignore you. If I wanted things the easy way, I wouldn't have un-installed XP, now, would I? :lol:

Anyhow, after much hunting, I found something telling me that if the plug in was installed and all that (which it seems to be, though I don't HAVE anything saying about plugins. :? ) to try entering the following command from the mozilla plugin directory:

> ln -s /usr/java/jrel.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so

Which I did, and was told the following;

> ln: `./libjavaplugin_oji.so': File exists


 The thing I'm trying to use the java plugin for is here;

[http://www.themystictavern.com/content/view/46/55/](http://www.themystictavern.com/content/view/46/55/)

 It's a roleplay chatroom. I can use IRC to get in, but theres no &*%$@@ing point because it cuts people's posts to about four lines, and most people post around twenty. T___T
 I need the java plug in, and it won't work.

Can anyone help at all? ](*,)

---

### Post by Sef on 2006-04-30
What you wrote

> ln -s /usr/java/jrel.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so

What the directions from restricted formats say

> ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so

They are not the same.   Go to restricted formats and follow the directions for installing sun java.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by Raavea on 2006-04-30
It says file exists when I enter the commands that tells me to enter too. Yet java still doesn't work.

 *itches her eyeballs* I'm off to bed, I'll try something else in the morning...

---

### Post by harishg on 2006-05-01
check using about:  plugins to check if the java plugin is there.IF it is seen there it should work. Also there might be a conflict if you installed both the restricted and open source versions of java.

---

### Post by Raavea on 2006-05-01
I don't have an about: plugins. .-.

---

### Post by manicka on 2006-05-01
[QUOTE=Raavea]I don't have an about: plugins. .-.[/QUOTE]

type it in the address bar, press enter

---

### Post by Raavea on 2006-05-01
I'm pretty sure this;

> Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_08 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_08 	Java 		Yes

 Means it ought to be working. Is it just my tired, coffee-starved brain, or is there really a problem?

EDIT TO ADD: Just tried the room again, and it still ain't working..

---

### Post by manicka on 2006-05-01
try upgrading to j2re 1.5

[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

---

### Post by Raavea on 2006-05-01
I did what it said on that, and it **still** doesn't work.

 Can someone check if it works for *them?* Q-Chat is known to be... A little... Crap. You don't need a password, that's just if you're using a registered name. Stick something like uberbobness and click Log in and it oughta load.

 If it doesn't this whole thing was _pointless._ >..<

EDIT TO ADD: [Here]("http://www.abandoneddreams.com/myaboutplug")'s a text file with everything my about: plugins tells me.

---

### Post by Hallavej on 2006-05-01
Use this link to check if java plugin works.
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

I dont think it is a java problem. I tried to log in on the site with firefox with java plugin and opera without java plugin. It worked with them both and it looked the same to me.

---

### Post by joshrobinson on 2006-05-01
are you using firefox? go to edit > preferences then click content.. and make sure enable javascript is checked then click ok

if you did the symbolic link thing just make sure thats def. where you java file is located.. you might be putting in the wrong file location

id delete the libjavaplugin_oji.so file in the mozilla plugin directory and run the ln -s command again

---

### Post by Raavea on 2006-05-02
Hallavej: It's not the site I need to run with Java, it's the chat-room.

Joshrobinson: It's not important anymore... I'm moveing my HDs around 'coz I want to make the big one the Mistress, so I'll be doing a new install of Ubuntu there and transferring my documents.

---

### Post by manicka on 2006-05-02
when you're up and running try this page to see if Java is installed properly

[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

---

### Post by Raavea on 2006-05-02
I tried that link, and it resulted fine. My java is apparently sorted.

 Then later, I decided to try automatix, 'cause it's likely simpler to use it to install them packages I needed, now that I know how to do it via the command line. I installed the newest firefox, 1.5, with the plugins. The test again said my java is working, but the fsking chat room still don't load.

 Fsking Q-Chat. -_-

---

