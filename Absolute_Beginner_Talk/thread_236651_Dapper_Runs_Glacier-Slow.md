---
title: "Dapper Runs Glacier-Slow"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by Beastmouth on 2006-08-15
I have a homemade computer, about five years old.  It's pretty decent hardware, 1.3 GHz Athlon, Geforce 2, 40 gig HD.  However, Ubuntu is slower than anything I can even imagine to make a metaphor.  Molasses in winter comes to mind, though.  I am very new to Linux and Ubuntu (<2 wks), and I would greatly appreciate any help.  

I am not talking about games not running, or any heavy computing.  All I am doing is trying to browse the internet, rip CDs, listen to some MP3s and use Nautilus.  This is very difficult to do, however.  Here are the problems I'm encountering:

I have MP3 support working, after major effort, however, often when I open a new application Rhythmbox just quits making any noise, or skips horribly.  

Characters are often quite slow to show up on the screen.  I almost always have to type slower than I'm used to, and when I use GAIM, the program cannot keep up with my typing.  There, I can type an entire paragraph and still see nothing but a blinking cursor.

Opening up Nautilus or a Terminal usually takes half a minute to a minute.  I cannot understand this at all; it's just a file browser or a command line, shouldn't this be a relatively light thing to open?

If Rhythmbox is running I accidentally click on an MP3 file as I'm moving it around on the GUI, it will attempt to play using mp3123 or something.  This has happened twice, once I had to go to System Monitor to find out what was happening, as the MP3 program playing what I had clicked showed up nowhere else.  The second time this happened it completely froze my system, I could move the cursor but my mouse buttons and my keyboard did nothing and I had to reset.  


Those are the issues I am experiencing, can someone help please?  
I also tried changing my NVidia drivers from nv to the nvidia ones from the repos, but came upon errors in enabling which I found a thread to help fix.  I'd try searching more for help, but my computer works so slowly (even though I have a decent connection) that it is highly ineffective when I don't know exactly what to search for.

---

### Post by JerMe on 2006-08-15
Missing a vital part here... how much memory does it have?

I have an Ubuntu box downstairs with a 1.3GHz Athlon XP, ATi 9200se, 512MB pc2100, which works nicely.

---

### Post by Beastmouth on 2006-08-15
I don't remember off the top of my head and didn't want to reboot.  :/  

Is there some way to find that on Ubuntu or do I just have to reboot?

EDIT:  Also, though, I know enough was put in when it was built to run XP just fine.  My cousin who built it's a real big gamer, so he made sure I had a pretty good bit, so I know it's something that fits in pretty alright w/ the specs I listed.

---

### Post by JerMe on 2006-08-15
System > Administration > System Monitor > Resources Tab

below Memory and Swap History, there's User Memory:  xxx MiB of xxx MiB

---

### Post by Beastmouth on 2006-08-15
250.2 MiB, then.  

And my CPU usage stays high 90s.

---

### Post by JerMe on 2006-08-15
The GeForce2 and 256MB of ram worries me.  I know that 256MB of ram is on the low end of what Ubuntu Dapper can run.  The GeForce2 I'm sketchy on.

You might want to give Xubuntu a shot.  It uses XFCE which is supposedly lighter than GNOME, which Ubuntu uses.
[http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/](http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/)

---

### Post by Beastmouth on 2006-08-15
Thanks, I already have burned the CD for that a week ago, thinking this might be the problem.  I didn't install it yet tho b/c I wanted to be sure about reg Ubuntu.  Thanks, I guess I'll try a partitioned install tomorrow (5 a m's a little late for me to be doing installs!)

---

### Post by eccentricity on 2006-08-15
> **Beastmouth said:**
> Thanks, I already have burned the CD for that a week ago, thinking this might be the problem.  I didn't install it yet tho b/c I wanted to be sure about reg Ubuntu.  Thanks, I guess I'll try a partitioned install tomorrow (5 a m's a little late for me to be doing installs!)

Well, hello everyone! Yea, new here to ubuntu and the community. I must say that I'm impressed. Everyone seems helpful and friendly and I'm glad to be here. I'd be even more glad to have a better idea of what I'm doing instead of fumbling around so much with gnome that I feel clueless...

Is there a difference between "Xubuntu" w/ default and "Ubuntu" w/ sudo apt-get install xubuntu-desktop? 

If I install Ubuntu and apt-get xubuntu desktop, is it the same as having a fresh xubuntu install? Does the xfce environment only access specific applications to it (gtk2??)or does it access the gnome apps also?:-k

---

### Post by JerMe on 2006-08-15
> **eccentricity said:**
> Is there a difference between "Xubuntu" w/ default and "Ubuntu" w/ sudo apt-get install xubuntu-desktop?

> If I install Ubuntu and apt-get xubuntu desktop, is it the same as having a fresh xubuntu install?

Yes, and no.  Installing xubuntu-desktop in an existing Ubuntu installation will install XFCE but will have a heavy amount of GNOME libaries still present for the GNOME desktop.

---

### Post by wog on 2006-08-15
How much ram does default Ubuntu want? What's optimal? Is there an upper limit?

---

### Post by JerMe on 2006-08-15
I've read reports where 256MB of RAM wasn't sufficient for the install.   It'll install if you manually enable swapspace, I'm not sure how it'd run normally.  I'm not willing to find out. ;)

---

### Post by derouge on 2006-08-15
As someone suggested definitely give Xubuntu a go. It might take a little getting used to. I switched from Windows to Ubuntu (with Gnome) and a few days ago installed Xubuntu. Gnome worked a lot like Windows, but XFCE just feels a little different .. not in a bad way, though. I'm running Xubuntu on a system very similar to yours and it's **fast**. Good luck!

The minimum RAM is listed here: [http://www.ubuntu.com/download/releasenotes/606](http://www.ubuntu.com/download/releasenotes/606)

256MB RAM and 3GB of HDD space.

---

### Post by klytu on 2006-08-15
> **Beastmouth said:**
> I have a homemade computer, about five years old.  It's pretty decent hardware, 1.3 GHz Athlon, Geforce 2, 40 gig HD.  However, Ubuntu is slower than anything I can even imagine to make a metaphor.  Molasses in winter comes to mind, though.  I am very new to Linux and Ubuntu (<2 wks), and I would greatly appreciate any help.  

I am not talking about games not running, or any heavy computing.  All I am doing is trying to browse the internet, rip CDs, listen to some MP3s and use Nautilus.  This is very difficult to do, however.  Here are the problems I'm encountering:

I have MP3 support working, after major effort, however, often when I open a new application Rhythmbox just quits making any noise, or skips horribly.  

Characters are often quite slow to show up on the screen.  I almost always have to type slower than I'm used to, and when I use GAIM, the program cannot keep up with my typing.  There, I can type an entire paragraph and still see nothing but a blinking cursor.

Opening up Nautilus or a Terminal usually takes half a minute to a minute.  I cannot understand this at all; it's just a file browser or a command line, shouldn't this be a relatively light thing to open?

If Rhythmbox is running I accidentally click on an MP3 file as I'm moving it around on the GUI, it will attempt to play using mp3123 or something.  This has happened twice, once I had to go to System Monitor to find out what was happening, as the MP3 program playing what I had clicked showed up nowhere else.  The second time this happened it completely froze my system, I could move the cursor but my mouse buttons and my keyboard did nothing and I had to reset.  


Those are the issues I am experiencing, can someone help please?  
I also tried changing my NVidia drivers from nv to the nvidia ones from the repos, but came upon errors in enabling which I found a thread to help fix.  I'd try searching more for help, but my computer works so slowly (even though I have a decent connection) that it is highly ineffective when I don't know exactly what to search for.

Trust the previous responses from those more knowledgeable than me, but I am really surprised that you are having problems with speed. I am running Ubuntu with the default Gnome environment on a 400Mhz Pentium II, 300MB RAM, ATI/Radeon 7000 64MB AGP graphics card and performance is VERY good. I would bet heavily that you're having an issue with the performance of your graphics card the way it's set up. I mean I am not a gamer, other than some retro gaming with Xmame, but unless 42MB extra RAM makes a huge difference I can't see another obvious reason for your set up to run that slowly.

---

