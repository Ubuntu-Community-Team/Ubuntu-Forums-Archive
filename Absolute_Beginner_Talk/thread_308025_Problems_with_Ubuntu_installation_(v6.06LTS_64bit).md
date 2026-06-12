---
title: "Problems with Ubuntu installation (v6.06LTS 64bit)"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Sparkl on 2006-11-27
So, what I can say is - HELP MEEE!

The problem is next - when I try to install Ubuntu, I normally boot the cd, and then I click at the first option of the menu. This is install Ubuntu. I've got an AMD Athlon 64, so I got myself a copy of Linux Ubuntu for 64bit processors.

Well, when the setup starts to install Ubuntu, it passes the first step of installation and then it says that: Failed to start the X server (your graphical interface). It is likely, that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

And then it disables me that function, but after that, I cannot proceed with furder installation.

Can please anybody help me? Cos I don't even know, what this X server is anyway...](*,)

---

### Post by diepruis on 2006-11-27
I'm assuming you get a command line after the error? If you do, could you try to copy /etc/X11/xorg.conf and paste it here. Also, please post what graphics card your PC is using.

---

### Post by cilynx on 2006-11-27
I would seriously advise that you get yourself a copy of the 32-bit install.  The 32-bit version will work just fine on your AMD64, just not quite as fast as the 64-bit version would.  Many things don't work right out of the box yet on 64-bit.  These include graphics drivers, flash players, networking drivers, video codecs, many other things.  Personally, I run Ubuntu64, but I've been using Linux for over 10 years.  I've run Ubuntu32 on a couple of 64-bit machines in the past simply to avoid all of the annoying things that don't like to work.

---

### Post by Sparkl on 2006-11-27
OK. I'm using ATI Radeon X800RX (Club 3d) 256mb...

---

### Post by diepruis on 2006-11-27
> **Sparkl said:**
> OK. I'm using ATI Radeon X800RX (Club 3d) 256mb...

First off, let me say that cilynx has a point. The 64bit version isn't *quite* ready yet.

I really do need to know what is contained in that file I asked you about, otherwise I cannot diagnose your problem.

---

### Post by Sparkl on 2006-11-27
Where do I use this command? You know, I'm quite a big "noob" with Linux... I need some more explanation...

I'm on the other computer, the one, on which is Linux going to be is without OS...

---

### Post by diepruis on 2006-11-27
> **Sparkl said:**
> Where do I use this command?

I'm on the other computer, the one, on which is Linux going to be is without OS...

When you boot up the one with Linux on it, does it offer you a command prompt after you received the error message? It should look something like this:

```

sparkl@sparkl-desktop:~$

```

It will also be helpful if you answered yes to the question of whether you'd like to see the output and posted that as well.

---

### Post by duality on 2006-11-27
You need to install the graphics drivers: 
for ATI
sudo apt-get install xorg-driver-fglrx
then: 
sudo aticonfig --initial
and reboot

---

### Post by Sparkl on 2006-11-27
The situation is next: When this error message shows it throws me in command prompt, but it shows me this text: ubuntu@ubuntu:~$, and no desktop in it. What do I do next?

---

### Post by diepruis on 2006-11-27
> **Sparkl said:**
> The situation is next: When this error message shows it throws me in command prompt, but it shows me this text: ubuntu@ubuntu:~$, and no desktop in it. What do I do next?

Try typing the commands that **duality** gave first. If that works, great. If it doesn't: do you have a flash drive or some such on you?

---

### Post by Sparkl on 2006-11-27
The first command that Duality gave me is working, but the second doesn't. So I tried to reboot the computer, but the problem is still not removed.

And with the flash disc: do you mean USB? If so I have few pairs...  The biggest is 512mb. Is that going to be ok?

I also must tell you, that I don't have any partitions on the disk, because I can't make it to the formator... Is that the problem maybe?

---

### Post by diepruis on 2006-11-27
Yes one of those sticks will be enough. :)

What error did duality's command give you?

---

### Post by Sparkl on 2006-11-27
The command, that does not work is: sudo aticonfig --initial.
And it says, that command is not found...

So, what do I do with the stick now?

---

### Post by diepruis on 2006-11-27
Could you first do the following?

Type "mount" on the command-line. Tell me if you see **anything** like /dev/sda1 or /dev/sdb1. I don't care about /dev/hda and such, only the sda/b/c things.

---

### Post by Sparkl on 2006-11-27
> **diepruis said:**
> Could you first do the following?

Type "mount" on the command-line. Tell me if you see **anything** like /dev/sda1 or /dev/sdb1. I don't care about /dev/hda and such, only the sda/b/c things.

No. Those commands are not shown at my computer. Well, the first part of the command "/dev" is shown, but it doesn't match to any command you wrote...

---

### Post by diepruis on 2006-11-27
You only need to type this at the command prompt:

```

mount

```

And check if it returns anything resembling what I asked, and if so, what.

---

### Post by Sparkl on 2006-11-27
Yes yes, i know that...

Here I'm going to post all commands, that command prompt "throws" me out:

ubuntu@ubuntu:~$ mount
unionfs on / type unionfs (rw)
proc on /proc type proc (rw)
/sys on / sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-amd64-generic/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuite,nodev)

---

### Post by diepruis on 2006-11-27
Okay, please try the following:

Insert the USB drive, then:

```

cd /mnt
sudo mkdir usb
sudo mount /dev/sda1 usb
cp /etc/X11/xorg.conf usb/
sudo umount /dev/sda1

```

Remove the drive, insert into the working PC and post the file "xorg.conf" that should now be on it.

---

### Post by Sparkl on 2006-11-27
hmmm... There's one really big problem...

Half of commands I wrote in the command prompt are not existable... For some of commands it says, that file exist, but cannot create directory... and for some files, that they don't exist...or that special device does not exist...:-k :-k 

I really don't know what to do...:-k :-k :-k

---

### Post by diepruis on 2006-11-27
That's really odd. I have one last command for you to try and if that doesn't work I can't help you.

```

sudo dpkg-reconfigure xserver-xorg

```

Select "No" at the first prompt, and "vesa" at the second one. Go through the other options, selecting the values that are correct. The defaults should be fine in most cases.

Reboot.

---

### Post by cilynx on 2006-11-27
Can you give us the output of the first command in that group that didn't work?

---

### Post by Sparkl on 2006-11-27
It was sudo mkdir usb... And than every command from then on does not work...

---

### Post by diepruis on 2006-11-27
> **Sparkl said:**
> It was sudo mkdir usb... And than every command from then on does not work...

What was the error message?

---

### Post by Sparkl on 2006-11-27
mkdir: cannot create directory 'usb' : File exists

---

### Post by diepruis on 2006-11-27
> **Sparkl said:**
> mkdir: cannot create directory 'usb' : File exists

What was the error given by the command right after that one?

---

### Post by Sparkl on 2006-11-27
mount: special device /dev/sda1 does not exist

---

### Post by diepruis on 2006-11-27
> **Sparkl said:**
> mount: special device /dev/sda1 does not exist

Mmmm... sounds like the USB stick isn't being recognised. Is it plugged in? If it isn't, could you try the other one and do the whole process from the start? If that doesn't work, could you please post the output of
```
dmesg | tail
```

---

### Post by Sparkl on 2006-11-27
[2906.416626] sdb: Mode sense: 0b 00 00 08
[2906.416628] sdb: Assuming drive cache: write through
[2906.426062] SCSI device sdb: 1001472 512-bytes hdwr sectors (513mb)
[2906.427172] sdb: Write protect is off
[2906.427175] sdb: Mode Sense: 00 00 08
[2906.427177] sdb: Assuming drive cache: write through
[2906.428690] sdb: sdb1
[2906.429365] sd 11:0:0:0: Attached scsci removable disc sdb
[2906.429402] sd 11:0:0:0: Attached scsci generic sg1 type 0 
[2906.430181] usb-storage: device scan complete

---

### Post by diepruis on 2006-11-28
Okay, can you try the following:

Insert the USB drive, then:

```

cd /mnt
sudo mkdir usb
sudo mount /dev/sdb1 usb
cp /etc/X11/xorg.conf usb/
sudo umount /dev/sda1

```

Remove the drive, insert into the working PC and post the file "xorg.conf" that should now be on it.

---

