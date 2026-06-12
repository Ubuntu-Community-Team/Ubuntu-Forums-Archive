---
title: "[SOLVED] Compaq Armada problems"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by nomis3613 on 2007-11-10
Hi,
I just installed Xubuntu 7.10 on my compaq armada M700. I gave it a 3 GB partition and I have 256 MB ram. My wireless card is a Realtek RTL8180. After I enter the password for my router, the laptop freezes. There is no response whatsoever and the Caps Lock and light to the right of it (arrow pointing down to a horizontal line) flash. I also had this problem when using the LiveCD, I think it was at the repartition stage. It'd be great if someone could help me solve this so I can escape the clutches of XP...
- What type of freeze is this? Is it thermal overload?
- Do I need to install special drivers for my wireless card? How do I do this? (I have no previous experience in Ubuntu)
- Do I need to install video card drivers? Again, how? It mostly works fine, but there are some graphics artifacts sometimes.

Thanks heaps,
Simon

---

### Post by Daveski on 2007-11-11
Are you saying that the Xubuntu system runs fine until you try to connect to your wireless network?

---

### Post by nomis3613 on 2007-11-20
> **Daveski said:**
> Are you saying that the Xubuntu system runs fine until you try to connect to your wireless network?

Thanks for your interest Dave. Sorry if I was confusing in my first post...

Yeah, I haven't tried to do much else in it, but I tell in to connect to my VPN, it asks me for the network key, I put it in then the computer locks up.

Thanks,
Simon

---

### Post by Daveski on 2007-11-20
Does this help:

[http://ubuntuforums.org/showthread.php?t=584046&highlight=Realtek+RTL8180](http://ubuntuforums.org/showthread.php?t=584046&highlight=Realtek+RTL8180)

---

### Post by nomis3613 on 2007-11-21
> **Daveski said:**
> Does this help:

[http://ubuntuforums.org/showthread.php?t=584046&highlight=Realtek+RTL8180](http://ubuntuforums.org/showthread.php?t=584046&highlight=Realtek+RTL8180)

Yes! (well, sort of). They seem to be describing exactly the problem I am suffering. Only problem is, as a complete Xubuntu ignoramous, I have no idea how to follow their instructions to fix it. Can someone please walk me through it in baby steps?

And I hate to be greedy with all your great advice, but I can't access my windows partition anymore. It used to display as 5Gb volume but now I get a "hal-storage-fixed-mount refused uid 1001" error. Same as [this thread]("http://ubuntuforums.org/showthread.php?t=601210&highlight=mount+refused"). Again, I can see that it is solved on this thread, but I need the instructions translated into Totally Clueless speak.

Thanks heaps,
Simon

---

### Post by Daveski on 2007-11-21
The wireless problem is a bit more in-depth, so I would try to fix the windows partition problem first.

Can you post a copy of your fstab which can be found in /etc/fstab. This is a key system file so when logged in as your normal account you will be able to open it to read, but not to make any changes. You can copy the contents into a post here by:

Accessories -> Text editor
Open
Browse to *File System* -> *etc* and open* fstab*

Copy and paste the contents.

fstab is the list of which partitions are mounted at startup.

---

### Post by nomis3613 on 2007-11-24
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=36c7a273-386c-4587-b1b3-7dfc77ebda19 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=24e92bed-4fcd-4c9a-a408-b6b6fbb4f192 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Hope this is what you need for your prognosis, Dr Daveski! (and thanks for your help)

In the spirit of asking one question only revealing 2 more...I couldn't find the text editor under Accessories in the Applications menu (is that what it's called?). I found a file manager somewhere and opened fstab there, but is the text editor shortcut normally installed in Ubuntu?

And...I went to edit the menu.lst (to change the default OS in grub), but it wouldn't let me save changes, saying "can't open file to write"

Thanks for your help and patience,

Simon

---

### Post by Daveski on 2007-11-25
> **nomis3613 said:**
> I couldn't find the text editor under Accessories in the Applications menu (is that what it's called?). I found a file manager somewhere and opened fstab there, but is the text editor shortcut normally installed in Ubuntu?

Oops, my fault. In Ubuntu my instructions were correct, but you have Xubunut installed. This version has a text editor called Mousepad. Go to Applications -> Accessories -> Mousepad.

> And...I went to edit the menu.lst (to change the default OS in grub), but it wouldn't let me save changes, saying "can't open file to write"

Sure. This is because when you login to Ubuntu (or Xubunut etc) you are simply a user, not a full administrator. Only root (the full Administrator account) can access many of the system or configuration files, so opening fstab or menu.lst for READ-ONLY is fine, but to be able to make changes you need to run as root. This is one of the reasons that Linux / Ubuntu has a good security record because you (or malicious code you run) cannot destroy the system as it simply cannot change important files.

Your normal user account is granted the ability to 'sudo' to the root account. This means that you can run any app or a terminal session with full root access so long as you run the prefix sudo and type in your normal password. This is also the reason why Ubuntu fades the screen and asks for your password some times as you have run something which needs root access and this is what you are allowing when you type in your password again.

To run Mousepad as root with the ability to make these changes, enter a Terminal session and type 
```
sudo mousepad
```
Enter your password when prompted and then Mousepad will run as root - I think it even warns you that it is open with root access. As usual there are many more ways to do this without entering a terminal, but I'll leave that for you to find out.

Back to your problem. Is the NTFS drive always connected (i.e. it is internal), or is it connected via USB or similar? I am guessing this is a partition on one of your local internal drives.

You'll notice that the last 2 lines in your fstab are for the removable media of the CD and floppy - both of which have the option 'user' which allows normal users to mount and unmount these drives. The thread you pointed at suggests that a line in the fstab for your NTFS drive can be added with the 'user' option to allow the same rights as the CD / Floppy. Post back how your drive is connected and hopefully we can run some commands which will let us know what we need to add to the fstab.

---

### Post by nomis3613 on 2007-11-26
Thanks for the sudo trick, I'm sure that'll come in handy many times in the future (the plan is to totally abandon windows once I've got a grasp of Xubuntu).

The windows partition is a FAT32 partition of the same (only) internal hard drive that I repartitioned to install Xubuntu on. I would like read and write access to both partitions in Xubuntu. And ummm how do I open a terminal (yes, I am that clueless!)

Thanks

PS Nice signature!

---

### Post by Daveski on 2007-11-26
> Thanks for the sudo trick, I'm sure that'll come in handy many times in the future (the plan is to totally abandon windows once I've got a grasp of Xubuntu). 

This will become very important for any configuration work (or administration) you need to do, so it is good to get familiar with the concept.

> The windows partition is a FAT32 partition of the same (only) internal hard drive that I repartitioned to install Xubuntu on. I would like read and write access to both partitions in Xubuntu. And ummm how do I open a terminal (yes, I am that clueless!)

To enter a terminal, go to Accessories -> Terminal (this is Ubuntu and I don't have Xubuntu in front of me to check, but somewhere in the menus should be Terminal.)

When you have it open, type

```
sudo fdisk -l
```

*NOTE: Sudo means this will run as root and therefore could be dangerous. Always be wary of people asking you to type commands such as the one above as if they are being malicious they could be asking you to destroy your data/installation. *

fdisk -l (L is for List) asks the system to list disk partitions. If you are in any doubt as to the command you are running, try man <command> to find out what it does. e.g.

```
man fdisk
```

(scroll with the mouse wheel or cursor keys, q to quit)

Post the results of fdisk -l here so we can see your partition numbers etc.

> PS Nice signature!
Cheers.

---

### Post by nomis3613 on 2007-12-01
> **Daveski said:**
> 
```
sudo fdisk -l
```
Post the results of fdisk -l here so we can see your partition numbers etc.

Cheers.

Dave,
I didn't have much luck with the sudo command, so I just ran fdisk normally:
```
general@simon-laptop:~$ sudo fdisk -l
general@simon-laptop:~$ fdisk -l

Disk /dev/sdb: 524 MB, 524288000 bytes
255 heads, 63 sectors/track, 63 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c39f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          64      511968+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(62, 254, 63) logical=(63, 188, 61)

```
Is this useful? What do you think my problem is with sudo? I only remember entering the password for my "general" login, is this the password I need. I remember it spat out some other error first time I tried sudo and said something like "this incident has been reported".

Thanks,
Simon

---

### Post by Daveski on 2007-12-03
> **nomis3613 said:**
> Dave,
I didn't have much luck with the sudo command, so I just ran fdisk normally

Hmm, I think because you have run fdisk as the normal user you have only been given details of a drive which was mounted by that user. Do you have a memory card slot or USB attached?

The output you posted talks of /dev/sdb (i.e. a second physical disk) which is only 524Mb so I do not think this is the windows partition we are looking for.

Your laptop internal drive is called /dev/sda as shown by the fstab you posted earlier. The drive is sda, and so the partitions on this drive will be called sda1, sda2 etc.

The fstab shows that the Ubuntu partition is called sda2 so I would guess that the windows partition will be sda1 (as it was probably on the disk before you created the Ubuntu one). To confirm this we need to run fdisk as root.

> What do you think my problem is with sudo? I only remember entering the password for my "general" login, is this the password I need. I remember it spat out some other error first time I tried sudo and said something like "this incident has been reported".


You will only have created 1 password for your main account, but as this account is allowed (or at least SHOULD be allowed) to run sudo, then it is this same password that you type in when prompted.

If you are still having problems, can you describe what happens when you enter a terminal and type
```

sudo fdisk -l
```

It should prompt for a password. Type in your normal password and it should then run fdisk. If not, let me know exactly what happens.

---

### Post by Daveski on 2007-12-05
Sorry - may not check back here for a week or so. Anyone else help while I am away?

I am back checking the forums again. Has there been any progress on this problem?

---

### Post by nomis3613 on 2007-12-22
Hello from Xubuntu!!!

I never got the old wireless card working in Xubuntu, but then the card died anyway. So I plugged in my housemate's tp-link card to get back on the net in windows. Thought I'd boot linux and see just for the hell of it, and it worked! Without any fiddling!!

Since 99% of my PC use at home is web browsing and I've synchronised my firefox profiles, I can't see any reason to boot windows ever again. I've been fiddling with some settings and already it's obvious how much better linux is. But it's crashed a couple of times (file manager + a heap of firefox tabs open), nooo. But crash recovery isn't a big deal in linux (my instincts were still thinking I'd have to reboot!) so that's not too bad.

I still need to get write access to my files on the windows drive and I think I must have changed some setting when I installed Xubuntu. A couple of guys at work run linux, so I'm gonna take this laptop in because it'll probably be much easier for them to look around and figure out why I can't sudo etc.

Thanks! I'm sooo excited about this brave new world!!

By the way, I'm thinking of getting the D-link DWLG-630 because I had a look around and can't find too many people with problems. Could you let me know if this is a bad choice, please.

---

### Post by Daveski on 2007-12-22
> **nomis3613 said:**
> Thought I'd boot linux and see just for the hell of it, and it worked! Without any fiddling!!

Since 99% of my PC use at home is web browsing and I've synchronised my firefox profiles, I can't see any reason to boot windows ever again. I've been fiddling with some settings and already it's obvious how much better linux is. But it's crashed a couple of times (file manager + a heap of firefox tabs open), nooo. But crash recovery isn't a big deal in linux (my instincts were still thinking I'd have to reboot!) so that's not too bad.


I know what you mean. You can usually move a working Linux install by plugging the HD from one machine into another and most of the time it simply works with the new hardware. Also if you have lots of Windows experience it is odd not having to reboot everytime a system change is made.

> Thanks! I'm sooo excited about this brave new world!!

Welcome.

---

### Post by nomis3613 on 2008-01-23
Hi,
I took my laptop in to the resident Linux guru at work and it turns out that I'd created another login during installation that I wasn't even aware of. But it was called Simon and somehow I'd managed to create the General account I use as well, even though I don't know how to!! Anyway, he fiddled with some groups, permissions, and other stuff I don't really understand- and now I can sudo!

He also got me access to my windows drive, but said he used a dodgy method not the proper way to do it. But it works, anyway.

So thankyou for your help, hopefully I can figure out most problems myself, now that I have root access!

Simon

---

### Post by Daveski on 2008-01-23
Excellent - glad to hear you are up and running.

---

