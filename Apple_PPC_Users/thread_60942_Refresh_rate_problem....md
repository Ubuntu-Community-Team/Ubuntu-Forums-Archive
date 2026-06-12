---
title: "Refresh rate problem..."
date: 2005-08-29
forum: Apple PPC Users
---

### Post by iiJeebz on 2005-08-29
Hello One & All,

I have one extremely PITA problem here...

I have Ubuntu installed on a G3, and am using a TFT display that cannot handle refresh rates higher than 75Hz. No matter how often I set the default refresh rate to 75Hz, it resets to 85Hz when shut down/rebooted.
The only way around this (that I know of) is to grab another monitor, hook it up to the G3, then reset the refresh rate back to 75Hz... YES - this is a real PAIN IN THE REAR END!

No matter how often I set the rr to 75Hz (system/preferences/screen resolution), I just won't stick. And yes, I do tell it to make this change permanant and the default rr.

Does anyone have a solution, or failing that... how to 'fix' it without swapping monitors? i.e while it is booting up and still showing the command line..?

Thanks

---

### Post by ubuntme on 2005-08-30
look at a file called /etc/X11/x.org

you can use this command:
cat /etc/X11/x.org |less

Look for a line with vertRefresh and tell us what is says, or even copy and paste your entire x.org.conf.  

It is probably set to a range of values, e.g. 60-85.  If so, editing this line to have 75 will probably fil your problem.

---

### Post by iiJeebz on 2005-08-30
[QUOTE=ubuntme]look at a file called /etc/X11/x.org

you can use this command:
cat /etc/X11/x.org |less

Look for a line with vertRefresh and tell us what is says, or even copy and paste your entire x.org.conf.  

It is probably set to a range of values, e.g. 60-85.  If so, editing this line to have 75 will probably fil your problem.[/QUOTE]

Thanks for this suggestion... once I checked that conf file out it was obvious what the problem was - I had a Dell CRT monitor hooked up during the installation of Ubuntu.

No problem I thought, I just need to log in as root and edit the file... heh :)

Try as I might, I couldnt log in as bloody root. It never, ever occured to me that Ubuntu is not set up that way... I was tearing my hair out trying to remember what password I set for root... Anyway, a search brought up the fact that I needed to set up the root account. Never expected this in a million years as every other flavour of Linux I've used always let me log in as root without any B.S. I am still a newb to Linux by and large, but even so I wasnt too impressed by this, mainly because there was NO indication at any stage that 'root' was essentially non existant from a logging in point of view - it merely suggests the username or password is wrong. Anyway... now that I have vented... time to move on <g>

A quick look through all the options suggests to me there is no way to make Ubuntu re-detect hardware? I figured the simple solution (other than editing the conf file) would be to make Ubuntu look for a new monitor, but I did not find where to do this. I naturally tried Device Manager, but I didnt see any way to do it there?

Anyway, I have sorted this problem out at the least, thanks so much for the help, this is a great forum... plenty of helpful ppl. Thanks :)

---

### Post by ubuntme on 2005-08-30
hmmm, 

you shouldn't need to log on as root.  You can use sudo i.e. sudo vim /etc/X11/xorg.conf will open xorg for editing as root.  or you can open a terminal as root, somewhere in the gnome menu, I'm not sure where as I don't use gnome.

There is a utility to make an xorg.conf but I can't emember what its called, or even if there is one under ubuntu.  Besides, the important bits concern your vid card not the monitor.  Reading your monitor docs and entering the appriopriate modes into xorg.conf should work a treat.

good luck

---

