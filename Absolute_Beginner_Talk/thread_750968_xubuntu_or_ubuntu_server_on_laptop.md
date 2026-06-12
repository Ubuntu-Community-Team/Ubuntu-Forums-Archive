---
title: "xubuntu or ubuntu server on laptop"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by merker19 on 2008-04-10
Hi-
I run a Windows XP server at home that offers me a myriad of services such as: GB-PVR, Newsgroup downloads, SSH, SFTP, OpenVPN, and data backup. I did some research into setting up WAMP services on this box as well until I read many, many postings all regarding the same concern - use WAMP as a test environment only and if you publish your WAMP server publicly, watch out you may get hacked.

So my thinking lead to Linux and ultimately to Ubuntu --which I've enjoyed throughout the years-- and installing a LAMP server on an old IBM Thinkpad 570 with a cool 366Mhz processor, stomping 128MB of RAM and ginormous 6Gig hdd. All of these stats are certainly more than robust to support a Linux install, but I wondered if I should go with Xubuntu or Ubuntu Server? I love the small footprint of Xubuntu and the lightweight XFCE, but I'm conflicted about security repercussions of using Xubuntu vs. Ubuntu Server. Also, I NEED a useable desktop interface. I recall installing just plain Ubuntu 5 on this same laptop years ago and the disappointing sluggish response I had to work with after the fact. So my question to all those who read this post is: Should I go with Xubuntu or Ubuntu Server on this IBM Thinkpad 570 that I want to use as a LAMP server and have accessible publicly. Also, please factor in security when thinking about this question. Thx!!!

---

### Post by ibutho on 2008-04-10
Any of the two options would do. You could start with Ubuntu server, setup and configure the services you need and then install xubuntu-desktop later. I prefer not install a GUI on a server, preferring instead to do remote administration via SSH and webmin.

---

### Post by kerry_s on 2008-04-10
none of the above, go debian it's much better for a server.
net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

uncheck the desktop at package selection, check the server stuff you want.
i recommend you grab a gui after's, with those specs you should go as light as you can stand.
example xfce4:
apt-get install xorg xfce4

i'd go lighter:
apt-get install xorg jwm mc

but it's your rig, do what you think is best.

---

### Post by sdennie on 2008-04-10
I believe that if you install an Ubuntu Server machine and then type, "sudo apt-get install xubuntu-desktop", you will have essentially installed an Xubuntu machine.  The security updates and package updates all come from the same place.  I think the primary difference between Ubuntu/Xubuntu/Kubuntu is the high level meta-package that is installed.  If you start from Ubuntu Server, you can either decide to use one of those high level meta-packages, leave the machine GUI-less, or slowly build a custom GUI machine from there.  But, again, as far as security is concerned, it will make no difference: All the packages come from the exact same source.

---

### Post by newbieubu on 2008-04-10
> 
Re: xubuntu or ubuntu server on laptop
none of the above, go debian it's much better for a server.
net installer->
[http://cdimage.debian.org/debian-cd/...sinesscard.iso](http://cdimage.debian.org/debian-cd/...sinesscard.iso) 

Hi, your suggestion is quite good. But can you show me the link that i can get it full. 
and some commands that is suitable for that OS.

> 
Any of the two options would do. You could start with Ubuntu server, setup and configure the services you need and then install xubuntu-desktop later. I prefer not install a GUI on a server, preferring instead to do remote administration via SSH and webmin.


DO you have commands that use to control Ubuntu server without GUI. And pls tell me how can I control via SSH or webmin.

---

### Post by hyper_ch on 2008-04-10
what do you want to control by SSH? You edit config files and (re)start/stop services on the server...

---

### Post by merker19 on 2008-04-10
Awesome suggestions... and thanks for the info on the diff between Xubuntu and Ubuntu. I've tried many flavors of Linux over the years and I'm still a n00b with it... I've learned a number of things on Linux, but everytime I want to do something I run into 5 other things I need to learn just to accomplish my original goal... point being, I need a GUI to help me do what I need on this server. Thx!

---

### Post by kerry_s on 2008-04-10
> **newbieubu said:**
> Hi, your suggestion is quite good. But can you show me the link that i can get it full. 
and some commands that is suitable for that OS.


[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/)

this might help->
[http://howtoforge.com/perfect_setup_debian_etch](http://howtoforge.com/perfect_setup_debian_etch)

---

### Post by Oldsoldier2003 on 2008-04-10
> **hyper_ch said:**
> what do you want to control by SSH? You edit config files and (re)start/stop services on the server...

I do all that by ssh. but in the case of the home laptop server you can just do it from the console of course.

---

### Post by hyper_ch on 2008-04-11
I just don't see a point on installing a gui on a server...

as said, configuration is done by editing config files and whether you do that in a fancy gui environment or basic text editor does not matter at all...

---

### Post by Oldsoldier2003 on 2008-04-11
> **hyper_ch said:**
> I just don't see a point on installing a gui on a server...

as said, configuration is done by editing config files and whether you do that in a fancy gui environment or basic text editor does not matter at all...

yep, ssh and use nano or vi. there really isnt any need for a gui text editor.

---

