---
title: "[SOLVED] Swap space"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2007-06-23
Hi All

I have heard some users mention that we could try to increase the size of the swap space; I have 2 questions on this one(I'm still a bit of a noob).
1. What does this do for me?
2. How do  I accomplish this task?

Any help will be appreciated.

Thanx

Xoanan:popcorn:

---

### Post by apjone on 2007-06-23
Swap space is basically an extension os RAM which is stored on your hard disk. Nowadays with the amount of ram computers have you should not really need swap. But it is good to put it in just incase.

---

### Post by raja on 2007-06-23
> **Xoanan said:**
> Hi All

I have heard some users mention that we could try to increase the size of the swap space; I have 2 questions on this one(I'm still a bit of a noob).
1. What does this do for me?
2. How do  I accomplish this task?

Any help will be appreciated.

Thanx

Xoanan:popcorn:

How much RAM and how much swap do you have now?

---

### Post by stevebakerj on 2007-06-23
I run 3G RAM and 512K SWAP, works well for me

---

### Post by Xoanan on 2007-06-23
Thanx for all the replies

I know I have at least 128 Megs of RAM.  I put another card in to increase it to 256 but I cant verify that it is working properly or not.  THe only noticable difference I see is that the Dell Screen doesn't pop up on boot time anymore. 

I am not sure how much swap space I have

BTW, Steve, which episode does that Doctor Who quote come from?:popcorn:

---

### Post by stevebakerj on 2007-06-23
In Kubuntu:

System
Infocentre

It will tell you about both RAM and /SWAP.  How much you've got/using and how much is free

Dr Who quote - Tom Baker Meglos

---

### Post by bodhi.zazen on 2007-06-23
In a terminal enter :

```
free -m
``` That will show us ram and swap info

In general, size of swap is RAMx2, max 1 Gb

If you use hibernation , then swap = RAM

The more ram you have the less you need swap.

---

### Post by Xoanan on 2007-06-23
> **stevebakerj said:**
> In Kubuntu:

System
Infocentre

It will tell you about both RAM and /SWAP.  How much you've got/using and how much is free

Dr Who quote - Tom Baker Meglos


Cool!  I need to update my DVDs on that at some point

Thanx for the help:popcorn:

---

### Post by Xoanan on 2007-06-23
> **bodhi.zazen said:**
> In a terminal enter :

```
free -m
``` That will show us ram and swap info

In general, size of swap is RAMx2, max 1 Gb

If you use hibernation , then swap = RAM

The more ram you have the less you need swap.

Thanx for the help;  

When I get back home, I will check those and get back with you.

How do I change the amount of Swap space I use?

---

### Post by bodhi.zazen on 2007-06-23
Well, swap is it's own partition, so,

either :

[list=number][*]boot to a live CD and use gparted to resize swap


[*]or make a swap file and update fstab. [/list]

I vote for #1

To use a swap file : [http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html)

Scroll down to the swapfile information (hint : use dd then swapon)

---

### Post by Xoanan on 2007-06-23
Thanx;  I will post some results later on...

---

### Post by Xoanan on 2007-06-23
Hi All

I found this while surfing the user docs.  
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

Could that work?  
BTW, I read the word "gedit" which I believe refers to Gnome, which I am not using. 
Is there an XFCE alternate?

---

### Post by bodhi.zazen on 2007-06-23
Yes that will work, That is a swapfile.

I think the editor in xfce is mousepad

You can use nano (in a terminal) too.

gksudo mousepad ...

sudo -B nano ...

The -B flag makes a backup :)

The "problem" with a swap file is you swap partition will take up space on the hard drive if unused ...

---

### Post by Xoanan on 2007-06-23
> **bodhi.zazen said:**
> Yes that will work, That is a swapfile.

I think the editor in xfce is mousepad

You can use nano (in a terminal) too.

gksudo mousepad ...

sudo -B nano ...

The -B flag makes a backup :)

The "problem" with a swap file is you swap partition will take up space on the hard drive if unused ...


Thats okay;  I have space on the harddrive;  I erased the old OS that was on this one in favor of Xubuntu.  The old one was Win ME. blech

---

### Post by Xoanan on 2007-06-23
results of free -m

  ____________total _____ used__free___shared___buffers     cached
Mem:_______ 138______ 136 ___  2_____ 0________ 1_____________ 39
-/+ buffers/cache: _____94_____ 44
Swap:_______ 352_______ 49_____303

If I am reading that correctly, that chip I inserted only increased the amount of RAM by 10MB.  I could be misinterpreting that though.

Had a little trouble with copy/paste; sorry

---

### Post by Dennis the Menace on 2007-06-23
> **Xoanan said:**
> Thanx for all the replies

I know I have at least 128 Megs of RAM.  I put another card in to increase it to 256 but I cant verify that it is working properly or not.  THe only noticable difference I see is that the Dell Screen doesn't pop up on boot time anymore. 

I am not sure how much swap space I have

BTW, Steve, which episode does that Doctor Who quote come from?:popcorn:

When I put extra ram in my Dell dimension, after powering it up for the first time it beeped and told me that the amount of memory had changed.
I don't know if they're all the same.

---

### Post by Xoanan on 2007-06-23
Mine didn't tell me anything at all.  I once took out the extra RAM and it told me it detected a decrease in memory.

It would appear that the RAM is being used quite a bit and the SWAP not as much.  I wonder if there is a work around for this?

---

### Post by bodhi.zazen on 2007-06-23
> **Xoanan said:**
> Mine didn't tell me anything at all.  I once took out the extra RAM and it told me it detected a decrease in memory.

It would appear that the RAM is being used quite a bit and the SWAP not as much.  I wonder if there is a work around for this?

Actually you want to use RAM >> swap.

How much ram can our motherboard use ?

---

### Post by Xoanan on 2007-06-24
It is upgradable to 512;  That card I put in should have increased it to 384 MB but evidently that is not the case.  Perhaps it is because it is not a Dell Proprietary Card.

---

### Post by Xoanan on 2007-06-25
I took out that other mem stick and noticed no difference in performance

---

### Post by bodhi.zazen on 2007-06-25
> **Xoanan said:**
> I took out that other mem stick and noticed no difference in performance

Sounds like your are limited by your hardware in terms of the RAM upgrade.

Sometimes motherboards are funny that way, at lease I had this kind of problem. I am no expert in hardware, perhaps someone else will chime in ... Otherwise, see if the manufacturer can be of assistance.

---

### Post by Xoanan on 2007-06-26
Well, it is upgradable to 512 Megs, but you have to have a compatible card, not just a PC133 that will fit evidently.  After taking it out, the Dell screen pops up during the boot and so does the Xubuntu mouse, denoting that the OS is loading.  I will probably get the new stick from Memory 10 or something.

Even so, there is still a lot of things you can do with Xubuntu even with only 128 MB of RAM

---

### Post by Xoanan on 2007-06-30
BTW, did I interpret those readings I gave correctly?  2 MB free?

---

### Post by bodhi.zazen on 2007-06-30
The second line, buffers is better so 44

1. LInux uses ram different then windows, so the linux saying if free ram is wasted ram ;)

2. When you run out of ram you use swap. Since swap is on the hd it is slower, so a ram upgrade should give you a (small) boost in performance.

---

### Post by The Seeker on 2007-06-30
Just out of interest, is anyone aware as to why Ubuntu creates such a huge swap space (2933MB) as default?

---

### Post by Xoanan on 2007-06-30
> **bodhi.zazen said:**
> The second line, buffers is better so 44

1. LInux uses ram different then windows, so the linux saying if free ram is wasted ram ;)

2. When you run out of ram you use swap. Since swap is on the hd it is slower, so a ram upgrade should give you a (small) boost in performance.
Ah hah!

That would explain a few things; 
So it reserves ram in the buffers then.  Gothcha!

---

