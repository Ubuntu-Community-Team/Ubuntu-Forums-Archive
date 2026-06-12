---
title: "[SOLVED] Help Me Quick Plz!!!"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by KuroRai on 2007-07-05
HELP ME!!! iJust installed Ubuntu 7.04 on my computer...

it's a 1.4 Ghz, 384 MB RAM, some video card (mp 64 MB), and a 250 GB MAxtor HD...

now before Ubuntu, iHad a 127 GB partition for windows...

iMade a 50 GB partition for Ubuntu, as well as a 5 GB Swap file...

the install went fine, using the Live CD ( iHave both Live and Alt. CDs)...

However when iRestarted the comp for the first time iGot a GRUB Error 18

nothign else came on... iHave NO idea what GRUB is, or what htis is about

help me asap plz!!! iAm using my comp. off the Live CD rite now!!!

Thank you in advance!!

More info :

iHave 2 partitions , one labeled ext3 the other Swap; the mount point for the ext3 is /

(Like the installer told me too)

---

### Post by Cypher on 2007-07-05
This is what [GRUB Error 18 ]("http://wiki.linuxquestions.org/wiki/GRUB#Error_18")means. GRUB is the boot-loader that will boot Linux and other OS' if it was found duration installation.

P.S, do you like the iPod, iPhone, i<Whatever> else????

---

### Post by annda on 2007-07-05
did you get something like that:
Error 18: Selected cylinder exceeds max supported by BIOS

can you type this in the terminal

```
fdisk -l
```

(small cap L, not i)

and copy and post the output here? (in terminal ctrl+shift+c copy the selected text into memory)

---

### Post by KuroRai on 2007-07-05
No, it just says Error 18, but iWill try your second part in a sec

---

### Post by KuroRai on 2007-07-05
iLove Apple!!!

---

### Post by Skrynesaver on 2007-07-05
GRUB (Grand Unified Bootloader) is the program that offers you a selection of OS; to boot from.
Error 18 means that the /boot/grub directory is not mountable as the partition it is on starts at a cylinder beyond that readable by your BIOS.

As you have the liveCD you could use it to boot the installed system.
escape to the grub menu then
root (hd0,1)                  if your ubuntu partition is on the second partition of the first hard drive
kernel /vmlinuz
boot 

Windows is slightly harder to boot as grub doesn't read the filesystem, again at the grub> prompt

rootnoverify (hd0.0)
makeactive
chainloader +1
boot

As your BIOS can't read beyond your windows install you may have to put in a /boot partition at the start of the drive.  Thus your drive would be partitioned as 4 partitions in the order
boot(32MB)|Windows|Ubuntu|swap

I hope this hasn't put you off the OS, unfortunately while it hides a lot of complexity from you, one of the most complex tasks most users ever undertake is the partitioning a multi-boot system, after that it's almost all plain sailing ;)

---

### Post by KuroRai on 2007-07-05
ok iTried that terminal thing, fdisk - l does nothing, it just jumps to teh enxt line

however if iType in just fdisk it gives me...

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

---

### Post by KuroRai on 2007-07-05
ok yea, iGet what you are saying about it being too far, iwndows can (as well as my bios) read only up til 127 GB... which i used all for iwndows....

as for your second part, could you explain it again in a bit plainer english plz :P

---

### Post by loserboy on 2007-07-05
iKnow this isn't helpful, but iLike to laugh at things that iSee like this

oh don't you have to use sudo with all the fdisk stuff

---

### Post by KuroRai on 2007-07-05
ok, iAm willing to put teh boot at the begining of my drive, BUT HOW DO I DO THAT?!?!?!

and no, this doesn't put me off ubuntu, it looks like a really good OS; and a need an actual stable OS for the summer when iNEed to get things done til iGet my new iMac...

---

### Post by jimbob on 2007-07-05
It looks like you left a space between the "-" and the "l" .

Try fdisk -l again from the terminal and post results.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by KuroRai on 2007-07-05
ok when iType THIS EXTACLY fdisk -l then nothign happens, however as iWas confused in your last post iTried a few other combinations, and fdisk - l give me this

ubuntu@ubuntu:~$ fdisk - l

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$

---

### Post by Bothered on 2007-07-05
> **KuroRai said:**
> ok, iAm willing to put teh boot at the begining of my drive, BUT HOW DO I DO THAT?!?!?!

That is tricky but can be done.

Type:

```
sudo fdisk -l
```

in a terminal and post the results (it won't work if it isn't preceded by sudo).

---

### Post by KuroRai on 2007-07-05
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       22933    50002312+  83  Linux
/dev/sda3           22934       23555     4996215   82  Linux swap / Solaris

---

### Post by Bothered on 2007-07-05
That's what I needed. Give me a few mins to type the response, it's a bit lengthy.

---

### Post by KuroRai on 2007-07-05
ok, iThink Skrynesaver has the right idea; he makes perfect sense (check page 1)

the problem is sticking the boot partition at the beginning of the HD wihtout damaging my windows partition (or my hardware)...

HOWEVER iMust do all of this from boot CDs, as iCAn't log into any OS

---

### Post by KuroRai on 2007-07-05
kk thanks bothered

---

### Post by Bothered on 2007-07-05
Ok, before trying this, make sure you back up all data. You should be able to access the Windows and Linux partitions, and burn data to a CD/DVD, or copy it via a memory stick etc.

1. Launch gparted (sudo gparted).
2. Select the linux partition (second on the drive), right click and select "resize/move". Increase the start point on the partition by 128MB.
3. Select the windows partition (first on the drive), right click and select "resize/move". Increase the start *and* end point by 128MB.
3. Select the newly created blank space on the front of the drive and select "new". Select start point 0, end point 128MB, and partition type ext3.
4. Click the "Apply" button.
5. You now need to reinstall ubuntu (this is the quickest way I can think to move GRUB onto the start of the drive in your situation). Run the install, and at the partitioning section select "custom partitioning". Set the mount point of the first partition to "/boot" and check the "format" box next to it. Set the mount point of the other linux partition (should be third on the drive, and ext3 partition type) to "/" and check the format box next to it.
6. Complete the remaining install steps.

Post questions if you hit errors/problems.

EDIT: If gparted refuses to resize/move a partition, launch a new terminal and type "sudo umount -a". You might need to do this more than once.

---

### Post by KuroRai on 2007-07-05
ok, iHave no DVD drive, only CD, which can't be sued becasue Live CD is in there... iBacked up my data just a few days ago when iGot my 2nd external dive, so iWon't lose anytign TOO drastic.. but 1) can iDo this wihtout backup and 2) what is the chance of somehthing drastic going wrong?

---

### Post by KuroRai on 2007-07-05
also iUnderstand what you are saying COMPLETLY, and i understand exactly what is happening, and see that ther is no cahnce of possible damage, however iAm not sure what would ahppen if there are files on the beginning 128 Mb (mp are) and if they were to be damaged in the move, hopefully windows is there, and if it does get damaged iCan just repair it.. but yea

---

### Post by KuroRai on 2007-07-05
btw, thanks for all your help bothered...

---

### Post by Bothered on 2007-07-05
No problem.

I do not know what will happen to the data on the front of the Windows partition. I cannot guarantee that you won't lose data on that partition, up to and including the operating system itself.

---

### Post by Bothered on 2007-07-05
> **KuroRai said:**
>  ther is no cahnce of possible damage

Unfortunately, that isn't the case. Data may be lost, which is why I recommend the backup.

---

### Post by KuroRai on 2007-07-05
ok, iWillt ry it without back-up, but iWill look thru my HD quickly jic...thanks...

---

### Post by KuroRai on 2007-07-05
ok, there isnt't, me is trying your plan now...

---

### Post by KuroRai on 2007-07-05
PROBLEM!!!

in gparted, all menu options (right-cliccking) are shaded out!!!

maybe iNEed to log in as root? or admin?

---

### Post by KuroRai on 2007-07-05
also the dircves are all mounted, oculd that be teh probelm? and lastly, there is a third partition alrdy, the swap file, what changes do iMAke to that?

---

### Post by diatribe on 2007-07-05
it sounds like the hard drive is mounted, partitions can not be edited while the hdd is mounted; you dont need to change the swap partition

---

### Post by Skrynesaver on 2007-07-05
You should ask this specifically to the forums in a new thread as I'm not at all sure.

You may have to reinstall windows after re-partitioning :(

---

### Post by Bothered on 2007-07-05
Try "sudo umount -a" in a new terminal. If the partitions are mounted (for reading/writing of data) they can't be edited.

---

### Post by Bothered on 2007-07-05
> **Skrynesaver said:**
> You may have to reinstall windows after re-partitioning :(

That's true. Asking for a second opinion is a good idea.

---

### Post by KuroRai on 2007-07-05
reinstall or repari? because from the windows boot CD you can repair, which as much as iKnow, deltes windows and reinstalls it keeping your files...

---

### Post by Bothered on 2007-07-05
KuroRai , I recommend that you do not proceed right now, as you sound a little panicked. Let me reassure you that your system is not in that bad a state, and can be recovered right now. My advice may work, or it may break Windows (which is almost certainly currently intact by the way). I would take a little time away from your computer, then come back when someone who knows more precisely what will happen when you move the Windows partition posts.

---

### Post by KuroRai on 2007-07-05
also, when iUnmount a HDD to resize/move, i can only unmount one HDD at a tie, so do iDo that? or should iStop?

---

### Post by Bothered on 2007-07-05
> **KuroRai said:**
> also, when iUnmount a HDD to resize/move, i can only unmount one HDD at a tie, so do iDo that? or should iStop?

I would stop, and wait for a second opinion.

---

### Post by KuroRai on 2007-07-05
iKnow windows isn't damaged, worest coe to worest iCAn coopy the iwnodws aprtition somewhere else, format my entire HDD, install uBuntu, and copy my aprtition back (or not install ubuntu) but that would take SO DAMN LONG... so yea...

---

### Post by KuroRai on 2007-07-05
sry for my bad seepling, iCan't type fast and spell nicely :P

---

### Post by KuroRai on 2007-07-05
spelling* :P

---

### Post by KuroRai on 2007-07-05
iGuess iCan wait for a while...

---

### Post by KuroRai on 2007-07-05
but iDon't think any exterem windows users will use linux, they generally hate OS X, linux, and thus hate free OSs and Unix as a whole.

---

### Post by KuroRai on 2007-07-05
(too help me with the windows repair delema)

but iGuess iWill wait til tomarrow, if no one answerws iWill go ahead with your plan, seeing as how theres nothign TOO IMP on my comp... thanks...

---

### Post by KuroRai on 2007-07-05
OK WAIT new info, gparted CANT move NTFS partition, BUT IT CAN RESIZE IT; resizing wont damgae my files will it!?!?!? if it wont, will it wrk if iAdd the /boot partition BEFORE the 127 GB limit, but AFTER the windows partition?

---

### Post by KuroRai on 2007-07-05
also, cna somone plz explain the whole swap partition thing? what is it for? does size amtter for it?

---

### Post by Bothered on 2007-07-05
Placing a boot partition after the windows partition is much safer, but less likely to work. It's probably a good idea to try it first, however.

The swap partition is virtual memory, used in addition to the physical memory in your computer.

---

### Post by KuroRai on 2007-07-05
ok iwill try that then... thanks for all your help guys!!!

---

### Post by KuroRai on 2007-07-05
iWill post any updates on this thred, thanks!!!

---

### Post by Bothered on 2007-07-05
OK, I got a second opinion from the irc channel, and it seems that the Windows partition can be moved. There are, however, the normal risks associated with editing partitions.

---

### Post by KuroRai on 2007-07-05
well gparted doesn't let me move it...

---

### Post by Bothered on 2007-07-05
In response to your message: No the boot partition doesn't have to be 128MB. That's just a convenient number. My boot partition is 128MB, of which just under 36MB is used.

Sorry to be so cagey in my responses by the way. I just want you to be aware of the risks of resizing and moving partitions.

---

### Post by Bothered on 2007-07-05
Can you select "Resize/Move"? If so, can you edit the start and end numbers? Have you resized the linux partition yet (moved it's start point)?

---

### Post by KuroRai on 2007-07-05
well iGuess resizing JUST my windows partition is the easiest and least destructive way no? and it seems that gparted knows exactly how much is used out of the partition and wont let me go beyond that, so as long as it targets only empty secotrs, (or a clump of empty secotrs omewhere in the middle)  there shouldn't be a porbleam no?

---

### Post by KuroRai on 2007-07-05
no, iHaven't touched the linux partition, which may have been the reaso for the no resizing, however the features menu in  gparted has a "x" on the moving part of NTFS

---

### Post by xtrm_redbull on 2007-07-05
Try this link [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) , it might help you in partitioning your hard drive. Good luck.

---

### Post by Bothered on 2007-07-05
I refer you to post 18 for complete moving instructions.

---

### Post by KuroRai on 2007-07-05
but which do you think would be asfer? moving linux then windows, or just resizing windows?

---

### Post by Bothered on 2007-07-05
Ah, I see the question. Let me give new instructions:

1. Launch gparted (sudo gparted).
2. Select the windows partition (first on the drive), right click and select "resize/move". Reduce the end point by 128 MB.
3. Select the newly created blank space on the drive and select "new". Create a 128MB ext3 partition to fill the space generated.
4. Click the "Apply" button.
5. Reinstall ubuntu. Run the install, and at the partitioning section select "custom partitioning". Set the mount point of the second partition to "/boot" and check the "format" box next to it. Set the mount point of the other linux partition (should be third on the drive, and ext3 partition type) to "/" and check the format box next to it.
6. Complete the remaining install steps.

If GRUB fails with the same error, then follow:

1. Launch gparted (sudo gparted).
2. Select the small linux partition (second on the drive), right click and select "delete".
2. Select the windows partition (first on the drive), right click and select "resize/move". Increase the start and end point by 128MB.
3. Select the newly created blank space on the front of the drive and select "new". Create a 128MB ext3 partition to fill the space generated.
4. Click the "Apply" button.
5. Reinstall ubuntu. Run the install, and at the partitioning section select "custom partitioning". Set the mount point of the first partition to "/boot" and check the "format" box next to it. Set the mount point of the other linux partition (should be third on the drive, and ext3 partition type) to "/" and check the format box next to it.
6. Complete the remaining install steps.

As before, execute "sudo umount -a" if options are greyed out.

EDIT: Correction to 5 on the second set of instructions.

---

### Post by jrfoleyjr on 2007-07-05
> **KuroRai said:**
> ...the install went fine, using the Live CD ( iHave both Live and Alt. CDs)...

However when iRestarted the comp for the first time iGot a GRUB Error 18

nothign else came on... iHave NO idea what GRUB is, or what htis is about

help me asap plz!!! iAm using my comp. off the Live CD rite now!!!

Thank you in advance!! 


I had the same thing happen when I tried installing 7.04 and 6.10 with the GRUB error... weird!  I have an old disk with 5.10 that installed perfectly.

Now I cant figure out how to update to a newer version. Update manager says I have latest software.


Needless to say, I am a total linux noob but have been using windoze (W2K and XP) for a long time and had a Commodore Amiga before that, ran a bbs on the Amiga.

---

### Post by KuroRai on 2007-07-05
ok it all wrks now!! Thanks Bothered!!! (altho iDid get an error after trying to resize it,m it did resize)

windows wrks as well... the iFanatic part of me is sad because of it :P

always, thanks to all of you guys who helped!

---

### Post by Bothered on 2007-07-05
Good to hear :) Good luck with the new system

---

