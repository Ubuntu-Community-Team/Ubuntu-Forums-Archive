---
title: "Partition Setup."
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by miguel1986 on 2007-06-22
Can anyone, please, explain me the whole process of partition using Ubuntu LiveCD?
I'd be very, very grateful.

---

### Post by Jose Catre-Vandis on 2007-06-22
To a certain extent it is going to depend on what you are trying to do. You basically have two choices, wipe the whole drive and install ubuntu all over it, or select a pre existing partition or unallocated space to install into (you will want to do this if you are dual booting!). If you do the latter you need to set the partition as your root (/). Ubuntu will automatically generate a swap parition if you do not already have one. After these basics, you have so many options about creating partitions for /home and doing all sorts of other things, but to start off with it is best to keep things simple. i usually use the alternate cd so its been a while since I installed from live...

Perhaps others who retain more knowledge on this subject can expand.......

---

### Post by Crafty Kisses on 2007-06-22
> **miguel1986 said:**
> Can anyone, please, explain me the whole process of partition using Ubuntu LiveCD?
I'd be very, very grateful.

It's pretty simple, you click the "install" icon, and then after that follow the instructions, then choose how much HDD space you want dedicated to Ubuntu. 

This link may help you a lot: 
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by miguel1986 on 2007-06-22
Jose Catris-Vandis, my friend, and if the swap partition don't be created by itself.
What is reifersfs (not sure if it's spelled rightly)?

I mean, I need a very detailed explanation, please.
I'm new to it.

---

### Post by miguel1986 on 2007-06-22
By the way, I am dual booting. One of my partitions include the Windows XP, which I do not intend to format. I have other partitions, so it's hda1 (Windows XP) and hda5. I want to install Ubuntu into hda5 and create, from the hda5, another partition to the swap.

How can I achieve these things?

---

### Post by antoz on 2007-06-22
Using the live Cd open the gnome partition editor right click on hda5 then resize to make room for your swap partition you won't need much about 1.5 times your RAM. Then rightclick the empty space and create your swap. Depending on which live cd you are using you may have to unmount hda5 first
had5 format "ext3", swap partition format "swap"
Once you install ubuntu make sure[COLOR="Red"]** only these 2 partitions**[/COLOR] are checked to format, "/"  and "swap"

---

