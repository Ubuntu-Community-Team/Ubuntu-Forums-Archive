---
title: "A Couple Random Installation Questions"
date: 2007-10-08
forum: Apple PPC Users
---

### Post by Blah3 on 2007-10-08
I am new to linux (obviously) and all of the OS stuff.  I need (and want) to keep OSX but I also want to use Ubuntu.  I have had a lot of experience with iPL(iPod Linux) which allows me to boot multiple OS for the iPod.  I would like to be able to do this with my computer (of course).  I am running Ubuntu off the CD and I keep having this problem accessing the hard drive (or any other drive).  I have source of programs that I would like to build but I cant access them with the unix command prompt.  I also have many gigs of files I don't want messed with but partitioning usually erases the disk(right?)

I talk a lot so heres my questions:

  • Can someone help me dual boot with OSX and Ubuntu?

  • How can I access my hard drive (or usb drives) from Ubuntu off the CD?

  • Will Installing Ubuntu erase my data?

There are probably answers out there but I searched for a while and couldn't find it...

---

### Post by Auria on 2007-10-08
> **Blah3 said:**
> I am new to linux (obviously) and all of the OS stuff.  I need (and want) to keep OSX but I also want to use Ubuntu.  I have had a lot of experience with iPL(iPod Linux) which allows me to boot multiple OS for the iPod.  I would like to be able to do this with my computer (of course).  I am running Ubuntu off the CD and I keep having this problem accessing the hard drive (or any other drive).  [...] I also have many gigs of files I don't want messed with but partitioning usually erases the disk(right?)

I talk a lot so heres my questions:

  • Can someone help me dual boot with OSX and Ubuntu?

  • How can I access my hard drive (or usb drives) from Ubuntu off the CD?

  • Will Installing Ubuntu erase my data?

There are probably answers out there but I searched for a while and couldn't find it...

You need to disable journaling from your mac partition frist from disk utility. Then, boot from the LiveCD, choose the partitionner from the menus, shrink your mac partition, leave the remaining space empty (no partition) then run the installer. When it asks where to install, tell it to install in the largest free space.

If all goes well you will not lose any data. But, it so happens that things can go wrong :) so be sure to back up important data before starting

Accessing USB drives from ubuntu worked out-of-the-box for me. Reading your mac partition can be done by turning off journaling and keeping it off. You can also use a partition as swap space

> 
I have source of programs that I would like to build but I cant access them with the unix command prompt. 

I'm not sure what you mean, but anyway you can't expect to compile source code from a LiveCD, you'll need to install ubuntu first

---

### Post by Blah3 on 2007-10-08
Ah, I'll try the partitioning thing soon but one thing first, the word on the "street" is that when I boot up, I'll have the option of going to Ubuntu or OSX (or is that just Intel?).

---

### Post by Auria on 2007-10-08
> **Blah3 said:**
> Ah, I'll try the partitioning thing soon but one thing first, the word on the "street" is that when I boot up, I'll have the option of going to Ubuntu or OSX (or is that just Intel?).

The ubuntu installer will Yaboot, a boot loader. By default, i think it is configured to launch directly into Ubuntu. But after the install you can reconfigure it to have a boot menu. You can also choose to have a default OS and only show the choice of OS when booting with 'alt' down.

---

### Post by Blah3 on 2007-10-09
OK, "boot loader" rings a bell, I guess I'll try now.  I'll reply if it works.  
'Red leader, you have a go'

---

### Post by Blah3 on 2007-10-10
:shock: Ahhhhhhh!!!!!!!!!!! Poor my data, alas, I knew it well...
I did the shrinking and the ext2 partrition, told the installer that my hard drive was new world, and when I installed, I couldn't boot into OSX!!!!!!   Can I fix this?

Cause I am in like pain of loosing my data. :sad: :sad: :sad: :sad: :sad: :sad:

---

### Post by Auria on 2007-10-10
> **Blah3 said:**
> :shock: Ahhhhhhh!!!!!!!!!!! Poor my data, alas, I knew it well...
I did the shrinking and the ext2 partrition, told the installer that my hard drive was new world, and when I installed, I couldn't boot into OSX!!!!!!   Can I fix this?

Cause I am in like pain of loosing my data. :sad: :sad: :sad: :sad: :sad: :sad:

i don't want to sound patronizing, but i had clearly said to back up any important data first :-k

Did you tell the installer to install in free space, or did you tell it to wipe the whole hard drive?

Anyway, please elaborate on what you mean by *cannot boot OS X*
If you mean that it boots directly into Ubutnu, just hold alt down and you should see the OS X partition and be able to boot from it. If anything else, please describe a bit more

---

