---
title: "Whining noice from CPU(Ubuntu 9.10)"
date: 2009-10-28
forum: Apple Hardware Users
---

### Post by CosyCat on 2009-10-28
hello, I always had whining CPU noice on my 2.1 MacBook but got help fixing it under OSX and Ubuntu 8.04 and 8.10 but now when upgrading to 9.10(clean install of RC on my macbook)I´m back to whining CPU and nothing seems to work 

this problem [https://help.ubuntu.com/community/MacBook2-1/Hardy#Whining%20noise](https://help.ubuntu.com/community/MacBook2-1/Hardy#Whining%20noise)
I dual boot snow leopard and Ubuntu 9.10

Intel graphic in 9.10 is so nice so I like to set Ubuntu as default os but this whine is holding me back.

Someone know how to silent my CPU.

THX

---

### Post by CosyCat on 2009-10-29
I bump this thread and ask another Q that might help me fix my problem.

how can this be don in koala?
[http://www.inliniac.net/blog/2008/07/25/fixing-noise-on-ubuntu-hardy-804-aka-setting-max_cstate.html](http://www.inliniac.net/blog/2008/07/25/fixing-noise-on-ubuntu-hardy-804-aka-setting-max_cstate.html)
set my cpu to "max_cstate=2"

thx again and hope someone know

edit:
looks like I fixed it!)

This is how I did it in terminal 
sudo pico grub.cfg 
edit this row with "processor.max_cstate=2" at the end like this
linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=b366eab5-0f04-4e8c-9459-0ffd0e6d1b58 ro   quiet splash processor.max_cstate=2


Saved and restart MacBook

No whining :)

---

### Post by karlstad on 2009-11-01
Is there no other way? I'd love it if I could do this realtime or something, like the old days when you just echo'd "2" to /sys/module/processor/parameters/max_cstate

---

### Post by boomshop on 2009-11-02
Hi,

I fear there's not. And the described one will unfortunately only last until anything or anyone updates the grub config, since the file /boot/grub/grub.cfg is written by grub2 as stated in the header.

In grub2 some things (like default kernel options) are done in /etc/default/grub, so you have to edit this file:

```
sudo pico /etc/default/grub
```

search for the line GRUB_CMDLINE_LINUX="" and change to (or add if it doesn't exist):

```
GRUB_CMDLINE_LINUX="processor.max_cstate=2"
```

press STRG+x and y to save and exit and execute the grub update:

```
sudo update-grub
```

It will rewrite your actual grub configuration with the new kernel option and will affect all kernels in /boot.

Greetz, markus.

[edit]
I think it should better be "sudo update-grub2"
[/edit]

---

### Post by laxhodu on 2009-11-02
Default Re: please check my site
Thanks for the suggestion, I wish it had worked.

---

### Post by jdriessen on 2009-11-02
yes, Boomshop's post fixed mine. (macbook2,1)

---

### Post by Morientes on 2009-12-18
Any of you know how much setting the max cstate to 2 will affect battery life?

---

### Post by boomshop on 2009-12-21
Hey!

You can measure it easily:

[http://www.thinkwiki.org/wiki/How_to_measure_power_consumption](http://www.thinkwiki.org/wiki/How_to_measure_power_consumption)

---

