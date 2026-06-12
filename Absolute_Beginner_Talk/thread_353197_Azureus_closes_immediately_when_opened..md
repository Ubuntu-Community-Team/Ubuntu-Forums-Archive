---
title: "Azureus closes immediately when opened."
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Catsworth on 2007-02-04
Hey guys,

I've just installed Azureus using Synaptic.

After install I went through the configuration thingy but now when I try to run Azureus the splash screen comes up but then Azureus closes straight away.

Anybody got any ideas what might be causing this?

Thanks.

---

### Post by taurus on 2007-02-04
Try to run it from a terminal to see what's the error message is.  I assume you have already installed java, right?

Applications -> Accessories -> Terminal
```
azureus
```

---

### Post by Catsworth on 2007-02-04
Here's the output from the terminal:

```
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=8216, tid=3084736176
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_10-b03 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid8216.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

I can't find the location where the 'error report file' file has been saved, so unfortunately I can't see what that says (any ideas?).

Thanks for the help.

---

### Post by taurus on 2007-02-04
Post these two commands here.

```
java -version
sudo find / -name hs_err_pid8216.log -print
```

---

### Post by Afoot on 2007-02-04
It's bugged. The same thing happens with Frostwire and other similar apps. The solution is rather simple; just go the site and download the latest Azureus jar package. Direct link to the download: [http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus2.5.0.4.jar&use_mirror=heanet](http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus2.5.0.4.jar&use_mirror=heanet)

When you have downloaded the file, you only need to do one more thing. Open up a terminal, cd to your download directory, in my case it was:
```
cd /home/fredrik/Desktop
```

...and type:
```
sudo mv Azureus2.5.0.4.jar /usr/share/java/Azureus2.jar
```

It should now work. Good luck!

---

### Post by Catsworth on 2007-02-04
java -version

```
java version "1.5.0_10"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_10-b03)
Java HotSpot(TM) Client VM (build 1.5.0_10-b03, mixed mode, sharing)

```

sudo find / -name hs_err_pid8216.log -print

```
/home/rob/.azureus/hs_err_pid8216.log

```


And the contents of the error log are as attached, I had to zip it to get it uploaded - sorry.

Thanks again.

---

### Post by Catsworth on 2007-02-04
> **Afoot said:**
> It should now work. Good luck!

Ok, it loads now but that's about it.....

I have a status bar in the bottom left that simply says: "Checking Install" 

Unfortunately it isn't doing anything other than that :)

---

### Post by cptjaben on 2007-02-04
I had this problem also, and I could get around it by reinstalling Azureus and deleting my .azureus folder in my home directory. After a while I found it to be very irritating and ended up installing Ktorrent instead, always a good alternative if you can't get azureus working.

---

### Post by shareMenaPeace on 2007-02-04
For me worked the automatix install -- automatix is a tool to install many common things automatic.

[http://getautomatix.com](http://getautomatix.com)

---

### Post by Catsworth on 2007-02-04
Ok, Azureus is 'working' now.....sort of :)

I can get .torrent files opened within it but nothing seems to want to download.

I've got a green light from the NAT checker, and the required port is forwarded through the router's firewall.

Do I need to do anything to Linux's built-in firewall (is it iptables) or should it just work automatically?

Thanks.

---

### Post by taurus on 2007-02-04
If both buttons are green, you are good to go in term of firewall.  No need to configure anything else.  However, it depends on what you try to download because it could take a while before it would start downloading.

---

### Post by Catsworth on 2007-02-04
Yeah, I've used Azureus before (under Windows), I'm trying to download well seeded files (the Ubuntu 6.10 release actually :)  ) so I wouldn't have thought they should take that long.....

---

### Post by Catsworth on 2007-02-04
Oh yeah, and I can't close Azureus either.....the File | Exit command doesn't work.

I'm starting to wonder if the Linux implementation of my favourite BT client isn't all that it should be.....

---

### Post by morpheus01 on 2007-02-28
> **Afoot said:**
> It's bugged. The same thing happens with Frostwire and other similar apps. The solution is rather simple; just go the site and download the latest Azureus jar package. Direct link to the download: [http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus2.5.0.4.jar&use_mirror=heanet](http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus2.5.0.4.jar&use_mirror=heanet)

When you have downloaded the file, you only need to do one more thing. Open up a terminal, cd to your download directory, in my case it was:
```
cd /home/fredrik/Desktop
```

...and type:
```
sudo mv Azureus2.5.0.4.jar /usr/share/java/Azureus2.jar
```

It should now work. Good luck!

Worked a treat. You're a legend Afoot. If you or A.I. ever visit Dublin you're owed at least one pint of Guinness. 
Thanks.

---

### Post by morpheus01 on 2007-03-10
It's closing after 1 second again after an update I received yesterday. Any ideas why this is?

---

### Post by Catsworth on 2007-03-12
Yep, can confirm that bl**dy Azureus is knackered again - following the results above got it fixed but it's starting to get annoying having to redo this every time there's an update.

Does *anybody* know why this keeps happening?

---

### Post by Songwind on 2007-03-12
I had sketchy (but not horrible) results with Azureus under Linux also.

I've been playing around with ktorrent this past week and having a much better result.

I'm not meaning to be unhelpful or start any kind of client flame war.  Just thought I'd mention it in case you didn't know the alternative was out there.

---

### Post by Catsworth on 2007-03-13
Thanks for the pointer.  I did try KTorrent a while back but didn't have much luck with it.  I've used Azureus for years (on Windows systems) and always found it to be a very good client, even if it is a little resource hungry.

Just a shame that it goes belly up just about every time I get an update :(

---

### Post by Songwind on 2007-03-13
Have you noticed anything common each time you update?  The only thing that makes sense to me is that something is being deleted or overwritten when you update.

I never had that particular behavior with Azureus, downloads were just unstable and rarely maintained a good data rate, even on well seeded torrents.

---

### Post by Catsworth on 2007-03-13
Not really, I need to start keeping a log of what updates I accept and what they break - that way I know which updates not to accept in the future :)

---

### Post by morpheus01 on 2007-03-16
This command seems to give the option to use different versions of Java already on the computer.

sudo update-alternatives --config java

I found it on another thread. Changing it worked for me for a while. 

Now there's something wrong with NAT and firewall though, not sure if it's related. I think it's also effected compiling some code I wrote as I was using a version of the Java Development Kit I installed myself (not using synaptic or Update M) so I wasn't being given that option to run that Java. But if it's not related to NAT and you're not writing code, it may work for you.

Next time I need to download something I might try a different client myself.
Good luck.

---

### Post by slayerboy on 2007-03-21
I had this problem after my cable internet provider stopped providing me service for about an hour today and Azureus didn't like this and crashed.  I saw something in one of the bug reports about deleting the .azureus directory in your home directory.

I didn't feel like redoing all the settings, so I looked in my home directory's .azureeus folder and found a .lock file and deleted that, then I went into the logs folder and moved the contents of that folder (including the "save" folder) to a new folder on my desktop for backup purposes.  Then I restarted azureus and it seems like it's working now

Try it and see what happens.  This is a nasty workaround, but as long as azureus doesn't crash, you're fine. :KS

---

### Post by sunset_studies on 2007-04-06
thanks slayerboy, that worked (and seemed far less 'nasty' that the other proposed fixes).

---

### Post by schmolch on 2007-05-01
It works with gij but eats all my CPU with only 1 active torrent while with java it could run 20 torrents. Checking a torrent also requires at least 10 times more time than with java.
Also, with gij azureus fails to calculate the completion-level of the torrent (it's done before it reaches 100%).

I installed feisty twice now and java broke again after a reboot.

---

### Post by lobner on 2007-06-27
If people are  still having problems with this. Read the following:

[http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)
[https://help.ubuntu.com/community/AzureusHowTo](https://help.ubuntu.com/community/AzureusHowTo)

---

### Post by tarek on 2007-06-27
I had the same problem so I downloaded Azureus and installed it myself. More stable than the one from the repository

---

### Post by squee on 2007-06-29
Copying this from another post i made. I didnt work out the details but there are several posts where people have problems like this so I am posting the one that worked for me.

if you do get anymore problems try this

Running these commands will allow azureus to start again...

Quote:
rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*

i got it from here
[http://ubuntuforums.org/showthread.p...tdown](http://ubuntuforums.org/showthread.p...tdown) &page=2

the thread deals with a different problem but it solved this one for me.

Good luck!

---

### Post by zorkerz on 2007-09-19
I have deleted .lock and the files in log and save also the entire .azureus folder non of these have made azureus run for more than 1.5 seconds by my estimation. Any ideas

---

### Post by Poene on 2007-09-29
> **Afoot said:**
> It's bugged. The same thing happens with Frostwire and other similar apps. The solution is rather simple; just go the site and download the latest Azureus jar package. Direct link to the download: [http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus2.5.0.4.jar&use_mirror=heanet](http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus2.5.0.4.jar&use_mirror=heanet)

When you have downloaded the file, you only need to do one more thing. Open up a terminal, cd to your download directory, in my case it was:
```
cd /home/fredrik/Desktop
```

...and type:
```
sudo mv Azureus2.5.0.4.jar /usr/share/java/Azureus2.jar
```

It should now work. Good luck!

Thanks dude/dudette . Solved my issue too.

---

### Post by mandrill on 2007-09-30
I know there's a workaround, but....I finally downloaded deluge from their website, has a deb installer, runs on python, not java, and is every bit as configurable as azureus without using cpu cycles...

---

### Post by Vaelor on 2007-10-19
@ Afoot. thank you so much :)

---

### Post by AceRimmer on 2007-10-30
> **Afoot said:**
> It's bugged. The same thing happens with Frostwire and other similar apps. The solution is rather simple; just go the site and download the latest Azureus jar package. Direct link to the download: [http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus2.5.0.4.jar&use_mirror=heanet](http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus2.5.0.4.jar&use_mirror=heanet)

When you have downloaded the file, you only need to do one more thing. Open up a terminal, cd to your download directory, in my case it was:
```
cd /home/fredrik/Desktop
```

...and type:
```
sudo mv Azureus2.5.0.4.jar /usr/share/java/Azureus2.jar
```

It should now work. Good luck!

I did this and now it is telling me
"SWT library loaded from "usr/lib/eclipse/plugins" cant be automatically updated from version 3236 to 3318 (must be loaded from "/home/aaron/.azureus"). Please see the wiki for details".

---

### Post by stuffer007 on 2007-10-31
> **Afoot said:**
> It's bugged. The same thing happens with Frostwire and other similar apps. The solution is rather simple; just go the site and download the latest Azureus jar package. Direct link to the download: [http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus2.5.0.4.jar&use_mirror=heanet](http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus2.5.0.4.jar&use_mirror=heanet)

When you have downloaded the file, you only need to do one more thing. Open up a terminal, cd to your download directory, in my case it was:
```
cd /home/fredrik/Desktop
```

...and type:
```
sudo mv Azureus2.5.0.4.jar /usr/share/java/Azureus2.jar
```

It should now work. Good luck!

You are a life saver.... thanks

---

### Post by jaybombalous on 2007-10-31
forget the hassle just use '**deluge**'!

I am not sure I did anything other then hit enter to get it d/l'ing torrents. So newb friendly it actually bores me.

---

### Post by elabdel on 2007-11-01
hello

You can even dounload azureus3 :

[http://downloads.sourceforge.net/azureus/Azureus3.0.3.4.jar?modtime=1191466425&big_mirror=0]("http://downloads.sourceforge.net/azureus/Azureus3.0.3.4.jar?modtime=1191466425&big_mirror=0")

```
sudo cp Azureus3.0.3.4.jar /usr/share/java/Azureus3.jar
```

After you will need to modify your azureus script :

```
sudo gedit /usr/bin/azureus
```

At the end of this file you have to replace Azureus2.jar by Azureus3.jar.

---

### Post by Lord C on 2007-11-12
> **AceRimmer said:**
> I did this and now it is telling me
"SWT library loaded from "usr/lib/eclipse/plugins" cant be automatically updated from version 3236 to 3318 (must be loaded from "/home/aaron/.azureus"). Please see the wiki for details".

I installed the latest .deb file from GetDeb ( [http://www.getdeb.net/app.php?name=Azureus](http://www.getdeb.net/app.php?name=Azureus) )

Worked great :D

---

### Post by clparker on 2007-11-12
> **Afoot said:**
> It's bugged. The same thing happens with Frostwire and other similar apps. The solution is rather simple; just go the site and download the latest Azureus jar package. Direct link to the download: [http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus2.5.0.4.jar&use_mirror=heanet](http://sourceforge.net/project/downloading.php?groupname=azureus&filename=Azureus2.5.0.4.jar&use_mirror=heanet)

When you have downloaded the file, you only need to do one more thing. Open up a terminal, cd to your download directory, in my case it was:
```
cd /home/fredrik/Desktop
```...and type:
```
sudo mv Azureus2.5.0.4.jar /usr/share/java/Azureus2.jar
```It should now work. Good luck!

Seems to be working so far, do hope this does the trick!

---

### Post by barrack on 2007-12-23
Is there anyway to get a stable version of azureus pre version 3? The repo version closes immediately and the newest version, as recommended to install throghout this thread... well it sucks. I find the layout to be completely distracting... like i'm shopping on iTunes or something.

Any ideas? Thanks.

---

### Post by philinux on 2007-12-23
Yep like it been said by the mods even.

Azureus is buggy and its a resource hog cos it uses java.

Just try Deluge instead.

---

### Post by barrack on 2007-12-23
> **philinux said:**
> Yep like it been said by the mods even.

Azureus is buggy and its a resource hog cos it uses java.

Just try Deluge instead.

will do! thanks

---

