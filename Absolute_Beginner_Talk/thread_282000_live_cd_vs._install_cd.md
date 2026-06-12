---
title: "live cd vs. install cd"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Rory on 2006-10-22
I'm having a problem.  I boot the regular 6.10 RC 386 CD.  I goes through graphical ubuntu boot splash, but when it gets to the final stage where it's about to boot in to the live desktop, the screen goes blank/black.  Have never seen this on a distro before and I've used nearly every variation of Linux for three years.  Stumped.

So, I downloaded the Alternate CD, which seems to allow me to do a text-based install.  Thing is, I don't want to risk wiping my current version of Ubuntu on my HD only to discover that once the Alternate finishes the install, my screen goes black at the GDM Login again.  

I really am not sure how to proceed.  I'd like to figure out why my screen goes blank/black on the 386 CD, but I can't come up with an answer or a way forward.

Hardware Specs:
ATI Radeon 9200 SE video card
Compaq P1100 21' monitor and Acer 54e monitor
ASUS K8V SE Deluxe mobo
AMD Athlon XP 64 (I only load the 386 OS on to it, though)
512mb RAM.

update: Bug now filed. Testing updates below. [https://launchpad.net/distros/ubuntu/+bug/67487](https://launchpad.net/distros/ubuntu/+bug/67487)

---

### Post by wog on 2006-10-22
My only suggestion would be to go back to the install cd for Dapper 6.06 and update from there. 

Out of curiosity, did you try the live cd version before installing? Generally that lets you know without installing whether everything's going to work okay when you do install.

---

### Post by Foudre on 2006-10-22
hey, on the live cd one, the normal one, (i don't think the alternate had a live cd either) did you try to change some of the boot up options like the video options? you might want to try that

---

### Post by jorn on 2006-10-22
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by Sef on 2006-10-22
Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") site to learn how to dual boot and more.

---

### Post by Rory on 2006-10-22
Yes, I can't boot in to the Live CD (regular install CD).  I seem to be having the same issue with the Dapper CD.  Last Ubuntu CD I used was the Breezy one.  So, when Ubuntu changed the Live CD to be installable from their Live desktop, something changed around that time.  

Can you suggest any other boot options off the regular CD that might do the trick?  The second graphical option doesn't help.

---

### Post by alchimera on 2006-10-22
Had this problem too with the i386 alternate install... just after it was "configuring xserver-xorg" the screen blacked out... i figured that at the end of the install it would ask if i wanted to reboot... so i waited till activity stopped and hit <enter> twice and the disk ejected, closed the tray and hit <enter> again -> system rebooted perfectly!

---

### Post by Rory on 2006-10-22
UPDATE

Short story: no luck

Longer story: I downloaded the 6.10 RC DVD.  It booted, the boot splash screen moved through its paces, the screen went black and the white cursor appeared in the top left corner, and then it went to click over in to the desktop or GDM login (I haven't seen it to know what the next step is) and...  BLACK SCREEN.  

I've tried the first Start/Install default option.  I've tried the second Safe Graphics Mode option.  I used the F4 VGA mode and tried different modes, include 16bit (I usually do 32) and different screen resolutions.  

Same thing happens each time.  Now, the Text Install starts up fine, but without wiping my drive and doing a full install, I won't know if it's going to work, which makes me nervous, as you could understand, given my lack of luck so far.

So, I'm stuck.  Anyone have any ideas?  A different boot line, for example.  

And can anyone guess the root of this problem?  An Xorg issue?  Not good.

Thanks,
Rory

---

### Post by wog on 2006-10-23
It's beginning to sound like a video driver issue. It starts out okay, but then at the last minute it's black on black screen. 

Whatever linux uses as a default for the video may be the issue here. What sort of video card do you have?

---

### Post by Rory on 2006-10-23
I have an ATI Radeon 9200 SE.  From xorg.conf: 
"ATI Technologies, Inc. Radeon 9200 SE (RV280)"

I believe you may be right about the video driver issue.  I thought it might be my rare Compaq P1100 monitor, but I think I may have ruled that out.  

Further update:
I filed a bug, which I updated.  See below: 
[https://launchpad.net/distros/ubuntu/+bug/67487](https://launchpad.net/distros/ubuntu/+bug/67487)
[FONT=Arial][SIZE=3]
[/SIZE][/FONT]           [FONT=monospace][SIZE=3][FONT=Arial]I've done some more testing and I believe this is a real bug in the upcoming Edgy release.[/FONT]

 [FONT=Arial]I've used two monitors: Acer 54e (pretty generic monitor that works with everything) and my Compaq P1100, which is a more exotic 21" professional monitor, although the Compaq works with Breezy, Dapper, and recent Fedora and SuSE distros.[/FONT]

 [FONT=Arial]I ran a Dapper 6.06 CD with both monitors.
-The default Start/Install did not boot in to the desktop, going black after the boot sequence, identical to the above bug reported.
-The Safe Graphics mode did work with the Acer 54e monitor. It also worked with the Compaq P1100 when I chose VGA (I used the 768x1024 16 option).[/FONT]

 [FONT=Arial]The Edgy 6.10 CD or DVD does not get past the Ubuntu boot splash with either monitor, in either the Default or the Safe Graphics options, with or without using VGA mode options. It just doesn't boot in to the Desktop (formerly called Live CD).[/FONT]

 [FONT=Arial]Something has changed between Dapper and Edgy that will make it difficult for a certain number of people to boot in to the Desktop off the CD when checking out Ubuntu starting on Oct. 26th.[/FONT]
 [FONT=Arial]If people respond with possible workarounds (I need concrete steps), I'm happy to try to eliminate causes.[/FONT]
[/SIZE][/FONT][SIZE=3]

[/SIZE]           [FONT=Arial][SIZE=4]
[/SIZE][/FONT]

---

### Post by CatKiller on 2006-10-23
Out of interest, when you've got your black screen, what happens if you do a Ctrl-Alt-F2?

---

### Post by Rory on 2006-10-23
> **CatKiller said:**
> Out of interest, when you've got your black screen, what happens if you do a Ctrl-Alt-F2?

Catkiller, thank you for mentioning this.  Yes, I tried Ctrl+Alt+F1-F6 at this stage to bring up terminal and it didn't work.  This is what I had planned to do:
To reconfigure X from CD and re-start:
alt + ctrl + F6 
sudo dpkg-reconfigure xserver-xorg (reconfigure)
sudo /etc/init.d/gdm restart
Then cntrl+alt+f7 to go back to GDM 

Couldn't get past ctrl+alt+F6

---

