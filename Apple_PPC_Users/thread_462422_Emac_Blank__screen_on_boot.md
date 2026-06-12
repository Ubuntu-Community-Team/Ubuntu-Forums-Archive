---
title: "Emac: Blank  screen on boot"
date: 2007-06-02
forum: Apple PPC Users
---

### Post by [censored] on 2007-06-02
Hi. I've just tried the ppc desktop iso for Feisty, and I get a blanks screen when I should be getting a gnome desktop.

I've tried googling for a solution. I found this site:

[http://crowetech.wordpress.com/2007/04/14/ubuntu-704-beta-on-an-emac-part-1-installation/](http://crowetech.wordpress.com/2007/04/14/ubuntu-704-beta-on-an-emac-part-1-installation/)

I tried following the instructions there. Everything except changing the HorizSync and VertRefresh values, which didn't seem to be in my /etc/X11/xorg.conf anywhere.

Anyway, that didn't work. Can anybody help me on this?

---

### Post by stmiller on 2007-06-02
On some machines ESD is crapping out and causing gnome to hang after the login screen.
See if this fixes it:

(From the PPCFAQs)

> 

      Press CTRL+ALT+F1. Log in at the text terminal, if needed. Type

            killall esd

      and press enter. Press CTRL+ALT+F7 to return to the desktop. 
Go to Gnome's Sound Prefs and uncheck the 'ESD' box.


---

### Post by Auria on 2007-06-02
My problem was not exactly the same as yours, but lets share anyway ;)
to get my eMac to work, I had to 'sudo dpkg-reconfigure xserver-xorg' and change screen type from 'imac' to 'emac' then it worked

---

### Post by [censored] on 2007-06-03
Thanks for the posts guys. Unfortunately, neither of your suggestions seems to help, so I guess I'll have to use some other linux distro for my emac.

---

### Post by bencrowe on 2007-06-07
I had the same issues initially and tried 3 different ranges for vert/ hor. sync until I found the one that worked for me. Unfortunately, you DO have to modify that or you'll never get your desktop to display...
Feisty runs great on my eMac (700MHz / 512mb RAM)! I bought a Pioneer DVD burner for it and it works great! I now have my all in one entertainment solution for the garage...movies, music, and the 'net!

Ben

Links below:
[URL="http://crowetech.wordpress.com/2007/04/14/ubuntu-704-beta-on-an-emac-part-1-installation/"]
Installing Feisty on eMac - Part1 (Install)[/URL]

[Installing Feisty on eMac - Part2 (Basic config)]("http://crowetech.wordpress.com/2007/05/31/ubuntu-704-beta-on-an-emac-part-2-configuration/")

---

### Post by [censored] on 2007-06-07
thanks guys. Got the problem solved.

What it was: I had to insert the VertRefresh and HorizSync values into xorg.conf myself. They weren't actually in the xorg.conf on the live disk bootup.

I had a bit of trouble getting the syntax right at first, but eventually managed to get the desktop up and running and installed the OS.

---

