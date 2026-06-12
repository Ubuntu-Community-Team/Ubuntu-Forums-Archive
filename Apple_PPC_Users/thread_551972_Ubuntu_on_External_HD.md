---
title: "Ubuntu on External HD"
date: 2007-09-15
forum: Apple PPC Users
---

### Post by Jon Walker on 2007-09-15
I have a 500gb external HD that I want to put linux on and boot it onto my Ibook g4 via USB boot. How do I make this happen? Is it even possible to run it through the harddrive?

---

### Post by Jon Walker on 2007-09-16
I have been reading around and from what I gathered I had to partition my HD so I did.

200gb fat32

300 gb ext3

Now how the heck to I get linux installed on the ext3 part of my harddrive?

Any help would be greatly appreciated.

---

### Post by pxwpxw on 2007-09-16
Do you have a firewire option? it is easier.

---

### Post by Jon Walker on 2007-09-16
My hard drive and laptops both support firewire, but I have no idea if I can boot from USB or firewire.

---

### Post by pxwpxw on 2007-09-16
> **Jon Walker said:**
> My hard drive and laptops both support firewire, but I have no idea if I can boot from USB or firewire.

iBookG4 can boot external firewire hard disk linux, from an external boot partition or from a boot partiton on the intenal hard disk (much better option). It can also boot an external hdd usb system, but only from a boot partiton (or a macosx partition possibly)  on the internal. Firewire is faster and best.
  
Need to use  the "alternate install cd " or iso to install, not the live cd, with some extra manual stufff to do to fix up the booting, but either way should get ubuntu installed on the external.

 I should warn you that it  needs a bit of command line stuff and optimism. 
There is more to it, but what are your options on the internal drive there?

---

### Post by Jon Walker on 2007-09-16
My internal harddrive is a 60gb with about 20gb free. That is why I want to run linux on my external which has a 280 gb partition setup for linux. I will try to get the alternate cd installed on my external HD. Terminal doesn't scare me as much as it used to, I have been using Ubuntu for 4 months now, just not on my laptop. How to I boot it in firewire?

---

### Post by Jon Walker on 2007-09-16
running from external is my only practical option as I have 100gb of music/video/photos that I will be using/editing. My laptop internal does not have the room. 

Just so I don't waste my time, if I run it from my external hd, I will be able to use and store files on it without using the internal HD memory up?

---

### Post by Jon Walker on 2007-09-16
I just had an idea, can I make a firewire bootable external harddrive with my tiger os dvd? 

If I can do that I will make the hard drive tiger bootable and put a linux partition in it afterwords... Does this work? Or is it one or the other? 

If it is one or the other I can always find 15 gb on the internal for linux...

---

### Post by pxwpxw on 2007-09-16
> **Jon Walker said:**
> running from external is my only practical option as I have 100gb of music/video/photos that I will be using/editing. My laptop internal does not have the room. 

Just so I don't waste my time, if I run it from my external hd, I will be able to use and store files on it without using the internal HD memory up?

You don't need the internal hd for ubuntu except maybe 30MBytes max for booting, but the partitioning for the external is important, depending whether macosx and/or ubuntu and/or others will use them -  fat32 is a good choice for linux/macosx sharing.
Do you need all that space for ubuntu? 10GB will get a good system up, and free space can be left for later decisions. 

It will be a good idea to start by getting the existing partition listings types and sizes  for both disks and some other data, before going any further (from macosx). My comments so far are without knowing exactly what you have there . When the external firewire ubuntu installation and booting is complete, it runs quite separately from macosx, but initiallly we can use macosx to help with get set up.

If you have not tried it yet you should try the firewire connection to the external in macosx now.

Do not try to install ubuntu before I give you more information.

Posts overlapped.

---

### Post by pxwpxw on 2007-09-16
> **Jon Walker said:**
> I just had an idea, can I make a firewire bootable external harddrive with my tiger os dvd? 

If I can do that I will make the hard drive tiger bootable and put a linux partition in it afterwords... Does this work? Or is it one or the other? 

If it is one or the other** I can always find 15 gb on the internal for linux**...

That 15GB is  the easiest way to go, and can always install on the external later, but all depends on keeping the partitoning options open, by gettiing it right at the start - needs more thought.

---

### Post by Jon Walker on 2007-09-28
I have been booting my ibook with tiger OSX from my 500gb harddrive and liked it sooo much that I htought... I should boot from external with linux, so I bought a 750gb external, and I am putting linux on it right now. I am stoked! Now I have a 500gb tiger or 750 gb linux system!! This greatly enables my ability to edit RAW files and store them with my laptop.

Technology is great when you finally understand how to work it :) Thanks.:KS

---

