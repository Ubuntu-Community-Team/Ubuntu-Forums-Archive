---
title: "Ubuntu 7.10 install problems"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Seltox on 2008-01-27
I've had this Ubuntu install/live cd for about a month now, and I've just been given an old laptop.  The laptop isn't very good (something like 800MHz processor, 300 and something mb of ram, 20gb hdd, etc), and I decided to install Ubuntu on it.  I run Windows XP Professional and Fedora Core 7 on my desktop.

I started up the livecd (strange, the only way i've been able to get ubuntu to boot up on any of my computers is to edit the boot command line, removing the 'quiet' and setting 'nosplash' instead of splash.)

It took a while to boot up, as I expected with such a horrible computer.  once it was booted up it ran decently I guess.  I played a few games of chess and then tried to install.  Once the installer was open it lagged up horribly, taking a long long time to load any pages.  ESPECIALLY the keyboard layout select page.  I was fine with all this lag for now, but after the keyboard layout select page, it tries to open the partitioner.  It takes a VERY long time to even get up a screen where it shows in % how far loading or whatever it is.  Then this takes an _extremely_ long time to go anywhere.  During one attempt it took something 2-3 hours to get to about 60%, where it then gave an error.

I am currently (as I type this) attempting to install it again.  It has now been 'loading' the keyboard layout page for in ecess of 15 minutes now.

Is there some sort of text installer on this CD?  Or do I need to download another iso for that?  Because i'm not downloading anything if I have to.

---

### Post by Incense on 2008-01-27
With the low amount of ram you have, you may want to try the text based **Alternate Install CD**, it's found on this page. 

[http://releases.ubuntu.com/7.10/]("http://releases.ubuntu.com/7.10/")

it just uses the debian installer, and works quite well. Good luck!

---

### Post by MasterAslan on 2008-01-27
Is there an option to install a command line system?  If so then install that way and then run sudo apt-get install ubuntu-desktop.  It will install from the cd as this is a source until you remove it.

---

### Post by cecure on 2008-01-27
There is a text installer but you need to burn the alt iso for that.

Goto this page [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")and make sure you check the box that says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

Good luck

---

