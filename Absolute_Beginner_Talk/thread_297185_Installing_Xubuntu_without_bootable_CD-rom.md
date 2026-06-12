---
title: "Installing Xubuntu without bootable CD-rom"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by antonioclandestino on 2006-11-10
Hello everyone,

I have an old laptop, Compaq Presario 1700 HD15GB RAM 256MB, with a defect CD-rom player. I managed to get Windows XP on it with the bootable setup disks which recognizes the USB external CD-ROM drive.

The BIOS doesn't have an option to boot from an USB device.

Does Xubuntu have setup disks to install from an external drive?
If Yes, can you explain how this works.

Remember that I am just a beginner :) :confused: :)

---

### Post by bodhi.zazen on 2006-11-10
[Try this](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by scrooge_74 on 2006-11-10
I just don't remember to much of windows after so many months, but you should be able to make a boot disk and then download everything.  I know you can make a net install on Debian ( I am new here also), so you should be able to make a boot disk using another machine.

Good luck

---

### Post by antonioclandestino on 2006-11-10
Thanks for your answers but I don't see how these links can help a beginner with linux. :(

---

### Post by scrooge_74 on 2006-11-10
you can take a look at this net install from debian

[http://www.debian.org/distrib/floppyinst](http://www.debian.org/distrib/floppyinst)

---

### Post by bodhi.zazen on 2006-11-10
> **antonioclandestino said:**
> Thanks for your answers but I don't see how these links can help a beginner with linux. :(

The link I gave you gives step by step instructions.

Is there some part you do not understand?

---

### Post by scrooge_74 on 2006-11-10
> **bodhi.zazen said:**
> The link I gave you gives step by step instructions.

Is there some part you do not understand?

Don't be mean to the poor guy, some are slower learners than others, specially when you are not use to things as you are.

---

### Post by bodhi.zazen on 2006-11-10
> **scrooge_74 said:**
> Don't be mean to the poor guy, some are slower learners than others, specially when you are not use to things as you are.

LOL :lol: I thought I was trying to help! Without knowing at what step he is getting lost it is hard to help !

---

### Post by scrooge_74 on 2006-11-10
> **bodhi.zazen said:**
> LOL :lol: I thought I was trying to help! Without knowing at what step he is getting lost it is hard to help !

You never heard the one about calling tech support because the PCs does not start?

And when tech guy arrives to check on problem finds out the PC was unplugged?

I have seen that twice

---

### Post by bodhi.zazen on 2006-11-10
> **scrooge_74 said:**
> You never heard the one about calling tech support because the PCs does not start?

And when tech guy arrives to check on problem finds out the PC was unplugged?

I have seen that twice

I'll try that with my IT department to see how long it takes them to figure it out !

Want to wager ?

---

### Post by Shibby73 on 2006-11-10
1. What is Fluxbox
2. What is ICEVM

Do either of these cause the box to use USB for installing items from the BIOS?

---

### Post by scrooge_74 on 2006-11-10
> **bodhi.zazen said:**
> I'll try that with my IT department to see how long it takes them to figure it out !

Want to wager ?

They will probably have to take the machine to their department to check on the power supply, because it may be that or a bad mother board..... LOL

---

### Post by scrooge_74 on 2006-11-10
> **Shibby73 said:**
> 1. What is Fluxbox
2. What is ICEVM

Do either of these cause the box to use USB for installing items from the BIOS?

It was the other link under "try this"  [https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by bodhi.zazen on 2006-11-10
> **Shibby73 said:**
> 1. What is Fluxbox
2. What is ICEVM

Do either of these cause the box to use USB for installing items from the BIOS?

LOL: They are window managers, alternates to gnome/KDE/XFCE.

Screenshots:

[ Fallen Angel (fluxbox) ](http://img179.imageshack.us/img179/6141/200609272321061600x1200scrot3rc3.jpg)

[[color=navy]Space (icewm ; Dual Monitor)[/color]](http://img226.imageshack.us/img226/1095/200610061148233200x1200scrothu6.png)

both are faster. follow my sig for more info.

---

### Post by bodhi.zazen on 2006-11-10
> **scrooge_74 said:**
> They will probably have to take the machine to their department to check on the power supply, because it may be that or a bad mother board..... LOL

Worse, they turff out ALL HARDWARE....

I would be without a box for weeks :(

[indent]Plugs in box[/indent]

[indent][indent]Encrypts certain files[/indent][/indent]

Problem solved.

---

### Post by antonioclandestino on 2006-11-11
Thanks Shibby73, that was usefull info.
I wrote the sbm.bin from the Xubuntu CD to the formatted floppy.
I started up my PC and it still doesn't recognize the external USB CD-ROM drive.

"Tab->system settings->Enter->Rescan all boot records->enter"
didn't give any results.

Any suggestions? :(

---

### Post by scrooge_74 on 2006-11-11
> **antonioclandestino said:**
> Thanks Shibby73, that was usefull info.
I wrote the sbm.bin from the Xubuntu CD to the formatted floppy.
I started up my PC and it still doesn't recognize the external USB CD-ROM drive.

"Tab->system settings->Enter->Rescan all boot records->enter"
didn't give any results.

Any suggestions? :(

I think you should consider looking at a Debian net install booting from a floppy

---

### Post by antonioclandestino on 2006-11-11
I can't believe there is no solution for this issue.

---

### Post by bodhi.zazen on 2006-11-11
> **antonioclandestino said:**
> I can't believe there is no solution for this issue.

The only other solution would be to update your BIOS. Contact your laptop maufacturer and see if any such update is available.

You can also look at this thread: [Boot CD from floppy](http://www.ubuntuforums.org/showthread.php?t=246486)

---

### Post by antonioclandestino on 2006-11-11
@bodhi.zazen,

Thanks for your help but this gives the same result. 
Bios update is very risky. The BIOS doesn't show the BIOS version. HP/Compaq helpdesk said that they can't give anymore assistance with equipement over 5 years old.

Maybe I will try another distro.


I guess Windows XP is the winner here. :( :( :( :(

---

### Post by scrooge_74 on 2006-11-12
But did you check how to do a network install from a floppy?

---

