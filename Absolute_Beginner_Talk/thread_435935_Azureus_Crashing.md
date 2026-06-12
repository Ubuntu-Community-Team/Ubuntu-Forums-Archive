---
title: "Azureus Crashing"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Hellcom on 2007-05-07
Azureus crashes within a second of it finishing loading. It has worked perfectly until it locked up forcing me to close it via the system monitor. I ran it through the terminal to see if I could find any problems and I got this:

```
DEBUG::Mon May 07 16:51:33 BST 2007  Data Missing /home/rutter/Desktop/BtRLDemoInstaller.run
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb4797172, pid=22558, tid=3084286864
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid22558.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
```

---

### Post by Hellcom on 2007-05-07
Never mind, by reinstalling Azureus and its dependences (Java etc...) everything works fine again.

---

### Post by timmay on 2007-05-07
I had the exact same error after I shut down my PC without first closing Azureus. I tried first installing just Azureus again but that didn't work. Installing everything however did. The question still remains "how can this be fixed with out having to reinstall Azureus and ALL it's dependencies?"

This is not the first time ... I've broken Azureus a couple of times due to forgetting to close it before switching my PC off. This never happened with Ubuntu 6.10 ... seems to be the norm for 7.04 though :-(

---

### Post by kelvin spratt on 2007-05-07
its a bug in the latest java effects some people not all

---

### Post by pcsel on 2007-05-08
I had this happening as well, Azureus would crash 3/4 of the way through loading the splash screen. In the past I have cleared down the .lock file and the logs and that has  cured it. Not this time though.

I had just changed my theme and noticed Azureus shutdown I tried to restart it but got the usual crash. I reinstalled Java and Azureus and then cleared the logs and .lock files still no change. I then decided to backout the Theme which I had just installed and I could then start it up..Anyone any ideas?

Paul:confused:

---

### Post by chang47 on 2007-05-10
Same thing to me.

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=5153, tid=3084998336
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_11-b03 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid5153.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

I have xubuntu 7.04 with Java 5 installed using Add/Remove program.  It worked overnight until this morning.  I had the same thing with my last install of xubuntu.  I had tried clean install xubuntu 7.04 3 times now.  Very annoying but I guess part of the game.

Just adding my experience to the list and see if this is indeed a bug.

---

### Post by original_jamingrit on 2007-05-11
I have another problem that looks more similar to Hellcom's problem, except that I'm still running Java 5, and in Edgy.  My output in the terminal is this:

> #
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb028cd02, pid=6604, tid=3085080240
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid6604.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)


The crash occurs after the splash screen, when the main window is shown and my current torrents show up in the unfinished and finished lists.

I only installed Azereus today, and I downloaded a few tv shows with it.  Other than that, I also downloaded some proprietary codecs and libraries using:
> sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

I was able to watch the shows I had finished downloading, but Azereus stopped working about then.

I'll upgrade to the new Java, and post again whether or not the problem was fixed.

---

### Post by powder on 2007-05-11
Perhaps a quicker solution than reinstalling is to simply purge the .azureus folder in your home directory.

---

### Post by get$ on 2007-05-11
> **original_jamingrit said:**
> I have another problem that looks more similar to Hellcom's problem, except that I'm still running Java 5, and in Edgy.  My output in the terminal is this:



The crash occurs after the splash screen, when the main window is shown and my current torrents show up in the unfinished and finished lists.

I only installed Azereus today, and I downloaded a few tv shows with it.

This also happened to me, literally today. I found a fix on the ubuntu-fr forums. Check /usr/share/java for Azureus2.jar ... if that's what you have, you need to update Azureus; this can be done easily from the SourceForge repositories

```
sudo wget http://superb-west.dl.sourceforge.net/sourceforge/azureus/Azureus2.5.0.0.jar
sudo mv Azureus2.5.0.4.jar /usr/share/java/Azureus2.jar
```

After this you should be fine. (I think!)

---

### Post by original_jamingrit on 2007-05-11
I'm still a little confused, but it seems my problem is solved.  I had originally installed Azureus through the "Add/Remove Apps", but that version was 2.5.0.0.  I removed my current version of Azureus, and then I installed the newest version of Azureus by following these instructions at [http://ubuntuforums.org/showthread.php?t=144546]("http://ubuntuforums.org/showthread.php?t=144546")
replacing version 2.5.0.0 with 2.5.0.4.

Everything works fine now.  I left .azurues alone, and I'm picking up where I left off on my downloads before the crash.

Hope this helps anyone with a similar problem.

get$: thanks for the help, but it seems I already took the long way around. :P

---

### Post by jasondelta on 2007-05-18
I've found a nifty little trick that will let you get Azureus running again. Since my problem was somehow linked to me having to Force Kill a non-responsive Azureus, I found out that the main problem was being caused by the "Azureus was shut down improperly..." pop-up that comes up upon restarting the program. Most people have Sun Java on their Feisty install, which seems to have bugs with Azureus, but here's how to get around that temporarily:

Enter the command "sudo update-alternatives --config java" into the terminal

A menu will come up asking which java to use as default. Most people I believe will have /usr/lib/jvm/java-6-sun/jre/bin/java running as default. Just choose a different java selection for the time being.

Restart Azureus. It should work, and you'll get it to remain open. The pop-up will come up telling you about the improper closing - just click hide. Azureus probably won't be able to run, because it requires a more recent version of Java - and it will not let you download torrents. This is fine. Just close Azureus again.

Go back to the terminal, and re-enter "sudo update-alternatives --config java"

Select the java-6-sun selection.

Restart Azureus. Everything should work fine now! 


Now, I'm not certain this will work for everyone, but it worked for me in a pinch. So hopefully it'll work for you. :)

---

### Post by fenian on 2007-05-18
Running these commands will allow azureus to start again...

> rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*

---

### Post by Felipe Butcher on 2007-05-18
> **fenian said:**
> Running these commands will allow azureus to start again...

Great!!! thanks!

---

### Post by tomt on 2007-05-19
Thanks the rm commands worked for me also!

---

### Post by zhinker on 2007-05-19
> **fenian said:**
> Running these commands will allow azureus to start again...
Sweet, did the trick!  Btw, I'm running Ubuntu 6.10, so the problem wasn't just with Fiesty

---

### Post by chriskasurak on 2007-05-29
get$, 

Your solution seems to work but you've mixed it up a little in your directions: you say to download 2.5.0.0 but to mv 2.5.0.4. It works fine but you've got to download 2.5.0.4.jar

thanks for the solution!

---

### Post by kperkins on 2007-05-30
Thanks, I had the same problem, and this solved it wonderfully.

---

### Post by isparkes on 2007-05-31
Just to add for those that don't want to have to play around with things too much, you can just delete the log file under .azureus/logs and this will solve the problem. You could also add this to the /usr/bin/azureus script, but that's playing around with things... :0

---

### Post by squee on 2007-06-13
I had a different problem and that worked too. Thanks soooooo much!!!!

---

### Post by pimlottc on 2007-06-24
The problem happens when Azureus detects an improper shutdown (or other error) and tries to notify you with that "slide-in" dialog box that appears in the lower-right hand corner.  For some reason, this causes a crash when using sun Java (either 5 or 6) with the Fiesty shipped version.

This is why removing the log directories works (Azureus uses them to determine if it was shutdown properly) as well as why switching to using gcj for a single run works (since it is now shutdown properly).

A permanent solution is to update Azureus, either directly by replacing the Azureus jar or installing a new version of the Fiesty deb from feisty-proposed: [http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/azureus/azureus_2.5.0.0repack1-0ubuntu1.1~proposed1_all.deb)

More discussion at the launchpad bug entry: [https://bugs.launchpad.net/ubuntu/feisty/+source/azureus/+bug/68020](https://bugs.launchpad.net/ubuntu/feisty/+source/azureus/+bug/68020)

---

