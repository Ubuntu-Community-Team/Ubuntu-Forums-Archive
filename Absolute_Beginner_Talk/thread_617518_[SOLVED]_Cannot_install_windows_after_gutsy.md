---
title: "[SOLVED] Cannot install windows after gutsy"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by abicash on 2007-11-19
I had windows xp on the primary.I had kept space(14gb) aside for gutsy.I tried install through live cd.It installed good but i got the dreaded error 18.So now i partitioned the drive which had win.I formatted a 100mb ahead for /boot(ext3) and the rest fat32.Rest my gutsy drives.Like this i installed gutsy.And now grub can find it and i can boot ok into gutsy.But i dont have windows so with the fat32 of the previous win i put a win xp install disk but now i cant go beyond a blank screen.What should be done now?

---

### Post by duruttye on 2007-11-19
Well, hard one.
This what I would do:
format the whole drive with GParted in ntfs. Partition it, as you like, leave at least 4 GB for gutsy, after the XP install, try to install gutsy, too, that would keep in place the XP and grub too.

Hope it helps!
If anyone else has some better idea, don't hesitate.
Take care

---

### Post by Pumalite on 2007-11-19
I go along with the Gparted Live CD idea. Use to format the whole drive ntfs. Install XP. Boot the Gparted Live CD again and resize the XP partition (right click). I'd leave at least 20 GB for Gutsy. Then install Gutsy.

---

### Post by abicash on 2007-11-19
Thanks for the replies.:) but thats what i did earlier.Kind of.I have an older bios so after installing gutsy the grub have an error 18.So reading forums i partitioned the win 20gb to 100mb for /boot and the rest for win.I have a 160gb ide.And had 3 fat partitions where lots of data is present.At the end an ext3 14gb for gutsy.So i reformatted everything with the start for /boot.I instal gutsy now to the 14gb.Now grub gets to it.So i think lets instal win(and again gutsy. primarily the boot space wil be present)but now my instal cd doesnt go beyond a black screen.I hope i gave everything.I m writin this thro my phones internet its a bit hard to type.

---

### Post by houstonbofh on 2007-11-19
With an older bios, you entire /boot partition has to be low on the drive.  With one systm I had the /boot partition had to finish before the 100gig mark.  The plus i8s that while Windows would only see 200 gig of a big drive, Linux could see all 320 gig.  So it ended up being 90 gig windows, 10 gig /boot and the rest / and swap.

---

### Post by abicash on 2007-11-20
Oh yes i have been knowing that.Thats y i got the /boot very low before any partitions.So that grub recognises gutsy but how come win installation is not even getting through even though its got good 19gb fat formatted!

---

### Post by abicash on 2007-11-20
Ok.Now i m going through gparted.I see this
/dev/hdc2 149gb(#my hdd)
hdc9 /boot ext3 94mb
hdc10 fat32(#orig win)
hdc5 to 8 fat32(#30gb each of data)
hdc11 swap 1.8gb
hdc12 to 14 (ubuntu partitions)
i tried deleting hdc10 but it doesnt allow.So i reformatted it to fat32 again.I also need boot before that,right? I just dont want to ruin ubuntu and grub(i mean if it can be saved and something can be done to grub later but nevermind that,i can swipe off gutsy and reload it later)

---

### Post by daimaru on 2007-11-20
> **abicash said:**
> Oh yes i have been knowing that.Thats y i got the /boot very low before any partitions.So that grub recognises gutsy but how come win installation is not even getting through even though its got good 19gb fat formatted!

as far as i know linux has no problem booting from anywhere on harddisk, so your /boot could be right at the end.
windows is the one that has problems on older systems when its not the first partion on disk (exceeding the 1024 gig mark or something ) so just put windows as first on your disk make it ntfs not fat32 and then install gutsy somewhere behind it.

---

### Post by houstonbofh on 2007-11-20
> **daimaru said:**
> as far as i know linux has no problem booting from anywhere on harddisk, so your /boot could be right at the end.
windows is the one that has problems on older systems when its not the first partion on disk (exceeding the 1024 gig mark or something ) so just put windows as first on your disk make it ntfs not fat32 and then install gutsy somewhere behind it.
If the BIOS can not see that part of the drive it will not boot.  This is only important for booting...  Once the linux image is loaded it will see all of the disk.  For example, find an old P2 450 and put a 500 gig PATA drive in.  Install Windows and you will see 80, 160, or 320 gig depending on BIOS revisions.  Install linux with boot past what you see in Windows, and it will not boot.  Install Linux with boot inside of what you see in Windows and it will see all 500 gig.

---

### Post by abicash on 2007-11-20
So yesterday i backed up all my stuff and deleted all partitions including ubuntus(thank god all my data was stil ther).Only then was i able to get winxp in first c:16gb then got 3 more drives each 30gig.Then the one for gutsy.But havent got it installed yet.So i m now where i was a month ago.And i desperately want to get gutsy with windows on grub on a dual boot.Now please someone give me a newbie tutorial as to how this has to be done.I have searched and searched and frankly tired.So each and every thread i read drives me in a deeper pit.Though all the earlier help much appreciated.:)

---

### Post by abicash on 2007-11-21
Heloo
This is my first post through my computer (earlier were from my cell phone's internet).Although its Windows XP,that I have reconfigured and connected to internet through my gprs-bluetooth phone and a bluetooth dongle.(Its quite easy with Bluesoleil)
Since 2 days I was screwd.(see earlier posts) But XP is running ok now.
I have been reading about GRUB and the 1024 cylinders and I am able to understand that in theory,but whenever I implement this practically,the infamous ERROR 18 occurs telling me something of MBR being reset.(Windows being the culprit i guess)
Now I have set up XP in the first space of my disk with fat32 partition,followed by 3 nos of logical FAT32 partitions(which hold my indispensible data) followed by space for my ubuntu (which is just free space for now,not partitioned or formatted)

So now Is there a chance that I install Gutsy to the end and still my :confused: old BIOS recognises this?GRUB dual Booting (I mean)!
I am going through some tutorials as we speak,but again theres loads of information that I have read earlier that I am repeating and really dont know what seems right (I've tried almost all of 'em)

Further I am planning on bluetooth internet as well...but that in new thread

Thanks

---

### Post by Pumalite on 2007-11-21
XP needs ntfs.

---

### Post by abicash on 2007-11-21
Is NTFS mandatory for XP? I really am not sure.Check this [http://www.microsoft.com/windowsxp/using/setup/expert/russel_october01.mspx]("http://www.microsoft.com/windowsxp/using/setup/expert/russel_october01.mspx")
Also Linux may not write on NTFS.

---

### Post by meho_r on 2007-11-21
Just to confirm similar problem. Two days ago my WinXP crashed (what's new ;)) and I decided to make clean install (for Win I created ntfs partition, the first one). But when put install CD, there was a blank screen. I didn't think it was because of Gutsy, but now... Is it?

---

### Post by abicash on 2007-11-21
> **meho_r said:**
> Just to confirm similar problem. Two days ago my WinXP crashed (what's new ;)) and I decided to make clean install (for Win I created ntfs partition, the first one). But when put install CD, there was a blank screen. I didn't think it was because of Gutsy, but now... Is it?

The same thing with me,and I am learning more by the minute now!
This issue is because of the MBR(Master Boot Record).Your OS(es) will still be there but the bootloader may not know it is there.I have just downloaded the SUPERGRUB loader and according to the claims I hope it will boot into any of the installed OS(es)...Please correct me if I m wrong

---

### Post by meho_r on 2007-11-21
Well, I don't have problem with recognizing WinXP partition -- it is correctly displayed in GRUB and WinXP boots smoothly. The point is that I can't go through standard procedure of installing WinXP (boot from install CDs). I was lucky to managed to boot WinXP in Safe Mode and run installation from GUI because it is the only way for now. I don't like the idea of reinstalling Gutsy every time I need to reinstall Win

---

### Post by houstonbofh on 2007-11-21
Lots of stuff here...
> **Pumalite said:**
> XP needs ntfs.
This is incorrect.  XP will run fine on Fat32 if the drive is already formated.  Some versions of XP will not allow you to format Fat32 during install, but they will still run fine if you use gparted to format fat32.
> **abicash said:**
> Is NTFS mandatory for XP? I really am not sure.Check this [http://www.microsoft.com/windowsxp/using/setup/expert/russel_october01.mspx]("http://www.microsoft.com/windowsxp/using/setup/expert/russel_october01.mspx")
Also Linux may not write on NTFS.
This is also incorrect.  The linux ntfs filesystem is much better, and RW by default in gutsy.
> **abicash said:**
> Now I have set up XP in the first space of my disk with fat32 partition,followed by 3 nos of logical FAT32 partitions(which hold my indispensible data) followed by space for my ubuntu (which is just free space for now,not partitioned or formatted)

So now Is there a chance that I install Gutsy to the end and still my :confused: old BIOS recognises this?GRUB dual Booting (I mean)!

I do not know, as you have not provided enough information.  Specifically, disk sizes.  But, if you want to experiment, I can give you some steps to try.  **They will destroy your data!** Have good backups.

1) Go into the BIOS, and reset to defaults.  Turn off all devices you are not using, like parallel ports, serial ports, floppy drive, onboard modem... If you are not using it, free the IRQ.  Set up the drive for LBA mode.  Reset ECSD if you have that option.

2) Insert the XP CD, and format your drive, (NTFS of Fat32, it does not matter) without using and drive overlay or boot help.  Install XP to the entire drive.  Within XP, look at the drive size.  It should be significantly less than the size of the drive.

3) Insert a LiveCD with gparted (This can be the Ubuntu LiveCD) and look at the drive.  There should be a lot of space after Windows.  Shrink the Windows partition 125 meg.  Create a 100 meg /boot and devide the rest root and swap.  These can be all primary partitions as the total is 4.  If you want more partitions, it can be extended, but they will be at the end of the drive, and not available to Windows.  Most of linux will be unavailable to Windows.

If at any time the results do not match what is expected here, stop and post back.  (Specifically, if you format the entire drive, with no space left over.)

---

### Post by abicash on 2007-11-21
@houstonb
you mean i should get win on a single drive?But i normally make more than 2 partitions for my data.So that even i format my c: in win my other drives r ok.Currently i have c:15gig,e:30gig,f:30gig,g:30gig followed by 2 partitions 24gig and 20gig.Now i had the same thing 2months ago and had installed RedHAT and grub could boot into both oses.So why cant this happen with Ubuntu?

---

### Post by Pumalite on 2007-11-21
> **houstonbofh said:**
> Lots of stuff here...

This is incorrect.  XP will run fine on Fat32 if the drive is already formated.  Some versions of XP will not allow you to format Fat32 during install, but they will still run fine if you use gparted to format fat32.

This is also incorrect.  The linux ntfs filesystem is much better, and RW by default in gutsy.

I do not know, as you have not provided enough information.  Specifically, disk sizes.  But, if you want to experiment, I can give you some steps to try.  **They will destroy your data!** Have good backups.

1) Go into the BIOS, and reset to defaults.  Turn off all devices you are not using, like parallel ports, serial ports, floppy drive, onboard modem... If you are not using it, free the IRQ.  Set up the drive for LBA mode.  Reset ECSD if you have that option.

2) Insert the XP CD, and format your drive, (NTFS of Fat32, it does not matter) without using and drive overlay or boot help.  Install XP to the entire drive.  Within XP, look at the drive size.  It should be significantly less than the size of the drive.

3) Insert a LiveCD with gparted (This can be the Ubuntu LiveCD) and look at the drive.  There should be a lot of space after Windows.  Shrink the Windows partition 125 meg.  Create a 100 meg /boot and devide the rest root and swap.  These can be all primary partitions as the total is 4.  If you want more partitions, it can be extended, but they will be at the end of the drive, and not available to Windows.  Most of linux will be unavailable to Windows.

If at any time the results do not match what is expected here, stop and post back.  (Specifically, if you format the entire drive, with no space left over.)
*f you are going to use XP is silly to use vfat when ntfs is a far superior format. Besides, as you pointed out, Linux can read and write to ntfs.*

---

### Post by houstonbofh on 2007-11-21
> **abicash said:**
> @houstonb
you mean i should get win on a single drive?But i normally make more than 2 partitions for my data.So that even i format my c: in win my other drives r ok.Currently i have c:15gig,e:30gig,f:30gig,g:30gig followed by 2 partitions 24gig and 20gig.Now i had the same thing 2months ago and had installed RedHAT and grub could boot into both oses.So why cant this happen with Ubuntu?
Well, let me break this down into "musts" and "wants" to clear it up.

Musts:
No more than 4 primary partitions.
1 Windows and the Linux /boot partition must be bootable, and only primary partitions can be bootable.
The /boot partition must be low enough on the hard drive to be seen by the BIOS.
With a separate /boot partition linux **requires 3 partitions.**

Wants:
Lots of separate partitions make formatting simpler.
Different formats make for easier organization.

What all that means is that with linux taking 3 partitions, that leaves only 1 for Windows if you want them all primary.  If you want more, you will need 2 primary, Windows C: and Linux /boot.  After that, you cam make and extended partition with other stuff, but Windows may not see it as it continues after the limit Windows can see.  This is the problem with making hardware support other hardware beyond it's design specifications...  Things can get ugly fats.  By keeping your implementation as simple as possible, you minimize the ugliness.  While you can do everything you want, making sure it works can be a challenge.  Also, just because "it worked" doesn't mean it was right, or will continue to work.  For example, I put Linux on an old Compaq server just 2 partitions, / and swap.  It worked.  Later I updated the kernel with update-manager. (Minor patch.)  The new image was laid down on a part of the drive beyond the ability of the BIOS to see, and the system failed.  It took several days to track down why...

---

### Post by abicash on 2007-11-23
i think i will have to give rest to ubuntu for a week :(
I really thought it would be easy for a newbie/dummy(i m not one though) and I really know that is not ubuntus fault at all!
It is just that I have so little time on hands.

---

### Post by houstonbofh on 2007-11-23
> **abicash said:**
> i think i will have to give rest to ubuntu for a week :(
I really thought it would be easy for a newbie/dummy(i m not one though) and I really know that is not ubuntus fault at all!
It is just that I have so little time on hands.
This is a good week for it!  In the US, Thursday is Thanksgiving.  A traditional time to eat too much, and watch TV.  Also, there is some traditional self flagulation and shopping involved. :)  Feel free to use our vacation as an excuse any time!

---

### Post by abicash on 2007-12-17
:) So I figured out how to dual boot!I was trying this for so long now and with scarcity of time it was a herculian task (so it felt).
Since I had an old BIOS I created space just after my winxp C: for ubuntu and created just a swap and / with no separate /usr /home /boot So now my BIOS can boot ubuntu quite nicely....

Thanks all for the tips especially houstonbofh,w/o which it was pretty impossible for me to do that.:)

As it seems,its just the tip of the iceberg.I have yet to
1)Connect my nokia-phone modem via bluetooth to internet or learn to install some packages offline.
2)Get some eyecandy:guitar: (compiz/beryl) with my old nvidia riva tnt2/tnt2 pro 768mb ram)

Any quick tips/links?

Thanks again..much appreciated

---

