---
title: "Cannot boot without cd"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by petrockthief on 2006-09-01
I've installed Ubunut creating my own partitions or doing it automatically probably 10 times now. But I still can't boot unless I use the Live CD. The text reads something about mounting the boot partition but never okays it and then goes into a terminal screen.

---

### Post by taurus on 2006-09-01
You probably either forget to include "root=/dev/xxx" in your kernel or have "root=/dev/xxx" pointing at the wrong directory where your / is resided!!!

---

### Post by TFX360 on 2006-09-01
> **petrockthief said:**
> I've installed Ubunut creating my own partitions or doing it automatically probably 10 times now. But I still can't boot unless I use the Live CD. The text reads something about mounting the boot partition but never okays it and then goes into a terminal screen.

Could you mount you /boot in the live-CD?

Could you write down the error and give it to us?

---

### Post by petrockthief on 2006-09-01
It says "mounting root file system" and then "waiting for root file system". So I take it something is wrong with my root file system. I don't know how to do either of those two things :(

---

### Post by taurus on 2006-09-01
Boot with the LiveCD, mount your /boot if you have one; otherwise, mount /.  Then, paste the content of your /boot/grub/menu.lst here with 

```
sudo fdisk -l
```

---

### Post by petrockthief on 2006-09-01
It couldn't find /boot in either directories and mounting / just said "mount failed". I don't have a Grub folder in Boot

---

### Post by taurus on 2006-09-01
> **petrockthief said:**
> It couldn't find /boot in either directories and mounting / just said "mount failed". I don't have a Grub folder in Boot

How did you partition your harddrive when you installed it?  Did you create something like /, /boot, & swap or did you have the installer partition your harddrive for you?

```
sudo fdisk /dev/hda
```

---

### Post by petrockthief on 2006-09-01
After partitioning it myself over and over I let the installer do it. I see my cdrom drives alright in /dev and then theres /hda /hda1 /hda2 and /hda5- none of them are accessibale.

---

### Post by taurus on 2006-09-01
What is the output of 

```
sudo fdisk -l /dev/hda
```

---

### Post by petrockthief on 2006-09-01
with -l nothing happens, with out the -l option, "unable to open /dev/hda"

---

### Post by taurus on 2006-09-01
Do you have an EIDE or a SATA harddrive on your machine?  For SATA, replace the /dev/hda with /dev/sda...

---

### Post by petrockthief on 2006-09-01
nope its IDE

---

### Post by taurus on 2006-09-01
What is the output of this command then?

```
dmesg | more
(hit space bar for the next 24 lines...)
```

---

### Post by petrockthief on 2006-09-01
I don't have a good way of copying that massive amount of data over... cd burner doesn't appear to be working. I could take pictures of parts though.

---

### Post by taurus on 2006-09-01
You don't have internet access with the LiveCD!  Do you see anywhere in there that says something about your harddrive?  That is the section I am interested in...

---

### Post by petrockthief on 2006-09-01
Nevermind, wasn't thinking, how do I copy terminal output to a text file?

---

### Post by taurus on 2006-09-01
I assume you run that command from a terminal right.  You can use the left button to highlight the text and use the middle (if your mouse has three buttons) or hold both buttons down (if you have only two buttons mouse) to paste it.  That's what we call cut 'n paste...

---

### Post by petrockthief on 2006-09-01
was just wondering if there was a direct to text method, anyway here it is:

[http://www.trivialcrap.com/linux/output.txt](http://www.trivialcrap.com/linux/output.txt)

---

### Post by taurus on 2006-09-01
If you don't have X running, then you can dump the output of a command into a file with

```
dmesg > output.txt
more output.txt
```
Okay, it looks like you have three partitions on your /dev/hda:  /dev/hda1, /dev/hda2, & /dev/hda5.

I guess you have your Windows on /dev/hda1, / (Ubuntu) on /dev/hda2, and swap on /dev/hda5!!!

You can mount /, /dev/hda2, from the LiveCD with

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda2 /mnt/ubuntu
df -h

```

---

### Post by petrockthief on 2006-09-01
I don't have windows or any other OS

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda2/ /mnt/ubuntu/
mount: special device /dev/hda2/ does not exist
       (a path prefix is not a directory)

---

### Post by taurus on 2006-09-01
There is something strange going on with your machine!!!  The boot message says that you have /dev/hda1, /dev/hda2, & /dev/hda5 and you can't even look/mount at them!!!

```

sudo mkdir /mnt/ubuntu
sudo mount /dev/hda1 /mnt/ubuntu

```

```

sudo fdisk /dev/hda

```

---

### Post by petrockthief on 2006-09-01
Well I did just put this computer together 8 hours ago... could there be a problem there? Everything was working except the floppy which i just scrapped. But actually the CDRom does not work when operating inside linux, only while booting.

ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
mkdir: cannot create directory `/mnt/ubuntu': File exists
ubuntu@ubuntu:~$ sudo mount /dev/hda1 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo fdisk /dev/hda

The number of cylinders for this disk is set to 9964.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

---

### Post by taurus on 2006-09-01
When you are in "fdisk /dev/hda", you can list to see if you have any partitions with l.  I believe m will give you a manu of all the commands that you can use...

---

### Post by petrockthief on 2006-09-01
when i try to cd into hda it says it doesn't exist, fdisk says unable to open. :/

---

### Post by TFX360 on 2006-09-02
> **petrockthief said:**
> when i try to cd into hda it says it doesn't exist, fdisk says unable to open. :/


Can you recheck and reconnect all cables you used in your computer?

---

### Post by petrockthief on 2006-09-03
Thank you Taurus for all your help, it was actually a kmv switch I had in the computer that was ******* up the install. So I installed without it and now it works with it, strange. Sorry I didn't recognize that earlier...

---

### Post by taurus on 2006-09-03
> **petrockthief said:**
> Thank you Taurus for all your help, it was actually a kmv switch I had in the computer that was ******* up the install. So I installed without it and now it works with it, strange. Sorry I didn't recognize that earlier...
Glad to hear that you've solved the problem with your harddrive.  Good luck and have fun.  ;)

---

