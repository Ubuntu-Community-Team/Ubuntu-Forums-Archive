---
title: "*gulp* ... how to access my linux filesystem by using Live CD"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2007-07-08
The question below is:  --> **I am using the LiveCD right now, and I need to access my *installed* linux filesystem where my old /boot/grub folder is located.**
Edit:  My current terminal prompt is ubuntu@ubuntu and I need it to be username@ubuntu.  That would get me in there, I know it.  I just don't know how to do it.
Edit2: It seems this might be possible if I can mount the partition containing my previous ext3 installation.  I am researching that in the (memory-loaded) stab right now.

Well an hour ago ... I did a dingbat, and I altered the binary file called 'stage2' which is a part of the GRUB loader.

Now (after doing that) my GRUB just gets stuck after stage 1.5 .

I have tried to repair this by:
   (a)  booting live CD and using sudo grub application from terminal to rewrite grub to MBR.  Didn't work.  That surprised me, it always worked before - but then again I messed up the stage2 binary file.

   (b)  booting Super Grub CD.  Tried repair operations with it, didn't work.

   (c)  booting GAG Boot Manager, but won't boot into linux when GAG is written to MBR.

NOTE:  I am able to use options (b) and (c) to boot Windows, just not Linux.

So right now I am using the LiveCD desktop.  I need to know how to login to my Ubuntu installation from here, so that I can get to my original /boot/grub menu.  (Fortunately I made a backup of that stage2 binary before I messed with it.)

THANKS!!

---

### Post by forestpixie on 2007-07-08
Can you not see your linux partition in nautilus? I was in there in the week and could see all my partitions.

Running nautilus from the terminal would get you in I thought?

gksudo nautilus - and show hidden files

then be careful

---

### Post by Average_Joe on 2007-07-08
That's a great idea.  I will give Nautilus a try.
I never use Nautilus, so I didn't think of it.
I am installing Nautilus right now, as I am using the Xbuntu LiveCD which doesn't have Nautilus installed by default.
Thank you and I will follow up!

---

### Post by forestpixie on 2007-07-08
use the Xubuntu file manager then - can't remember it's name though 

gksudo though

---

### Post by forestpixie on 2007-07-08
thunar

---

### Post by Average_Joe on 2007-07-08
> **forestpixie said:**
> Can you not see your linux partition in nautilus? I was in there in the week and could see all my partitions.

Running nautilus from the terminal would get you in I thought?

gksudo nautilus - and show hidden files



Well Nautilus doesn't show the partitions eithe.  In fact Nautilus doesn't even show the NTFS partitions, which native file manager Thumar does do.  (This has to do with where Nautilus is being told to look for mounting file systems.)

I feel quite certain that I can do this, if I can figure out the appropriate line in /etc/fstab to add.

I have created a directory (mkdir) and have added what I feel should the correct line to /etc/fstab but it always gives me an error about the filesystem.  (I have used 'ext2fs' and 'ext3' each.)

Also, my ext3 partition is an extended partition and that may be causing problems??

Thanks again.

---

### Post by forestpixie on 2007-07-08
Well as much as I'd like to be able to help more I don't think I can - I could see all my partitions when I needed to. They were just listed in the left hand pane - but not mounted I don't think, until I double clicked them, then they mounted and I could get in, sorry.

:(

---

### Post by Average_Joe on 2007-07-08
No problem, I appreciated your idea.
I'm going to try booting a Knoppix Linux LiveCD
and see if that gives me access.
I need only to accomplish a very simple cp (copy) command I will be done, I am sure of it.

---

### Post by forestpixie on 2007-07-08
Well good luck anyway - see you on the other side I hope :)

---

### Post by Average_Joe on 2007-07-08
anyone else able to help?  The situation in the first post still exists.
I can see my files using Knoppix, but do not have ownership over them so that I can't complete my simple little cp operation.

---

### Post by brennydoogles on 2007-07-08
Isn't there an Install Grub option from terminal that will help you??? Also, the live cd will have a default copy of the binary you borked, maybe you could mount your partitions ```
sudo mount /dev/YOURDRIVE
```
and then copy from the live cd's /boot/grub folder to your own. Just an Idea

---

### Post by Average_Joe on 2007-07-08
> **brennydoogles said:**
> Isn't there an Install Grub option from terminal that will help you??? Also, the live cd will have a default copy of the binary you borked, maybe you could mount your partitions ```
sudo mount /dev/YOURDRIVE
```
and then copy from the live cd's /boot/grub folder to your own. Just an Idea



Both worthy ideas to be sure.  I'll just give some information from my experimentation to explain why those don't work.  (I tried them.)

There is a grub-install command (and even a 'grub module', on the Live CD) which is designed to do the trick.  Unfortunately, if a grub loader already exists (albeit mortally wounded) this grub-install (grub module) won't overwrite the stage2 file that I had screwed with.  There is an option (--stage 2 option) in the grub-install command, but I couldn't get it to do the trick despite reading helpful commentaries about that command.

As for the LiveCD having a copy of the stage2 file that I borked, the LiveCD actually does not contain a copy of this file.  In fact, the /boot/grub of the LiveCD is very different from the /boot/grub (having been installed) in the file system of an installation of Ubuntu.

I was able mount the partition desired, and even get to the actual file in question and its backup.  But unfortunately, I could not get the ownership of the file changed over to me as root in Knoppix.  I tried some helpful online manuals to do so, but it remained read-only.  A more experienced *nix person could probably have done it.

So in the end I just blanked out my hard drive partitions related to linux and am reinstalling now.  It was a good education, though!

---

