---
title: "Mounting partitions (dumb question inside)"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Cubedude04 on 2007-06-26
Hey, I am really new to linux and i don't understand how you mount a partition. I have read a few guides but i don't understand how i would mount my /home partition (i think that is what it is called). On a few different guides it gives different commands to type into the terminal and tells me different places to mount to and different partitions to mount.

So how would i mount my /home drive and where is the best place to mount it to 

Thankyou in advance :D

---

### Post by mikewhatever on 2007-06-26
The home partition mount point is specified during the installation and is /home.

---

### Post by Cubedude04 on 2007-06-26
So your saying my /home is already mounted and i will be in it if i go to places home folder?

Okay it's just i thought i had to mount it using the terminal

---

### Post by earobinson on 2007-06-26
thats correct, you can even type ```
df
``` in the terminal to see info on all your mounted partitions.

---

### Post by az on 2007-06-26
> **Cubedude04 said:**
> So your saying my /home is already mounted and i will be in it if i go to places home folder?

Okay it's just i thought i had to mount it using the terminal

/home is a folder.  There are many folders in the "/" folder and they all have differnt functions.  /boot is where the files you need to boot from a kept.  /etc is where the system configurations are kept, and so on...

Putting some of those folders on a hard disk (or a partition) of their own is sometimes a good idea.  For example, if you are using a very very old computer, the bios will not be able to boot from files that are written at the and of the disk.  Creating a boot partition at the beginning of the disk solves that problem.

On a web server, sometimes the logs can get filled and crash the system.  Logs are held in /var and so it is a good idea to put /var on a seperate partition or disk if you are running a web server and don't want someone to crash it by overfilling your logs ( by generating hundreds of erros per minute, for example.)

On a desktop system, it is not really necessary to have seperate partitions for everything.  You need a "/" filesystem on one partition and a swap partition for virtual memory.  Years ago, it was convenient to create a seperate home partition, but today, that can cause a lot more headache (by mixing configurations of different versions of applications, for example) and with disk media being so big and so cheap, it's a lot easier to just back up your data the conventional way.  Not to mention the headache of having to play around with the partition sizes (if even possible) when one partition gets full.  If everything shares the disk space, you do not have that problem.

So when you install Ubuntu, it does not create a seperate home partition for you.  The home folder is just part of what's in "/".



> **Cubedude04 said:**
> Hey, I am really new to linux and i don't understand how you mount a partition. I have read a few guides but i don't understand how i would mount my /home partition (i think that is what it is called). On a few different guides it gives different commands to type into the terminal and tells me different places to mount to and different partitions to mount.

So how would i mount my /home drive and where is the best place to mount it to 

Thankyou in advance :D

There are guides for creating a seperate home partition.  Is this what you mean?

---

### Post by Cubedude04 on 2007-06-26
I have already made my partitions when i installed the other day

/=10gb

/swap=2gb

/usr=5gb (i accidently made this one)

/home=rest of the hd about 30 gb

I was wondering how i mount the /home partition i have already made and where to mount it too

---

### Post by az on 2007-06-26
> **Cubedude04 said:**
> I have already made my partitions when i installed the other day

/=10gb

/swap=2gb

/usr=5gb (i accidently made this one)

/home=rest of the hd about 30 gb

I was wondering how i mount the /home partition i have already made and where to mount it too

Open a terminal and type:

mount

and post the output...

---

