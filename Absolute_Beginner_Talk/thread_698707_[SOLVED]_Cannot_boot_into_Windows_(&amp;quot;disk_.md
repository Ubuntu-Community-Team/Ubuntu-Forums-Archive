---
title: "[SOLVED] Cannot boot into Windows (&amp;quot;disk read error occurred&amp;quot;) after installing Kubun"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by teknosexual on 2008-02-16
**Update: **

I have managed to boot into Windows.

I used TestDisk (on the Gparted Live CD) to rebuild the boot sector (was bad). So that part is solved at least.

At the moment, this is ongoing and you can follow the process over here if you are so inclined:
[http://kubuntuforums.net/forums/index.php?topic=3091469.0](http://kubuntuforums.net/forums/index.php?topic=3091469.0)

:)

*

I have XP Pro on one partition and Kubuntu (7.10) on another. After installing Kubuntu and rebooting, I can enter Kubuntu just fine. But when I reboot and choose Windows XP from the GRUB menu, I get the following error:
> A disk read error occurred
Press Ctrl-Alt-Del to restart
If I press Ctrl-Alt-Del, I'm taken back to the GRUB menu where the loop starts all over again.

I can see all of my data, etc, is still there through the filemanager in Kubuntu, so I know the install is fine.

I'm guessing this is a problem with the Windows master boot record? But I don't know how to fix it.

I tried using the recovery console from XP cd, and I ran fixboot but that merely made my GRUB menu disappear so i couldn't access either OS. So I tried using Super GRUB Disc, and I repaired GRUB, but I still cannot access XP (same error as before).

Here is my GRUB menu.list file:

> 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ba59ab13-3812-4b80-88dc-67c614f37ff0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ba59ab13-3812-4b80-88dc-67c614f37ff0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I searched the forums here and I see people with similar issues but they usually have 2 separate hard drives, and I only have one with partitions, so the solutions are not quite for me I don't think.

Thanks in advance for your help!

---

### Post by noname123 on 2008-02-17
you can try this but i don't know if it will mess up your grub 


[http://www.techzonez.com/forums/showthread.php?t=3975]("http://www.techzonez.com/forums/showthread.php?t=3975")

---

### Post by asmoore82 on 2008-02-17
go back to that XP recovery console and
```
chkdsk /p
fixmbr
```
then make sure XP works(oops! I mean "boots"),
then fix GRUB again.

---

### Post by agim on 2008-02-17
[http://ubuntuforums.org/showthread.php?p=4346336#post4346336](http://ubuntuforums.org/showthread.php?p=4346336#post4346336)
This is an easy fix using your livecd. Read a few posts, don't just run the first commands you see.
Also, check out the super grub disk for all of your mbr needs :)

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Edit: Read the post too quickly, didn't see that you already had tried some of this. My apologies.

---

### Post by teknosexual on 2008-02-17
Thanks for the replies. I was able to get it figured out, finally.

---

### Post by sandysandy on 2008-02-17
> **teknosexual said:**
> Thanks for the replies. I was able to get it figured out, finally.

you may like to post what finally worked.:)

regards

---

### Post by teknosexual on 2008-02-17
> **sandysandy said:**
> you may like to post what finally worked.:)

It's in my original post, at the very top. :)

---

### Post by sandysandy on 2008-02-17
> **teknosexual said:**
> It's in my original post, at the very top. :)

i read ur post at the top.

what i meant was you could post the solution that finally worked so that we could all benefit from your experience:)

regards

---

### Post by magicman5421 on 2008-02-17
> **teknosexual said:**
> **Update: **

I have managed to boot into Windows.

I used TestDisk (on the Gparted Live CD) to rebuild the boot sector (was bad). So that part is solved at least.

*

[rest of first post here]


He did post it...

edit: You should probably mark this thread as solved.

---

### Post by teknosexual on 2008-02-17
> **magicman5421 said:**
> He did post it...

edit: You should probably mark this thread as solved.

Thanks for pointing that out, magicman.

@sandy: I also added a link to my OP regarding the process I went through if you would like to read more closely.

I have already changed my topic title to (solved) ... but it does not show the change on the thread listing page. :confused: So, maybe a mod has to do that? I don't know...

---

### Post by sandysandy on 2008-02-17
> **teknosexual said:**
> Thanks for pointing that out, magicman.

@sandy: I also added a link to my OP regarding the process I went through if you would like to read more closely.

I have already changed my topic title to (solved) ... but it does not show the change on the thread listing page. :confused: So, maybe a mod has to do that? I don't know...

thanks:)

---

