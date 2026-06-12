---
title: "missing progress bar in gutsy final?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Frank Golden on 2007-10-19
Hi all,
Just installed gutsy final and I noticed that on boot up nothing appears on screen while the machine is booting (animated progress bar etc) is this a bug or intentional. If intentional how do I get the progress bar back. I tried changing menu.lst entry from quiet to verbose no luck. I really like this visual cue that something is going on mostly for shutdown.
Any help would be greatly appreciated. 

BTW, I have been using gutsy beta for awhile but wanted to do a fresh install.

Thanks

---

### Post by Frank Golden on 2007-10-19
Hi all, After changing screen resolution in /etc/usplash.conf to 1280x800, my native resolution I got the progress bar back at shut down, but still nothing at startup. I did not have this problem with beta. What gives.

---

### Post by mistergq on 2007-10-19
I am having the same problem.  Also bootup seems to be taking longer than normal too.  This is happening with Kubuntu final.   I wanted to do a clean install because I was having a problem with sound after I had installed Ubuntu Studio.   

I am presently reinstalling 7.04 and was going to upgrade through 7.04 to 7.10 to see if that fixes the problem.

---

### Post by Frank Golden on 2007-10-20
Hi all, anybody? I find it hard to believe only a couple of are having the same problem.

Never mind the problem magically fixed itself. Don't know how or why. Don't you just love computers. LOL

---

### Post by jmcmegamega on 2007-10-20
Having the same problem too with an Amilo laptop (1280x800)... Very annoying. After grub does its thing, just "starting up..." appears and then nothing, black screen until the login page. Sometimes it's a short time, sometimes a long time... I wonder what happens when the hard disk is being checked... It should take a lot of time of blank screen.

Too bad because for the rest I have nothing to complain on gutsy... The first linux distribution I try which is able to recognize my wireless out of the box...

We got to find a fix!!!

---

### Post by rahimveron on 2007-10-20
Ya the screen goes black and my monitor light keeps blinking until we get the GDM login window.
Whats happening.
The same black screen and blinking of the monitor's light happens while shutting down.

---

### Post by jmcmegamega on 2007-10-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930](https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hej!

The only working solution I found was disabling usplash. You can do that by editing the grub options in /boot/grub/menu.lst.

Remove or comment out every word "splash" and the splash screen will not come out... Instead, you will get text explaining what the system is doing instead of a blank screen. I personally can live also without a graphical progress bar so the solution is fine for me. 

Also, it is now possible to access correctly to the text-mode consoles (ctrl-alt-F1 F6), which were not showing correctly before (wrong resolution or I dunno what. Now I finally have my ideal linux distribution... Too bad I can't still say everything worked out of the box for me... Hopefully the next time, as the usplash bugs will hopefully be fixed!!!!

Other solutions, which did not work for me (maybe I didn't try hard enough) can be found in the launchpad bug link.

JMC

---

### Post by Frank Golden on 2007-10-20
Hi all, I think I figured out how I fixed this issue. My usplash returned after installing the 8.41.7 ATI drivers using the ATI wiki that just got updated to include gutsy.

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Again I don't know why this should have made a difference, but it did.

BTW, I agree with the other posters I have no other complaints about gutsy.

---

