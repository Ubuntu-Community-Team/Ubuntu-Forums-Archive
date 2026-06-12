---
title: "GDM error at login"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by compsariomike on 2007-07-25
Alright.

I recently re-re-re-installed Ubuntu fiesty fawn 7.04 onto my computer(I ran into a few errors with the desktop live CD and it kept freezing).  I used the alternate CD and set it up on a 250GB Seagate external USB hardrive.  Windows XP Pro is on the main hardrive (a 30GB hardrive in my compaq persario R3000 laptop)  

In order for Ubuntu to load, I went in through BIOS and set the Seagate 250GB hardrive first in the boot order.  When this is done it loads into GRUB and I can select what I want to do.  

After selecting the first option (Linux kernel or whatever, the one that has worked before) the Ubuntu login screen loads.  I type in my user name and then my password.  After that I get an error window which states: 

"GDM could not write to your authorization file. This could mean you're out of disk space or that your home directory could not be opened for writing. In any case, it's not possible to login. Contact your system administrator."

I followed the instructions here...
[http://ubuntuforums.org/showthread.php?t=506334&highlight=GDM+errorr](http://ubuntuforums.org/showthread.php?t=506334&highlight=GDM+errorr)
...and it worked once.  I did this by going into recovery mode and typing it all without the "sudo" at the begining.  As i siad, this did work once.  The second time i had the error happen i thought it was because i typed it without the "sudo" and upon trying it a second time i used them.  When that didn't work I tried a third time without them again and it still didn't work.  

So now i'm stuck using windows until i can get some help.   Could someone please liberate me from the hell that is WINDOWS!!!!!
Thanks

---

### Post by Haegin on 2007-07-25
I would think it is because it is installed on an external drive so you may want to look at getting it installed on a second partition on the 30GB drive. I am not totally sure so you may want to check on the wiki and ask other users either on here or on IRC.

---

### Post by compsariomike on 2007-07-25
But after performing the instructions here:
[http://ubuntuforums.org/showthread.php?p=3059421](http://ubuntuforums.org/showthread.php?p=3059421)
I was able to access ubuntu and use it freely for a good couple of hours.  Then i restarted the system and got the GDM error.  I wouldn't think it's because of the dual hardrives.  Plus, as i stated with the re-re-reinstalling part, i've installed it before to where it worked fine.  Just now...it doesn't.  And i'm highly confused because i'm still learning the basics of Ubuntu and Linux

---

### Post by Haegin on 2007-07-25
Did you reformat your /home partition or did you keep your old one? Try removing the .ICEauthority file in your home dir and making sure your new user and your old user have the same UID and username if you kept the old partition. To get access boot in recovery mode and add a new user with the useradd command (run "man useradd" for more details).

---

### Post by compsariomike on 2007-07-25
Yeah, I  completely reformated the drive where Ubuntu was and is installed.  The Username and Password are the same.  

I'll try what you said and report back soon.  Thanks for helping (i've been up all night trying to find threads on how to fix it and haven't found much)

---

