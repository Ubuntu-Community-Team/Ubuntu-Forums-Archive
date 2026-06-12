---
title: "I want windows back (just temp)"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2006-10-03
I want windows back but it will not boot on startup of the computer. Does anyone know why???

<edit>
I will use windows to use vmware for linux
</edit>

---

### Post by sonny on 2006-10-03
Maybe your grub got screwed, or maybe MS doesn't want you anymore, who knows... perhaps a little bit of info would help any other member to know what is the problem.

---

### Post by think13 on 2006-10-03
Could you tell us exactly what comes up when you start up your computer?  That would help us fix your problem.

---

### Post by ProjectWhat on 2006-10-03
It just starts ubuntu regularly. My cd drive is supposed to boot up first, thats the first one on the list.

---

### Post by y6FgBn)~v on 2006-10-03
What is in the CD Drive when you boot up?

---

### Post by ProjectWhat on 2006-10-03
My windows boot up disk.

---

### Post by sonny on 2006-10-03
> **ProjectWhat said:**
> It just starts ubuntu regularly. My cd drive is supposed to boot up first, thats the first one on the list.
The problem is you can't boot the installation cd, right? Have you double check your cd drive is first to boot? Is your cd scratch sometimes scratched cd's won't boot, also you might want to check the md5sum of the cd it might be corrupted or something (happened to me with Ubuntu Dapper).

---

### Post by y6FgBn)~v on 2006-10-03
And you have double checked that the boot sequence in your CMOS shows the CD drive as first one too boot from?

---

### Post by ProjectWhat on 2006-10-03
Sonny, I sent you a PM. yes I have double checked.

<edit>
Isnt there a way to use my floppy drive to use a boot up floppy and use it to tell the cd drive to start before my os starts?
</Edit>

---

### Post by ProjectWhat on 2006-10-03
> **pcybill said:**
> And you have double checked that the boot sequence in your CMOS shows the CD drive as first one too boot from?
You said the same thing as sonny.

---

### Post by sonny on 2006-10-03
> **ProjectWhat said:**
> Sonny, I sent you a PM. yes I have double checked.

<edit>
Isnt there a way to use my floppy drive to use a boot up floppy and use it to tell the cd drive to start before my os starts?
</Edit>
Yes... just let me find the webpage...

---

### Post by sonny on 2006-10-03
> **sonny said:**
> Yes... just let me find the webpage...
That was obvious.. [http://www.bootdisk.com/](http://www.bootdisk.com/) there are boot disk for everything, good luck.

---

### Post by ProjectWhat on 2006-10-03
Which one do I need Im confused. I seen something that they cost 4 bucks. I know that not alot but really...

---

### Post by b_martinez on 2006-10-03
Go here;
[http://www.bootdisk.com/](http://www.bootdisk.com/)
and get the Wi XP boot disk. It SHOULD boot your windows for you. If that doesn't work, you may be able to d/l a win 98 bootdisk, and use it to start the XP install disk. Make sure that you have cd suport checked. The boot messages for the floppy will let you know the drive letter for the cd. Then type in the command 
E:\setup
It should look like this on your screen
A:\ E:\setup
The reason for thisis that you are in the A:\ drive and are switching to the E:\ drive (if that is your cd's drive letter. It may be F:\ if you have 2 hard drives. 
hth 
Bill

---

### Post by ProjectWhat on 2006-10-03
My cd burner doesnt work though. I cant figure out the problem.  When I try to open it it says:
mount: no medium found
mount: no medium found
error: could not execute pmount

hmmmm.

---

### Post by imaginos on 2006-10-03
One little warning, I suppose you know, but just in case.
Reinstalling Win will rewrite youor MBR, so it won't load GRUB (but ntldr). Ofcourse, you can install GRUB afterwards, or chainload from ntldr to GRUB.. 

Anyway, this is just a reminder.. :)

---

### Post by mongooseman1128 on 2006-10-03
if you read what I posted before, disregard, martinez is right. That's exactly what you need to do

---

