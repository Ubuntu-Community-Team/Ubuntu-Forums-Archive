---
title: "Ubuntu not installing or starting"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by cronic5 on 2006-12-29
I am fairly new to Ubuntu. I have installed it on two machines and it worked fine. However, due to me not having probelms before, I didn't learn much except on how to install using a graphical interface. This time, however, I have come across a problem. 

I am using version 6.06 LTS. I run the CD as normal, and get to this point:

[Boot](https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=boot.png)

Afterwards, I get an error message saying something along the lines of using "apic=debug" then it goes on to say that I should use the "noapic" option. So, I restart, and get to the bootscreen again, press "F6" for more options, and at the end of the command type in "noapic". This time, I get to the point of where it begins to run the Live CD, but gets to another error (I am not sure what the error is, after I post this thread, I will be sure to try again, and write it down this time and get back to you). 

Based on the information I have given, is there something more I should do? If anymore information is needed, please don't hesitate to ask.

---

### Post by Mirrorball on 2006-12-30
Did you check your CD for errors?

---

### Post by cronic5 on 2006-12-30
> **Mirrorball said:**
> Did you check your CD for errors?

Yes. This is one of my many CDs that I recieved in the mail. These are the official CDs you can get from Ubuntu directly. I tried 4 different discs.

---

### Post by Mirrorball on 2006-12-30
I suggest you find out what that other error was and post a list of your hardware. If the CD is OK, it's a hardware issue.

---

### Post by cronic5 on 2006-12-30
Okay, so I put the CD in, and got to the boot options. I selected "Start or install Ubuntu". I got this message right after:

> 
Uncompressing Linux...Ok, booting the kernel.
[4294667.880000] ..MP-BIOS bug 8254 timer not connected to IO-APIC
[4294667.880000] Kernel panis - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the "noapic" option.
[4294667.880000]


---

### Post by Sef on 2006-12-30
> Yes. This is one of my many CDs that I recieved in the mail. These are the official CDs you can get from Ubuntu directly. I tried 4 different discs.

Sometimes the official cds are bad.  Have you tried them on another computer?  If you get the same result, then likely the cds are bad.

---

### Post by riven0 on 2006-12-31
Okay, when you put in the cd why don't you choose F6, (or the **other options** selection), and boot with the noapic parameter. That may work.

---

### Post by Sef on 2006-12-31
> Okay, when you put in the cd why don't you choose F6, (or the other options selection), and boot with the noapic parameter. That may work.

The Poster did.

> Afterwards, I get an error message saying something along the lines of using "apic=debug" then it goes on to say that I should use the "noapic" option. **So, I restart, and get to the bootscreen again, press "F6" for more options, and at the end of the command type in "noapic"**. This time, I get to the point of where it begins to run the Live CD, but gets to another error (I am not sure what the error is, after I post this thread, I will be sure to try again, and write it down this time and get back to you).

---

### Post by cronic5 on 2006-12-31
> **Sef said:**
> Sometimes the official cds are bad.  Have you tried them on another computer?  If you get the same result, then likely the cds are bad.

Yes, I have tried them on other computers, and I have tried 4 on this computer alone.

[quote=riven0] 	Okay, when you put in the cd why don't you choose F6, (or the other options selection), and boot with the noapic parameter. That may work.[/quote]

I tried that, too. Actually, when I do that I get another error. I will get what the error was now and repost.

---

### Post by cronic5 on 2006-12-31
Okay, so I did the "noapic" option, and here is what I got:

> 
Failed to start X server (your graphical interface). It is likely it is not set up correctly. Would you like to view the X server output to diagnose the problem?


I select "<yes>" And it takes me to the X server output. I select "continue" and I am told this:

> 
The X server is now disabled. Restart GDM when it is configured correctly.


---

### Post by MkfIbK7a on 2006-12-31
wow that sound like you are having a frame buffering problem what monitor are you using and was any os installed on the hardrive previosly?

---

### Post by cronic5 on 2006-12-31
> **wert613 said:**
> wow that sound like you are having a frame buffering problem what monitor are you using and was any os installed on the hardrive previosly?

I am using a Dell CRT monitor. I am not sure what the serial number or model numebr is as all stickers have been removed. It isn't that great of a monitor, and is probably around 4 years old.

And I currently have Windows XP installed on one partition, and trying to install Ubuntu on the other.

---

### Post by cronic5 on 2007-01-01
Bump.

---

### Post by MkfIbK7a on 2007-01-01
if you are still ther try to boot  in to recovery mode (press esc while grub is loading), when it gives you a prompt type startx or xinit 
and put the output here

---

### Post by gn2 on 2007-01-01
Try more of the F6 options, for me "noapic nolapic" worked.

Keep trying till you find a combination that works.....

---

### Post by cronic5 on 2007-01-01
> **gn2 said:**
> Try more of the F6 options, for me "noapic nolapic" worked.

Keep trying till you find a combination that works.....

I have tried all that I have found on google that other people have tried when they had similar problems.

[quote=wert613]if you are still ther try to boot in to recovery mode (press esc while grub is loading), when it gives you a prompt type startx or xinit
and put the output here[/quote]

Okay, I will try that and get post it.

---

### Post by Captian Entropy on 2007-01-03
I'm getting the same problem.

( Uncompressing Linux...Ok, booting the kernel.
[4294667.880000] ..MP-BIOS bug 8254 timer not connected to IO-APIC
[4294667.880000] Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the "noapic" option.
[4294667.880000] )


I installed 6.06 successfully(?) from an ShipIt cd (yes it checked it for errors and ran it on other machines) and upon reboot and grub loading, i selected the normal option for ubuntu and it spat out the error. I have tried the command line extensions of /apic=debug/ /noapic/ and /noapic nolapic/ (the latter getting me as far as the ubuntu logo on-screen and the system hanging after "loading some drivers" (the second module/thing it tried to load appeared on screen and it hung)).

I have successfully gotten ubuntu to load in recovery mode (words were scrolling too fast along the screen for me to notice anything about APIC errors) and after typing "exit" I could log into the system successfully so at least I know that gnome works. When I logged in and clicked on the "update" icon thing and the first update I saw was what appeared to be an APIC fix; however i could not connect to the internet (is there something I am supposed to do? - the LiveCD did it automatically and my router (NETGEAR DG834 v2) showed that it was connected correctly, or is this a "feature" of recovery mode?).

The only other information of note i can think off is that I tried installing 6.10 for 64 bit computers (i'm running a 3800+ x2) and it refused to install (or even test the CD), and I know the ISO was ok because it passed a checksum and after it failed I re-downloaded it from a different source and the same thing happened.

My system specs (if they will help?) are: 
3800+ x2
Asus M2N4-SLi mobo
2gigs of XMS2 PC 6400 DDR2 Corsair Ram
and a 7900GS.

If anyone can point me in the right direction I would love them forever.

Cheers

---

### Post by atlien on 2007-01-08
I think the problem is the mobo, the M2N4.  I have one and I can't get past the errors either.  I used the cd to install Ubuntu on another machine, an A7N8X-E.  That machine surfs the net now.  

The M2N4-SLI gets the apic error.  When I go 'noapic', I've gotten it to run off the livecd.  However, once Ubuntu is installed and the cd is out of the drive, I can't boot up.  I get a 'grub' error, too.
I have same problem as you with 64-bit version.  Unlike the 32-bit which gives me the apic error, the 64-bit won't boot, won't test.  Nothing.

---

