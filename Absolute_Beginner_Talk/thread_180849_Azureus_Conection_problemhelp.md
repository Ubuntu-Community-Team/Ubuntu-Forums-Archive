---
title: "Azureus Conection problem/help"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-05-23
I know I have seen this somewhere before, but I cannot get the Azureus to connect to anything.  I tried the default port and the 6881 port, but to no avail.

[IMG]http://img99.imageshack.us/img99/35/screenshot2vs.th.png[/IMG]

you can see it says firewalled, but I am not running Firestarter.  It also say DHC firewalled.

I did try to go to the forums for Azureus but those gents are rather abusive to newbies and to people in general, so I turned to you

thanks 

KK

---

### Post by it.henrik on 2006-05-23
I would guess that you are running blackdown java. You should change it to sun1.5

Here is how it looks for me:
```

henrik@ubuntu-Latten:~$ java -showversion 
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
```

install suns jre (java runtime enviroment) from synaptics and tell ubuntu to use it with

```

sudo update-alternatives --config java
```

---

### Post by KarmaKing on 2006-05-23
> java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Usage: gij [OPTION] ... CLASS [ARGS] ...
          to invoke CLASS.main, or
       gij -jar [OPTION] ... JARFILE [ARGS] ...
          to execute a jar file

I know I just installed Java and everything went fine, but obviously this is wrong.

This is my Config
> There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-gcj/bin/java' to provide `java'.

wassup???  Did I miss a step somewhere??

The Azureus worked for all but a seconf then the firewall lights came up again.

---

### Post by jorn on 2006-05-23
Excuse me for this question:
Usually one can't se if firestarter is running. But you havn't installed it?

---

### Post by KarmaKing on 2006-05-23
[QUOTE=jorn]Excuse me for this question:
Usually one can't se if firestarter is running. But you havn't installed it?[/QUOTE]
Hi jorn,

yes I have it installed.  Perhaps I should try with it uninstalled?  Id that what you are getting at?
And when you say one can't see it, does that mean it runs in the back ground without any visible Icon?

---

### Post by jorn on 2006-05-23
Yes firestarter will run in the background.
Try stopping firestarter by typing or pasting:
> sudo firestarter
into terminal and klick on the botton "Stop firestarter"
If Azureus now works you know you have to configure firestarter if you want it running.

---

### Post by it.henrik on 2006-05-23
'you need to install SUN:s java runtime enviroment

go to synaptics .. search for jre .. now you should be able to see sun-java5-jre .. install it and everything synaptics wants to throw in there..

when its done 

```
sudo update-alternatives --config java
```

mark java version "1.5.0_06"  

restart azureus and it should be just peachy :)

---

### Post by sailor2001 on 2006-05-23
a question........are you behind a router and would that effect it? (firewall)

---

### Post by KarmaKing on 2006-05-24
[QUOTE=sailor2001]a question........are you behind a router and would that effect it? (firewall)[/QUOTE]
no not behind a firewall, but I am part of a rather small internet provider on an ISDN network and I am not sure what is on their end of the deal.

After properly getting the Java installed as was suggested by jorn, Azureus is connecting now, but is pretty slow (just waiting for some peers I guess). It is still shows it is firwalled even after I uninstalled Firestarter to test it.
Also, the yellow light indicating a NAT problem and Azureus wanted to upgrade the jar, but permission was denide.

I will keep it connected to see if the yellow light goes to green.

I am going to take a look at the wiki, but some more input would be much appreciated.

---

### Post by darkninja on 2006-05-24
I had similer problems with Azureus using GCJ, I switched to Sun's Java and now it seems to work fine. Still have the problem with the popup windows though.

Try using Sun's Java.

---

### Post by KarmaKing on 2006-05-24
[QUOTE=darkninja]I had similer problems with Azureus using GCJ, I switched to Sun's Java and now it seems to work fine. Still have the problem with the popup windows though.

Try using Sun's Java.[/QUOTE]
got it, but it is still showing a NAT problem.  The lights on the torrents never turn green.  And the DHT is always yellow.  It does download, but I am not sure how well yet.  Have to see whn I get good peer connection.

---

### Post by jorn on 2006-05-24
When you are on a network, that you say you are, there must be a kind of router to manage the different pc's. To enable NAT (network address translation) the router must know where to send packages your pc is asking for. In the router you opens the port that Azureus runs on.

darkninja : To get rid of the pop-up window, have you istalled the latest version of Azureus 2.4.0.2?

---

### Post by goldaryn on 2006-05-24
Big thanks to the poster who  upped the advice on installing the Sun JRE and switching over..

Azureus is working better for me now. The popups are still playing up though.

I don't really like Azureus, really could do with a utorrent port :-D

---

### Post by mattb1982 on 2006-05-24
I've been having the same problems with azureus.  Assuming you have suns jre installed:

Use:
sudo update-alternatives --config java
to select suns jre as the default java.

Then in azureus, go to tools > options and under Connection untick "supplied by another peer" and untick "Added by a plugin".

This should solve you NAT and DHT problems.  Mine are both showing green now.

However, I have another problem now, that the tracker health still stays blue, and my download is not starting.  Does  any one have any suggestions?

---

### Post by it.henrik on 2006-05-24
[QUOTE=mattb1982]I've been having the same problems with azureus.  Assuming you have suns jre installed:

Use:
sudo update-alternatives --config java
to select suns jre as the default java.

Then in azureus, go to tools > options and under Connection untick "supplied by another peer" and untick "Added by a plugin".

This should solve you NAT and DHT problems.  Mine are both showing green now.

However, I have another problem now, that the tracker health still stays blue, and my download is not starting.  Does  any one have any suggestions?[/QUOTE]

may I asked why you turned of the peer exchange? How does this help? (Ireally want to know.. im not sarcastic or something). 

Blue health means you are connected to peers but the tracker is unreachable... to get more info about the health of the tracker: Doubel click on the row with that torrent and you should get an new view opened. Here on the general tab look at the line that say Tracker Status: .. this should give you some info.

[QUOTE=goldaryn]Big thanks to the poster who  upped the advice on installing the Sun JRE and switching over..
[/QUOTE]

*bows* :)

---

### Post by user1397 on 2006-05-24
Just to clear some things up:
Sun's Java is not available through Synaptic in *Breezy* only in *Dapper*.  
Therefore you would have to follow the wiki guide: [https://wiki.ubuntu.com/RestrictedFormats#head-fabecb1554d75cd3116507e4da83335d4e4f8f3e](https://wiki.ubuntu.com/RestrictedFormats#head-fabecb1554d75cd3116507e4da83335d4e4f8f3e)

Also, Firestarter is not Ubuntu's firewall, it is just a GUI (Graphical User Interface) for the real firewall, called iptables.  So uninstalling firestarter would do nothing.

Also, I download stuff with Azureus, and the little smiley faces next to the downloads are always yellow for me, but they still download fine.

---

### Post by KarmaKing on 2006-05-25
thanks for the clarification eric.

---

