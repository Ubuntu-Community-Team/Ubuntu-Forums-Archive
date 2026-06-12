---
title: "libesd.so.0"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by rishi.lalseta on 2006-08-15
Hello 

I am using a ubuntu 5.10

I had accidentally typed 
ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1 and after doing this i restarted the machine.

While restarting it came to a point where it asks me for username and password which i jotted in.

But there was a error which said 
your xsession doesn't login and comes with this message

"THE GREETER APPLICATION APPEARS TO BE CRASHING"
"ATTENPTING TO USE DIFFERENT ONE"

when i click on OK it just keeps on with the same message.

Could someone please help

Thanks

---

### Post by fakie_flip on 2006-08-15
Follow the directions from [here]("http://gentoo-wiki.com/TIP_Booting_into_single_user_mode") to boot your computer into single user mode. Single user mode will give you root only, and a command line. It's similar to a Window's safe mode in some ways. Be careful what you do in single user mode because you will be root when you do that, and typing something like this "rm -rf /" could really do a lot of damage. Once you are in single user mode, and you have a prompt, you will need to type this command.
```
rm -f /usr/lib/libesd.so.1
```
For some reason you can't go into single user mode such as someone has locked you out of the bootloader with a password, then you will need to get any Linux live cd such as Knoppix or the Ubuntu 6.10 cd, and you can still get single user mode from the cd. You need to mount your partition with the the bad symbolic link, so that you can delete it. I am assuming your root partition is the device /dev/hda1. You can find out what yours is with this command. 
```
sudo fdisk -l
```
If you have windows installed, you are likely to have something else besides hda1 for your Linux root partition. To mount your the partition with the bad symbolic link, give this command on the live cd.
```
mkdir ~/Desktop/a;sudo mount -t ext3 /dev/hda1 ~/Desktop/a
```
Next, to get rid of the bad symbolic link, do this.
```
sudo rm -f /usr/lib/libesd.so.1
```
Do not worry if you do not have the root password. None of the things I told you to do require the root password. Let me know if this solves your problem.

---

### Post by fakie_flip on 2006-08-15
Tell me if that helps you.

---

