---
title: "Installing a new Ubuntu...how?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by R6V2 on 2008-04-11
Well, I want to be ready so that when the Hardy release comes out, I can already know how to do it. I am tring to over-write my old Ubuntu version after loading into the cd. I have already tried this, but when I select 'Manual' from the partition area (in the installer) It shows a bunch of partitions. I choose the checkbox beside the 'ext3' one, because that's linux. But, when I click forward it says I havn't choosen a root!?!??! So, needless to say, I want my computer back the way it was before I installed Ubuntu. So that I can have a clean install again. I need some tips on this! I want to have my Ubuntu parition, and everything having to do with Linux, gone! So next time I install I can just use: Use largest continous free space. :) Thanks!

---

### Post by schauerlich on 2008-04-11
I'm not sure what you're asking here - Do you want help reinstalling Windows, or do you just want to know how to install Hardy? It's pretty easy to just overwrite the old Ubuntu partition and put the new system over it.

---

### Post by PurposeOfReason on 2008-04-11
You can do manual and the one you clicked format for is listed as /media/something. Change that to just / for root. Of course you could just let Ubuntu update so that it saves you partitioning problems.

---

### Post by bt224 on 2008-04-11
The partition manager will only work if you boot from the LiveCD and use the tool from there. It's because you are not mounting your hard drive that way. Found this out the hard way myself. Ugh.

---

### Post by R6V2 on 2008-04-11
Well, A little more information. I want to install Hardy soon, and I want to know a simple way to over-write the old ubuntu partition with the new hardy version. Like I said, when I check the ext3 partition it says it's not a root. So...

---

### Post by PurposeOfReason on 2008-04-11
> **R6V2 said:**
> Well, A little more information. I want to install Hardy soon, and I want to know a simple way to over-write the old ubuntu partition with the new hardy version. Like I said, when I check the ext3 partition it says it's not a root. So...

Read what I posted. It isn't root as it is said to be under /media/sda#, change it to be root (/)

---

### Post by R6V2 on 2008-04-11
What!!? That'll remove my windows partition, and my Linux One!!

---

### Post by PurposeOfReason on 2008-04-11
> **R6V2 said:**
> What? That'll remove my windows partition!
What? Maybe I'm understanding wrong. You put in a live cd and install. You're trying to override a current install so when you get to the partitioning screen you go to manual. There is an ext3 partition that is your current ubuntu install. You want that overrode, so you choose format. It complains about not being the root partition because you choose format and you left the mountpoint to something like /media/sda2. You need to change that to just / so that it is formatted to root.

---

### Post by zvacet on 2008-04-11
```
gedit /etc/fstab
```

There you will see which partition is root and install new version over it.

---

### Post by R6V2 on 2008-04-11
> **PurposeOfReason said:**
> What? Maybe I'm understanding wrong. You put in a live cd and install. You're trying to override a current install so when you get to the partitioning screen you go to manual. There is an ext3 partition that is your current ubuntu install. You want that overrode, so you choose format. It complains about not being the root partition because you choose format and you left the mountpoint to something like /media/sda2. You need to change that to just / so that it is formatted to root.
I think im stupid. I still don't get what you mean, when I click the checkbox beside the ubuntu partition, it gives me that error. I'm supposted to change the ubuntu name to "/" ?

---

### Post by PurposeOfReason on 2008-04-11
> **R6V2 said:**
> I think im stupid. I still don't get what you mean, when I click the checkbox beside the ubuntu partition, it gives me that error. I'm supposted to change the ubuntu name to "/" ?
Do what the above poster said but use cat and not gedit as it's better practice. Look for what partition is mounted as /. That is the one that will be listed as /media/sda#. Change that to /.

---

### Post by R6V2 on 2008-04-11
Check Out The Picture Below.

---

### Post by PurposeOfReason on 2008-04-11
> **R6V2 said:**
> Check Out The Picture Below.

/media/hda3 should be changed to /

Read the message at the bottom. :)

---

### Post by R6V2 on 2008-04-11
So, now im just testing this with the hardy 8.04 beta. So far it's working I chanegd the linux partition to /, and now it's installing :)

---

