---
title: "EDGY - Distorted screen, can't even use the REAL terminal"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-10-27
Hi, I'm having an annoying problem with Edgy, which I just Clean-installed right now. So I got it installed then restarted and Logo  + loading bar seem fine. Then When it starts up X, I don't see anything, just a blank screen. I press CTR+ALT+F1 and it takes me to another screen that is really trashed. It's full of horizontal lines.. not even straight lines... **_it looks like a messed up, distorted barcode label_**. Anyway the screen is realy messed up. When I type something in, I see a white spot/shadow on the screen. When I press CTRL+ALT+F7 or F8 just to check out X again, the screen again is blank, except it has turned gray.

This is just after installing EDGY EFT. I haven't able to boot Edgy even once for now.

BTW, I was having the same problem with the liveCD, but when I used 800*600 to boot up the live CD, it worked for me (Even though Im sure the resolution was a lot higher than that when it booted up to the liveCD's X)

I'm on a desktop, Using an nvidia 7300LE (](*,) )

---

### Post by Dual Cortex on 2006-10-27
BUMP!
I want to use edgy!

---

### Post by Dual Cortex on 2006-10-27
Just bringing it up to the first page again...

---

### Post by Dual Cortex on 2006-10-28
Wow... I guess no Edgy for me and many. Seems like lots of people are getting blank screens.

---

### Post by compwiz18 on 2006-10-28
I'm no expert, but I'll see if I can help.  Did you try booting Edgy using no splash screen, and with the resolution set to 800*600?  That might help...

---

### Post by Dual Cortex on 2006-10-28
How do I set the res to 800*600... am I supposed to do that on GRUB?

As I said, same problem was happening to me with the LiveCD but when I used a low res it worked.

---

### Post by Perfect Storm on 2006-10-28
You could try starting it up in failsafe mode and then:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Dual Cortex on 2006-10-28
vesa driver seems to work... NV doesn't.
I guess I should try to install nvidia's bin. drivers

---

### Post by Perfect Storm on 2006-10-28
Then you can try with 9xxx beta drivers and see how it works on your system.

---

### Post by Dual Cortex on 2006-10-28
I need to login as root... how do I change root's password?

---

### Post by Perfect Storm on 2006-10-28
> **Dual Cortex said:**
> I need to login as root... how do I change root's password?

Why do you need to login as root?

---

### Post by Dual Cortex on 2006-10-28
wow. 
Ubuntu seriously shouldn't be this hard to start using. It was a pain in the ... to get it working. I have installed Nvidia's drivers. After numerous edits here and there, resintalls, etc. I succeeded in getting it working. I'm somewhat gifted when it comes to computer as lots of the forum staff and members in this forum are, and I'm not expecting a semi-average user to figure all of the steps I had to take. I f I remember everything I did step and step I would post the mto help he community ... but I just don't remember them.
(for nvidia pc's) In short details, I had to:
1) boot in failsafe mode (press ESC when you see GRUB's message right after you turn on your computer)
2) might be different in other computers: sudo dpkg-reconfigure -phigh xserver-xorg
Select the VESA driver and 1024*768 
3)restart your PC ... (CTRL+ALT+DEL)
4) IF it loads up KDE (or gnome) AND if MIRACULOUSLY your network works out of the box, go to nvidia's site and download their beta driver 9625 (im suggesting BETA drivers since those are the ones I used) Download them to your desktop and I recommend renaming them to nvidiadrivers.run (easier name to type in the console to start installation)

5) Set up a password for ROOT. On gnome... umm go to administration>users>find root (might have to select 'show hidden users' or something similar) then click on edit or modify somewhere then finally search for the fields to set up a password. Click OK/APPLY/etc...etc.

6)close all windows then hold CTRL+ALT+F1 and log in as root (type 'root' as username press Enter and type in your password...press enter) Then type "/etc/init.d/kdm stop" if you are on Kubuntu OR "/etc/init.d/gdm stop" if you're on gnome.

7) assuming you saved the driver on your desktop and it is named nvidiadrivers.run, type 'cd Desktop' press [ENTER]  then type 'sh nvidiadrivers.run'
Just press OK through everything. It will show a couple of warnings. I just OK'ed my way through the driver set up. If you are one of the unlucky ones, and you are unsuccessful during the st up then... I'm really sorry I have no answers for you.

8 ) after you're done with the set up, restart your PC. X DID NOT start after I restarted my computer after installing the drivers giving me an "API MISMATCH ERROR: module 1.0.7184 installed while this modules is 1.0.9625" or a similar sentence.
I don't know what the consequences for the following actions are but it was the only way to get my beta drivers to work on Dapper (I had received the same error on dapper while trying to install and use NVIDIA's beta drivers)
So, if your screen is blank press CTRL+ALT+F1 then type "/etc/init.d/kdm stop" if you are on Kubuntu OR "/etc/init.d/gdm stop" if you're on gnome, press ENTER. Next, log in with your normal account and type "sudo apt-get purge nvidia-kernel-common" and follow instructions to remove it.
**_NOTE IT SEEMS TO UNINSTALL SOME OTHER MODULES TOO_**

When done, if X server still doesnt load, CTRL+ALT+F1, log in as root, "cd Desktop", "sh nvidiadrivers.run" after installation is done try typing startx to see if X loads up. If it does restart your computer and see if it loads up by itself. If it doesn't then ... well I got no answers. Same thing Happened to me in all of my tries but then later after many many things I did, which as I previously said: "I dont remember", I was able to get Edgy working.

**_AGAIN LET ME WARN ANYONE WHO TRIES TO FOLLOW MY INSTRUCTIONS THAT I HAVEN'T USED LINUX FOR MORE THAN *3 WEEKS*(](*,) )._**
EVEN THOUGH I believe that this problem almost always occurs to people how have a clean install of ubuntu's EDGY so there wouldn't be much of a problem if something got messed up.

---

### Post by compwiz18 on 2006-10-29
Glad you got it working :D

---

### Post by mr.blacke on 2006-10-31
I can't either use command line to install edgy!!! I think that edgy hasn't improved anything except the boot interface at the beginning. Hope to make it work. Edgy developers should work more on Graphics card!

---

### Post by FRAMBO on 2006-12-21
> **Dual Cortex said:**
> Hi, I'm having an annoying problem with Edgy, which I just Clean-installed right now. So I got it installed then restarted and Logo  + loading bar seem fine. Then When it starts up X, ...

I've installed xubuntu and I get a trashed screen when X starts up.  It seems like the system is reinitializing the monitor which it is successful in doing as the system continues on to loading the desktop.  (I have automatic login enabled)  

When shutting down the same issues arises in between the desktop and the Logo + unloading bar.  

Should it be this way?  This is on a intel i810 video chipset...

---

