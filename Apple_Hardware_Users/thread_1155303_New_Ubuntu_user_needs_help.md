---
title: "New Ubuntu user needs help"
date: 2009-05-10
forum: Apple Hardware Users
---

### Post by maflynn on 2009-05-10
Ok guys.

I'm new to the linux world and I need a little noob hand holding regardng ubuntu.  I've been reading/researching and playing with both 8.04 and 9.04 on vmware.

I just installed 9.04 on my bootcamp partition and made a swap partition as well and here's one of my questions.  

Swap partition size, since I'm running on a MBP, with 4gig of ram, how large should the partition be?  I initially created an 8gig partition but so far I've not seen any swapping. I think I made it too big.  Any insight on sizing would be great (would 64bit ubuntu alter the sizing suggestions?)


I'm really impressed with ubuntu, its a lot more efficient then windows, uses a smaller foot print much more stable. I use windows under vmware on my mac for work stuff and a couple of programs.  What application would anyone recommend to run windows programs on linux. I know there's wine but I don't know how well that works or what else there may be.

I know I'll not be giving up OSX because of what I use my mac for, Aperture, iTunes, syncing my iPhone etc but over all, I can see using Ubuntu for a lot of my work

Finally as a noob on linux any suggestions on sites/resources to get me more up to speed. I blew away my vista partition to load ubuntu 9.04 and it works a whole lot better but I know I'm only scratching the surface.

---

### Post by WA_Garrett on 2009-05-11
Usually making a swap partition between 1x - 2x of your of ram is a good amount. The thing is, swap partitions are becoming less and less necessary because computer hardware is getting bigger better faster ect. Infact you can get away without a swap partition now. I don't have one for my Ubuntu and it's been working fine and I only have 2 GB of ram. I think the reason why the swap partition hasn't been filling up is because your computer hasn't had the need to use it. I'm pretty new at this stuff to, I've only had Ubuntu installed on my MB for a few months and I use it occasionally. I find it fun to see what I can get working on it.

---

### Post by ravi_buz on 2009-05-11
Swap partition size is equal to 2X the size or Ram, and if u have Ram more than 1 gb u dont need it

---

### Post by maflynn on 2009-05-11
Thanks, for the rule of thumb. I'm monitoring my ram usage via the system monitor and so far I'm not using any of it. I've changed the swappiness to zero and reduced my swap partition to 2 gig. I think that's  a safe setting for the time being.

---

### Post by cyberdork33 on 2009-05-12
> **maflynn said:**
> Swap partition size, since I'm running on a MBP, with 4gig of ram, how large should the partition be?  I initially created an 8gig partition but so far I've not seen any swapping. I think I made it too big.  Any insight on sizing would be great (would 64bit ubuntu alter the sizing suggestions?)if you want to hibernate, you have to make the swap at least as large as your RAM.

Also, with 4GB of RAM, you really need to install the 64bit version of Ubuntu to utilize it all.

---

### Post by maflynn on 2009-05-14
> **cyberdork33 said:**
> Also, with 4GB of RAM, you really need to install the 64bit version of Ubuntu to utilize it all.
Really, so if I have the 32bit version ubuntu, I cannot access my 4gig of ram?  I knew that you'd need the 64bit flavor for anything > 4gig but not 4gig itself.

---

### Post by cyberdork33 on 2009-05-14
> **maflynn said:**
> Really, so if I have the 32bit version ubuntu, I cannot access my 4gig of ram?  I knew that you'd need the 64bit flavor for anything > 4gig but not 4gig itself.
I think it is slightly less...

run 'free' in a terminal to check RAM total.

---

### Post by maflynn on 2009-05-14
will do.

I'm waiting for a new internal 500gig hard drive for my MacBook Pro, so if I want to upgrade to the 64bit version, it will be then.

---

### Post by cyberdork33 on 2009-05-14
> **maflynn said:**
> will do.

I'm waiting for a new internal 500gig hard drive for my MacBook Pro, so if I want to upgrade to the 64bit version, it will be then.
more pros / cons are here:
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by maflynn on 2009-05-14
excellent thanks for the linky, I'm researching it right now.

---

### Post by jbruced on 2009-05-14
Congrats and welcome to Ubuntu!

Because the GTK widgets and other code are shared(buttons, sliders, checkboxes etc..), it's pretty efficient at using memory. A lot of the same used memory is shared  between applications.

I have only 512Meg Ram, and I don't swap much at all. As previously stated, 1 - 2x your ram is suggested.

---

### Post by renkinjutsu on 2009-05-17
i know that the 32bit linux kernel can support up to 64GB of RAM with PAE enabled.. i know that the 32bit server edition of Ubuntu has PAE enabled by default.. you can also recompile your desktop kernel to enable it if you're comfortable with doing things like that

i myself have not compiled anything (except for one application which i hardly use anymore)

---

