---
title: "Ubuntu problems."
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Jaack on 2008-04-12
Hi,
I have recently downloaded Ubuntu 7.10 on my laptop and tried Ubuntu out, it is great but it won't let me setup a wireless internet connection which isn't any good for me. I have previously tried to fix the problem but without succes. I have partitioned my hard drive, windows vista and Ubuntu 7.10 and when i turn on my laptop Grub 1.5 loads up so that I can choose the OS I would like to use and as I only use Vista because I don't have any internet on Ubuntu I wan't to get rid of it because i need as much space as i can get. I have tried just deleting Ubuntu but then when i boot up Grub 1.5 wont load and it says grub loading error so i have to reinstall Ubuntu and i can't seem to find any way to remove Ubuntu and Grub. Can anyone help me?

Thanks, Jack

---

### Post by PriceChild on 2008-04-12
[http://support.microsoft.com/kb/315224/en-us](http://support.microsoft.com/kb/315224/en-us)

Choose "if linux is not installed"

---

### Post by stalkingwolf on 2008-04-12
If you are dead set on getting rid of Ubuntu you can format that drive.  Put in your windows
recovery disk , go to the repair mode and type FIX MBR. ( I think thats right) that will remove grub.

With more details on your wireless problem we might be able to help fix it.

---

### Post by bred on 2008-04-12
> **Jaack said:**
> Hi,
I have recently downloaded Ubuntu 7.10 on my laptop and tried Ubuntu out, it is great but it won't let me setup a wireless internet connection which isn't any good for me. I have previously tried to fix the problem but without succes. I have partitioned my hard drive, windows vista and Ubuntu 7.10 and when i turn on my laptop Grub 1.5 loads up so that I can choose the OS I would like to use and as I only use Vista because I don't have any internet on Ubuntu I wan't to get rid of it because i need as much space as i can get. I have tried just deleting Ubuntu but then when i boot up Grub 1.5 wont load and it says grub loading error so i have to reinstall Ubuntu and i can't seem to find any way to remove Ubuntu and Grub. Can anyone help me?

Thanks, Jack

[COLOR="Teal"]what kind of wireless card do you use?
try to boot from LiveCD and look if you have access from live cd to your wireless network?
it always happens to me - when I don't have wifi, I just 'show' to OS my wireless from LiveCD then it works fine... hope it help
it depends,what you want to do now - go back to Gates or to fix your wifi on ubuntu :)[/COLOR]

---

### Post by Jaack on 2008-04-13
On my laptop it says broadcom wireless and that is as much as i know, if its not that then how would i check what it is?

Thanks for all the replies.

---

### Post by seshomaru samma on 2008-04-13
If you are running from a Live CD issue this command:
```
lspci -v | less
```
it will tell you waht kind of wireless chipset you got

In Windows you can go to the Device Manger . It should be in the "my computer" properties dialogue , but I can't remember where they put it in vista

Many people have gotten their broadcom wireless working in Ubuntu 
You can search the forum for solution for your specific card , you can also post a thread here titled something like "need help with Broadcom Wireless model so and so..."

---

### Post by chrisdugdale on 2008-04-15
Use Partition Magic from Windows to remove the Ubuntu partitions. I'm not sure if you can still get it free? Make sure you backup all your data in both Windows and Ubuntu before you play with partitions. A free partitioner is at [www.soft32.com/Download/free-trial/Partition_Magic/4-151-1.html](www.soft32.com/Download/free-trial/Partition_Magic/4-151-1.html) but I haven't checked or tested it. I'd encourage you to continue to try to work out Ubuntu, it's got the lot, just confusing at first, but had no wireless problems myself. New version out in 8 days.

---

