---
title: "Unable to reboot or power down Mac mini G4"
date: 2009-02-01
forum: Apple Hardware Users
---

### Post by nattugglan on 2009-02-01
Hi.

I've installed Ubuntu 8.10 Intrepid Ibex PPC on one of my Mac mini G4 boxes. The problem is I can't reboot or power down.

GUI or command line (i.e. sudo shutdown -hP now) doesn't matter, the screen goes black but the mini can't reboot or power down, it's just sitting there..

Has anyone come across this or know what the problem is? The last version of Ubuntu I had installed was 7.04 IIRC, and with that version there was no problem.

---

### Post by nattugglan on 2009-02-10
I've now tried 8.04.1 LTS PPC alternate as well, but with 8.04.1 I can't even get to the login screen after install.

On 8.10 the following works at the yaboot prompt:

> Linux video=ofonly nosplash

And it's possible to use the system. But on 8.04.1 none of the following work:

> Linux video=ofonly nosplash

> Linux video=ofonly

> Linux nosplash

Or the standard:

> Linux

The screen quickly goes black, the only thing visible for a short while is the initial text marker in the top left corner. After that, nothing.

Going with the black screen I've tried to get the Mac mini G4 to restart by using the keyboard shortcuts to access the alternative menu on the login screen (bottom left corner).
Either it doesn't get that far, or it won't reboot like 8.10..

Any suggestions?

.: nattugglan

---

### Post by nattugglan on 2009-02-12
When Ubuntu 8.04.1 LTS PPC alternate didn't work I tried installing **Debian 5.0 Lenny RC2** next (debian-Lenny-DI-rc2-powerpc-netinst.iso), and it works "out-of-the-box". Both the screen and shutdown/reboot.

Nice!

If somebody finds a solution for Ubuntu, please update the thread. I'm leaving it open.
Perhaps Ubuntu 9.04 Jaunty Jackalope will work as smooth on Mac mini G4 PPC as Debian 5.0 Lenny.

.: nattugglan

---

### Post by DonaldJ on 2009-02-17
Food for thinktanking, to push this dern glitch thing deeper...

_______________________________________________________


Where is there a list of All the commands that start Ubuntu..?

Where is the list of all Ubuntu commands, and their descriptions..?

Is there such a thing as a "floating command"..?,

a "zulu_spear command..?  ["zulu-spear", being the substance of the peak-emotion in being jilted]
  
Is there a list of all known cures to boot-lockups..?

Can there ever be a "tyrant-class inter-spacial_random self-propelled rubix-command" in Ubuntu..?  Are there "tyrant-class" commands yet..?

Are any commands classified by "heat"...

 _______________________________________________________


Off the top, I think this glitch is a root-bound password denial conflict, between password files, and security "boot-latch".. failing to bring-up the password window, given that there was a tiny password glitch pop-up during install of 8.04 LS...  One strange thing happens just before the iMac fails to load the new OS, is the hd is very hard shut-down.. so hard that its arms skid violently across the plater quite audible...  There's where the problem probably is...   Something in the program instantly shuts off the hd.. It might even be damaging to the Mac's hd..?

I left the install image CD in the iMac's slot, with the iMac running, for about an hour, while I worked on the PC...
Every half hour the CD would spin on its own, then stop, as if it had just finished running through the whole CD...  
I happened to hit Return, and the CD popped out of its slot.. Never saw that before.. I doubt that's part of the iMac's normal operation... Could that be an indicator leading to the place of the problem's hooks..?

---

### Post by DonaldJ on 2009-02-18
If the install were done with root open, wouldn't that eliminate all these install and boot glitches in Mac..?

Isn't running in a secure root format, a bit of an overkill when dong basic installs..?  So when the system is complete and solid, only then does root engage solidified...

---

### Post by jim_murple on 2009-02-19
i experienced the same problem with 8.10 (blank screen prior to boot OS). A way to solve it, is to plug the VGA adapter in the DVI port and connect a VGA monitor, then it seems that everything is going right after that. there's another physical workaround by introducing a small paperclip in the holes of your DVI port, but i can't remember where i put the link. hope it helped !

---

### Post by DonaldJ on 2009-02-20
The iMac only opens a command, and stops there, in using "Linux video=ofonly nosplash", I see that the date is set to January 1st 1904...  So I'm thinking that maybe the problem is that the Mac's steam boiler has run out of coal or seal-oil...  

It seems the problem might be in the date and time settings not holding, and creating glitchy conflicts...

---

