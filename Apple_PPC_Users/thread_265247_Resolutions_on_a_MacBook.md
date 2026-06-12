---
title: "Resolutions on a MacBook?"
date: 2006-09-25
forum: Apple PPC Users
---

### Post by pan_linux on 2006-09-25
How can I enable a widescreen resolution on my MacBook? I only get 1024x768… 
(accidently posted this in the beginners forum, too)

-pan

---

### Post by goneskiing on 2006-09-25
you need to download and install the 915 intel package - that should adjust your resolution automatically.  (search in synaptic for it)

---

### Post by geodude on 2006-09-25
Is this the same for the Macbook Pro?

Chipset Model:	ATY,RadeonX1600
  Resolution:	1680 x 1050

Going full screen (using Parallels) results in a pretty ugly display! I've love to be able to get out of the default Parallels window.

---

### Post by pan_linux on 2006-09-26
Hmm, from what it looks like, it's already installed, isn't it? 

[IMG]http://axiom.gmxhome.de/ubuntu1.gif[/IMG]

---

### Post by geodude on 2006-09-26
Go to [http://forums.macnn.com/104/alternative-operating-systems/300577/macbook-and-parallels-ubuntu/](http://forums.macnn.com/104/alternative-operating-systems/300577/macbook-and-parallels-ubuntu/)

and follow the directions given by "kleinemans" and you'll get the  1280x800.

It's not all the way wide-screen, my MBP supports 1680 x 1050. I've not tried if simply plugging in those number will work. :-/

---

### Post by goneskiing on 2006-09-26
pan
no the file name begins with 915 I believe (it's not an xserver pkg) - works well on the 15" macbook pro

---

### Post by hajk on 2006-09-27
The package "915resolution" can be installed via Synaptic... but it may be necessary to uncomment additional repositories (like universe) in /etc/apt/sources.list.

---

### Post by vanth13 on 2006-09-30
I installed it but nothing happened. I have the custom resolution set on on parallels... I don't know what else to do...
if I use the sudo gedit /etc/X11/xorg.conf and add the res it doesn't work 
if I use the reconfig command It doesn't find the driver... 
any idea???

---

### Post by geodude on 2006-09-30
use the macnn link. easiest route.

---

### Post by vanth13 on 2006-09-30
can you explain to me how to?? sorry but I'm really new to linux. it's my first day...

---

### Post by hajk on 2006-09-30
> **vanth13 said:**
> I installed it but nothing happened. I have the custom resolution set on on parallels... 

Two things need to done before the 1280x800 native screen resolution can be used in a Parallels VM running Ubuntu:

1. Configure Parallels (File -> Edit Configuration), highlight Video and add the 1280x800 Screen Resolution and enable the check boxes, then save this new setting and quit.

2. Start Ubuntu and then run "sudo dpkg-reconfigure xserver-xorg". The suggested settings are OK, except for the following: choose the "vesa" graphics driver, and then choose *only* the 1280x800 resolution (uncheck the others). 

Restarting X (or rebooting Ubuntu) will make the native 1280x800 resolution available.

---

### Post by vanth13 on 2006-09-30
I've done all you said and:
the starting window with the login was 1200x800, but after the login the sistem crashed: nothing appeared and the processor started pushing hard. I quit... now? how can I recovery the situation? damn it I going mad with this resolution!!!

now it start whitout graphic...just terminal.. help!!

thanks a lot for your tips..

---

### Post by vanth13 on 2006-09-30
ok I reinstalled everithing. now if I run 915resolution like this:

sudo 915resolution  etc

it says that it only works with 800 e 900 series. on mackbook there is intel gma 950...

so I can't change the resolution running it...

It's beoming a war. and I can loose a battle but the war will be mine...!!!

Ideas???

---

### Post by hajk on 2006-09-30
Vanth13, I goofed in my advice to you, I'm terribly sorry.:(  I got installing in Parallels and directly to the HD mixed up, my fault entirely.

You need not install the 915resolution package, so uninstall it with
"sudo apt-get remove 915resolution". Then run "dpkg-reconfigure... ", restart X (or reboot), and things should be OK.

---

### Post by vanth13 on 2006-09-30
ok but when I run reconfigure

I don't get the 1200x800 between the res I can use for the monitor... theres only 1280x...

I'm trying...

It starts with 1200x800 login (as earlier) and then just terminal, then reappear the login and so on without endin...


](*,) :twisted: ](*,)

---

### Post by hajk on 2006-09-30
Yes, 1280x800 (ratio 8:5), you're almost there...:p

---

### Post by vanth13 on 2006-09-30
yes but after the login  it doesn't start with graphical interface!!! and loop with the login... unusable!!

---

### Post by hajk on 2006-09-30
Ok, reboot the recovery session (single-user mode), it will give you a non-graphical root terminal. Then you can simply do (without the # prompt):

# apt-get remove 915resolution

# dpkg-reconfigure xserver-xorg

# reboot  

and then boot the regular Ubuntu session.

---

### Post by Halsnalle on 2006-11-15
Vanth13, did it work out for you eventually? I'm running Parallels 1970 and Ubuntu 6.10 on a MacBook Pro C2D, and have bumped into similar problems (the looping login etc).

Any suggestions? Would be really nice to be able to run Ubuntu full-screen in Parallels.

---

