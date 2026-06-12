---
title: "fsck error"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by IsKall on 2007-05-27
Every time I start ubuntu the fsck check start (/dev/sda1)  and when it comes to over 60 % the it says:

Duplicate or bad block in use!

and then

/dev/sda1: Multiply-claimed block(s) in inodes xxxxxxxxx: xxxxxxxxxxx and so on

I have searched on the forum but no one had the same problem as me, and I am using Feisty.

Anyone who can help me? Today would be great, because I need to be finished with a projekt tomorrow.

---

### Post by drs305 on 2007-05-27
HymnToLife said my response was a bad idea so I have edited this post so others won't read it and get possibly poor advice.

---

### Post by Bachstelze on 2007-05-27
This is a *very* bad idea. If fsck throws an error, it's for a reason !

Instead of just ignoring the problem, it's better to fix it. Just fire up a Live CD and run fsck on your partition.

---

### Post by IsKall on 2007-05-27
ok will try that

---

### Post by IsKall on 2007-05-27
What is the password for root in live cd?

---

### Post by jbinto on 2007-05-27
There is no password for root (it is randomly generated).

Try "sudo su".

---

### Post by Lucifiel on 2007-05-27
If I were you, try and install smartmontools on the livecd.

Then, try this line:

sudo smartctl -d ata -a /dev/sda

where sda = your hard disk . 

An example of a log with plenty of errors would be something like this:

---

### Post by IsKall on 2007-05-27
well thats to late now :/

I tried fsck on live cd and typed "yes" for fix-questions, but now everything is "gone" my home catalog moved to  /usr/share/icons/gnome/24x24/status/weather-showers-scattered.png

very wierd but now I dont have time to fix this I am gonna make a backup of all things I have and make a clean install again, but how do I copy that catalog? It says Operation not permitted. 

when I do this I " cp -afr weather-showers-scattered.png/    /media/My\ Book/Backup/Linux/Unsorted/"

I get this :

```

cp: failed to preserve ownership for `/media/My Book/Backup/Linux/Unsorted/weather-showers-scattered.png/.icons/nuoveXT-1.6/48x48/apps/synaptic.png': Operation not permitted

```

anyone who can tell me the right command to move those files? I am logged as root too.

---

### Post by Lucifiel on 2007-05-27
> **IsKall said:**
> well thats to late now :/

I tried fsck on live cd and typed "yes" for fix-questions, but now everything is "gone" my home catalog moved to  /usr/share/icons/gnome/24x24/status/weather-showers-scattered.png

very wierd but now I dont have time to fix this I am gonna make a backup of all things I have and make a clean install again, but how do I copy that catalog? It says Operation not permitted. 

when I do this I " cp -afr weather-showers-scattered.png/    /media/My\ Book/Backup/Linux/Unsorted/"

I get this :

```

cp: failed to preserve ownership for `/media/My Book/Backup/Linux/Unsorted/weather-showers-scattered.png/.icons/nuoveXT-1.6/48x48/apps/synaptic.png': Operation not permitted

```

anyone who can tell me the right command to move those files? I am logged as root too.

Okay, try sudo cp . And trust me, try and run smartmontools 'cos if your hard disk is dying, you can then print out the log as proof when you RMA it.

---

### Post by IsKall on 2007-05-27
ok, I will do it when I have copied all of my stuff to the external :/ really cant loose those them, cant lots of school stuff saved.

---

### Post by IsKall on 2007-05-27
whats RMA btw?

---

### Post by Lucifiel on 2007-05-27
> **IsKall said:**
> whats RMA btw?

Oh did you assemble this pc yourself or is it from a Vendor like Dell, etc.?

Either way, you can print out the log and show it to them. :p 

RMA:

[http://en.wikipedia.org/wiki/Return_Merchandise_Authorization](http://en.wikipedia.org/wiki/Return_Merchandise_Authorization)

---

### Post by IsKall on 2007-05-27
It is an Acer-laptop :)

btw, the cp thing did not work it is complainin about the same thing

---

### Post by Lucifiel on 2007-05-27
> **IsKall said:**
> It is an Acer-laptop :)

btw, the cp thing did not work it is complainin about the same thing

Hmmm...
then try this.

sudo mkdir /media/chicken (or whatever name you wanna give your partition)

mount /dev/sda# /media/chicken

Where sda# = your partition. 

Then use, gksudo nautilus to browse the folder.

Alt + F2: gksudo nautilus /media/chicken 

Then, do the same for all other partitions you want to be able to access.

---

### Post by IsKall on 2007-05-27
okey, will try that!

BTW: thx for all help you have giving me so far :)

---

