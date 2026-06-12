---
title: "Can't Install 6.06, 6.10, or 7.10 on Emachines T1090"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Xarok on 2008-02-25
So I tried all three of these Ubuntu Desktop versions
(6.06, 6.10, and 7.10)
and they won't work on this old desktop of mine 
(Emachines T1090, 900 MHz Celeron 128 MB RAM)

6.06 and 6.10 give me I/O errors.
7.10 just hangs after the load page.

Got any ideas?

---

### Post by thisiam on 2008-02-25
you should check out the alternative install. text only

---

### Post by bwallum on 2008-02-25
128Mb RAM looks very minimal. Can you increase it to 256 plus? Also beware early BIOS constraints. E.g. I have recently tried to install Ubuntu on a partition that started half way through a harddrive. The Bios would only allow a Master Boot Record at the beginning of the harddrive. Make sure your have the latest BIOS firmware installed specifically for your motherboard. Good luck. I've salvaged many an old bit of kit and given it a new lease of life with Ubuntu (7.10) so its worth persevering.

---

### Post by agim on 2008-02-25
your ram might be a little slim. I don't think any ubuntu other than one running xubuntu for fluxbox will work well for you.
There are some great distros made to run on minimal ram.

Zenwalk is the next step from fluxbox. And smaller distros are Damn Small Linux, Feather Linux, and Puppy Linux. The last one I have used and can vouch for. It will run faster than any Windows computer you've ever seen, and it will do it on your 128MB (or even less).

But if you are new to linux and looking to get comfortable. I would download the Xubuntu Alternate Install and go from there.

---

### Post by Xarok on 2008-02-25
> **agim said:**
> your ram might be a little slim. I don't think any ubuntu other than one running xubuntu for fluxbox will work well for you.
There are some great distros made to run on minimal ram.

Zenwalk is the next step from fluxbox. And smaller distros are Damn Small Linux, Feather Linux, and Puppy Linux. The last one I have used and can vouch for. It will run faster than any Windows computer you've ever seen, and it will do it on your 128MB (or even less).

But if you are new to linux and looking to get comfortable. I would download the Xubuntu Alternate Install and go from there.

What I ultimately want to do is run a LAMP server either 
Ubuntu Server 6.06 or 8.04 (when it comes out)
with the Xfce desktop environment.

I actually have 192 MB, my bad, 
and when I take the ram from my current server,
it should be at least 256 MB

The reason I want to use Xfce with my webserver is because I'm a lasey bitch.
I'm sick of using text commands to load files onto my server and move them around and renaming them etc.

I just want to simply stick in a thumb drive and place the files in the folder with a mouse

---

### Post by agim on 2008-02-25
lol, Xubuntu should run well there. 256 should be plenty. Good luck, go with the alternate install. And make sure to check your md5sums and check your cd for errors!

---

### Post by jc836 on 2008-03-13
Just loaded 7.10 on our T1090 with 256 megs of RAM.  Strongly recommend that you upgrade memory with this machine anyway. 6.10 may load with 128, but is iffy at best.  I am using the package from the Ubuntu download page and created the CD using InfraRecorder.  Make sure that your Blank CD and the drive are compatible.

---

### Post by hitbyambulance on 2008-03-18
currently attempting to install Xubuntu Feisty on the 'rents old eMachines T1090 - RAM had been upgraded to 384MB. unfortunately, the HD appears to have been damaged and won't fully install - but the liveCD runs well.

---

