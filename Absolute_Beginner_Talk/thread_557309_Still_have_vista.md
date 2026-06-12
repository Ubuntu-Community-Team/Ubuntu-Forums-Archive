---
title: "Still have vista?"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Major Crash on 2007-09-22
I've tried lots of things now, and I'm just afraid of messing things up.  

I got a new laptop, Toshiba.  got it about 4-5 months ago.  It came with Windows Vista Home Basic.  2 days ago I thought I'd try dual booting vista.  Now I'm not even sure if I have vista on my hard drive anymore.  Is there any way to check for Vista?  I'd like to just switch back to Vista.  Ubuntu doesn't seem to be my thing right now.

---

### Post by HokeyFry on 2007-09-22
uh.... unless you have the install cd for vista or you have a recovery partition that came with your computer... ur gonna be getting used to ubuntu. vista doesnt like to be loaded by grub, i think it probably is possible, but it escapes my knowledge. thats the main reason ubuntu is my main OS now, because i couldnt reinstall the vista bootloader.

ill do some digging though, maybe ill find something

---

### Post by HokeyFry on 2007-09-22
if you do need help configuring ubuntu for what you need to do though, ill be glad to personally assist you

---

### Post by 22bsti on 2007-09-22
this may not be the appropriate forum for this (as what you are asking is more of a MS related question rather than an ubuntu related one), but here goes, from my expierence, vista has a repair function on the install media.  Meaning if you have a recovery disk, or install disk you should just be ale to pop it in and click "Repair" instead of "Install".  Dont click install or you will make windows try and reinstall which would be bad if you have data you still need to backup such as a report for school or music or something.  Some OEM's nowadays dont provide recovery disks and instead use a recovery partition or have some proprietary program and expect you to create your "recovery kit" after booting windows for the first time with a blank cd or dvd.  If you fall into the latter category, you still have a few options, they are just a little more distasteful.  Either way if you reply back myself or anyone here can try and help you.  best of luck

---

### Post by CaptainInsaneO on 2007-09-22
You could try going into Partition Manager in Ubuntu and setting your vista partition as bootable. I've seen this work for a couple people. For some reason Ubuntu doesn't play with Vista very well, and vice versa.

---

### Post by Jeroen Vernooij on 2007-09-22
So you don't now for sure if Vista is still on your computer?
How did you install Ubuntu? Did you choose for guided partition editing or did you just choose 'automatic'?

If you don't know anymore, just install the package **gparted** and post a screenshot of it.

---

### Post by DOH on 2007-09-22
this worked for me.  i am running vista and ubuntu 7.04 on an hp pavillion dv9000.  I cant seem to get my wireless card working though.

go to this site
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

I am pretty sure you have to have windows installed first for them to get along.

---

### Post by Major Crash on 2007-09-22
I just chose the Automatic setting when installing from the disk.

Am I just out of luck if I didn't use Vista's Partition thing?

---

### Post by Duck2006 on 2007-09-22
From the terminal type

sudo fdisk -l

and post the output that will show if you still have a windoze partition/s

---

### Post by Jeroen Vernooij on 2007-09-22
In that case, your whole harddisk was wiped, and you don't have Vista anymore on your computer.
If you got a Vista repair/recovery DVD with your computer, insert it into your DVD-drive.
If not, you should contact Toshiba to obtain one, or install Vista via other ways.

---

### Post by Maestro23 on 2007-09-22
> **Jeroen Vernooij said:**
> In that case, your whole harddisk was wiped, and you don't have Vista anymore on your computer.
If you got a Vista repair/recovery DVD with your computer, insert it into your DVD-drive.
If not, you should contact Toshiba to obtain one, or install Vista via other ways.


Can't tell ya how many people I know that didn't make a Vista repair/recovery disc.  Then when they ran into trouble...

Hopefully Major C made one or his system came with one.

---

### Post by Major Crash on 2007-09-22
> **Duck2006 said:**
> From the terminal type

sudo fdisk -l

and post the output that will show if you still have a windoze partition/s

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9400    75505468+  83  Linux
/dev/sda2            9401        9729     2642692+   5  Extended
/dev/sda5            9401        9729     2642661   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

---

### Post by HokeyFry on 2007-09-22
it looks like vista is there, but if you dont have a repair cd, you may be out of luck
id get on the phone with your laptop customer service and ask them if they can send you a repair cd
if you dont want to though you could always stick with linux for now

what exactly dont you like about ubuntu, like does it not do something you need it to that windows did?

---

### Post by Duck2006 on 2007-09-22
Do you have two hard drives on your system? I
f so if you go in to your BOIS and change to boot from your other drive thats the one with vista on it. From what it looks you do. If it was a recover partition it would be on the same drive as your vista install is.

---

### Post by Major Crash on 2007-09-22
As far as I know I only have 1 drive.  

I have a zune, so windows is kinda important, unless you know of a way I can run the zune hardware.

---

### Post by CaptainInsaneO on 2007-09-22
> **Major Crash said:**
> As far as I know I only have 1 drive.  

I have a zune, so windows is kinda important, unless you know of a way I can run the zune hardware.

Looking at the output of your fdisk -l, you have two hdds, not one.

---

### Post by Duck2006 on 2007-09-22
> I have a zune, so windows is kinda important, unless you know of a way I can run the zune hardware.

There are some posts on that in this form i looked it up one time for a friend, forget where the post are or what they are called, do a search in this form.
Go to zune's website and see if linux drivers are listed.

---

### Post by Major Crash on 2007-09-22
I have an external harddrive, would that be it?

---

### Post by jrusso2 on 2007-09-22
Yes its showing your external drive probably which means the main hard drive has only Linux on it.

---

### Post by Major Crash on 2007-09-22
Which means that everything that was on my hard drive is gone?

---

### Post by jordanmthomas on 2007-09-23
Indeed it is.

---

### Post by Major Crash on 2007-09-23
dang.  Thanks for all the help, people.

---

