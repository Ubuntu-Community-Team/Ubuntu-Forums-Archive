---
title: "Azureus dead"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by maxim1 on 2007-04-09
whats the easiest way to clean and sort out my system, I am having problems with Azureus installation. Some reason it stop working it would load up the splash screen then close down. I tried updating java and also updating Azureus but no joy, now its total broke. When you launch it nothing happens at all :( 

Any one have any ideas ?

---

### Post by tonyr1988 on 2007-04-09
Open a Terminal (Applications >> Accessories >> Terminal) and type:

> azureus

What happens? Copy and paste the output into a reply.

Also, what did you do to update java / azureus?

---

### Post by maxim1 on 2007-04-09
I updated both, currently I have installed java web start 1.4 and 1.5. I updated Azureus  to 2.5.0.4 using this method from a guide 

d Desktop/
tar xjf Azureus_2.3.0.4_linux.PPC.tar.bz2
sudo mv azureus/ /usr/lib/
cd /usr/lib/azureus
./azureus

I have since deleted this directory and reinstalled Azureus using synaptic  

I dont know what to post up as nothing happens, i double click the azureus icon and nothing happens :confused:

---

### Post by kc5hwb on 2007-04-09
From my experience, Azureus pretty much blow goats.  I had it running on a 1.1GHZ AMD box running Ubuntu 6.06 and it bogged the whole system down........and that is saying alot for Linux.  I also tried it on one of my XP boxes, and it still ran the system down (which isn't surprising for Windows)  I started using BitTornado and now I don't use anything else.

---

### Post by maxim1 on 2007-04-09
Ive been using Azuerus for a while on win Xp with no complaints, it would be nice to use it with Ubuntu. I have used bit tornado as well and preferred Azureus.

---

### Post by tonyr1988 on 2007-04-09
> **maxim1 said:**
> I dont know what to post up as nothing happens, i double click the azureus icon and nothing happens :confused:

Open a Terminal (Applications >> Accessories >> Terminal) and type:

> azureus

What happens? Copy and paste the output into a reply.

---

### Post by david_kt on 2007-04-09
> **maxim1 said:**
> Ive been using Azuerus for a while on win Xp with no complaints, it would be nice to use it with Ubuntu. I have used bit tornado as well and preferred Azureus.

I have been able to use azureus without any problem until now (well, sometimes it did not download but I guess it was due to ISP block). But now I change to utorrent, because it is small, faster download, but give the same functions as azureus. If you face speed problem (may be due to ISP) you could improve the speed by enabling encryption. I don't think azureus has this function.

You could try the standalone utorrent with wine in linux, it works.

DK

---

### Post by tonyr1988 on 2007-04-10
> **david_kt said:**
> I have been able to use azureus without any problem until now (well, sometimes it did not download but I guess it was due to ISP block). But now I change to utorrent, because it is small, faster download, but give the same functions as azureus. If you face speed problem (may be due to ISP) you could improve the speed by enabling encryption. I don't think azureus has this function.

You could try the standalone utorrent with wine in linux, it works.

DK
Not to start a flame war, but I switched from uTorrent to Azureus because it's got a ton of more features. If you don't use them, great - uTorrent is a great client to get things done simply. However, the biggest thing I've felt Azureus has the upper hand in has been seed management. I had to change my seed queue / priority quite often in uTorrent to make sure I got the ones I wanted to seed on top. I have rarely (and only on extreme circumstances) had to do this in Azureus. Of course, that's completely subjective, but that's a big thing for me.

But if the OP wants Azureus to work, and it's not, then we still need to get it working for him. Choice is good. :)

(and yeah, Azureus has encryption, if we're talking the same thing)

(reiterate: I didn't mean to start a flame war...it's awful late, though. :P)

---

### Post by david_kt on 2007-04-10
> **tonyr1988 said:**
> However, the biggest thing I've felt Azureus has the upper hand in has been seed management. 

I have never create seed file, just download and re-seed. May be that is why I don't see any advantage of big azureus as compared to small utorrent but a waste of resources?

DK

---

### Post by rockrerun on 2007-04-10
I'm having the same problem.  Are you using Feisty?  Azureus works great on my Edgy machine, but won't start up in Feisty.  I'm not sure if this is a problem w/ Feisty or not, but as of now, that's the only difference I can see between my two computers...

---

### Post by maxim1 on 2007-04-10
out put 

exec: 40: java: not found

---

### Post by ClinicalMistake on 2007-04-11
There's a problem with the 2.5 binary currently.  There's a fix floating around on the forums.  Lemmie try and find it.  It involves you switching to the 3.0 beta


I believe this link has the answer.  Try this.
[http://ubuntuforums.org/showthread.php?t=193660](http://ubuntuforums.org/showthread.php?t=193660)

---

### Post by maxim1 on 2007-04-15
Ok still having no joy with this, has any one have any other suggestions ?

---

### Post by Digitallysick on 2007-04-15
I have the problem here is what fixes mine, i go to my home folder, and i press ctrl+H to see hidden files, go into .azureus , then go into the logs folder if you see a file that says "default_log or alert_log" delete it, then run azureus again, mine will work fine after i do that, i think the file crashes it somehow?  let me know if it works for you

---

### Post by Derrkus on 2007-04-16
> **Digitallysick said:**
> I have the problem here is what fixes mine, i go to my home folder, and i press ctrl+H to see hidden files, go into .azureus , then go into the logs folder if you see a file that says "default_log or alert_log" delete it, then run azureus again, mine will work fine after i do that, i think the file crashes it somehow?  let me know if it works for you

I had the same problem that Azureus quits right after it shows up. Deleting the log files resolved the problem for me at least for now. Hope Azureus won't crash anymore. Thanks!

---

### Post by maxim1 on 2007-04-18
I tried the above fix but no joy, so I have removed java versions 1.4 and 1.5 completely  using synaptic packedge manager. I also removed azureus, I then reinstalled version 1.5 using add and remove. To confirm the installion I then type java -version but get a command not found I also try with sudo in front but same result.
please can some one point me in the right direction

---

### Post by alex_anthony on 2007-04-18
try running this in the terminal
cd azureus
./azureus

what happens?

---

### Post by tenzen on 2007-04-21
I dont know if it is related to what you all are experiencing or not but i fixed mine like this:

1) rm -r ~/.azureus/*
2) run azureus and set it up as per the way you had it before (directories and such)
3) re-add the existing torrents.   They should find the default directory that you stored them before, do a quick check and then continue downloading..

enjoy

---

### Post by Thangalin on 2007-04-24
Remove GIJ and install Sun's JVM.

It seems GIJ, which is the Java Virtual Machine installed by Feisty, cannot handle the connection load required for Azureus to perform properly.

1. sudo apt-get remove gij
2. rm /usr/bin/java
3. Download Sun's JVM ([http://java.sun.com);](http://java.sun.com);) try "Java Runtime Environment (JRE) 6u1"
4. Install Sun's JVM into /opt/jdk1.6.0
5. Set your PATH to include /opt/jdk1.6.0/bin
6. Close your shell window.
7. Open a new shell window.
8. Run Azureus.
9. Help -> About
10. You should see "Java 1.6.0" in the "System" pane.
11. Enjoy faster download speeds!

---

### Post by crav on 2007-04-24
Had this exact problem yesterday. Here's the thread that solved my issue:
[http://ubuntuforums.org/showthread.php?t=413192]("http://ubuntuforums.org/showthread.php?t=413192")

---

### Post by maxim1 on 2007-06-23
Ok at last sorted it , link to thread which did it for me [http://ubuntuforums.org/showthread.php?t=481318&highlight=azureus]("http://ubuntuforums.org/showthread.php?t=481318&highlight=azureus")

---

### Post by goodtimetribe on 2007-06-23
> **Digitallysick said:**
> I have the problem here is what fixes mine, i go to my home folder, and i press ctrl+H to see hidden files, go into .azureus , then go into the logs folder if you see a file that says "default_log or alert_log" delete it, then run azureus again, mine will work fine after i do that, i think the file crashes it somehow?  let me know if it works for you

thank you! didn't quite exactly work, but it put me in the right direciton.

i didn't have those two files, so I simply did this since it was the only other file in the folder:

```

rm debug_1.log

```

---

