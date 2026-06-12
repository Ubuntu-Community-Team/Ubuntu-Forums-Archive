---
title: "Asus A7n266-vm &amp; Nvidia Geforce2"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by AnyKeyButShift on 2007-06-05
I downloaded and installed Ubuntu 6.10 after reading about it on Fravia's site. I was amazed. Not new to computers but absolutely new to Linux, I was hooked.

I did have a problem with the Nvidia driver though. I have an ASUS A7N266-VM with GeForce 2 (NV Crush11) integrated motherboard (I know these things now ;-)).

I used the Add/Remove to find the Nvidia drivers but I didn't know which one to install. I mean, how old is old and what is new? I went with the leqacy option but it didn't work, luckily I had written down how to revert to the original x.conf (And what is with that backup...down to the second? As a newbie but not a newbie, I know why but...why?).

After recovering, I tried the later driver but that didn't work either. After a lot of searching and sudo'ing this and sudo'ing that and typing that damn forever changing backup string, I gave up (I know, I should have saved an easier file to restore...well...now that I know).

But it was like a tooth with a hole...I couldn't leave it alone.

I found out about Automatix and installed that. I saw there was a Nvidia driver section where Automatix would detect and install the driver needed. And it was easy to restore the old x.conf file if things went to pear shaped.

It worked. No probs. Big splash screen came up and Nvidia with all the options in the system tools.

In love with Ubuntu I grabbed a 7.04 iso and installed it over Edgy. 

Not even Automatix helped me out here. Nvidia just would not work. I tried using lots of posted "fixes" and drivers and waited every time the "New Updates" appeared to help me out but nix.

Frustrated, I re-installed 6.10 with Automatix and a working driver (yes, I downloaded all the upgrades for Edgy...again) and then upgraded to 7.10 via the online Update Manager.

It sorta worked...the login screen was only partly rendered and after I logged on I could "paint" the screen using my mouse like colouring in. A lot of fun unless you actually want to do something.

After more searching, reading, downloading, sudo'ing this and that (not really knowing what I was doing) I have gone back to 6.10. Where things worked...or, at least, I could get them to work. Even if I don't know why.

p.s. I have just found Beamerboy's post about Nvidia drivers. I am lucky. This month there will be a Blue Moon! I'm gonna try it then.

p.p.s. this post is a little tongue-in-cheek or tongue-in-tooth if you prefer. But I'm still an absolute newbie...noob...green...whatever when using Ubuntu is concerned. I have nothing but respect for the people that help in this forum and I hope to be able to contribute sometime in the future...as soon as I figure out who that babe beryl everybody talks about is.

---

### Post by Bruegger on 2007-06-11
Hey,
I got the same mobo and the same set of problems, random crashes screen painting with mouse et al.
Using the 9639 drivers on ubuntu 7.04. Hope someone can help us out fic the prob and we can go back to enjoying ubuntu like in dapper or edgy.

Bruegger.

---

### Post by dib058 on 2007-06-28
The motherboard has Nvidia Gforce2 MX 200, thus don't work (or partially) with 9xxx driver.

For feisty :

sudo apt-get install nvidia-glx-legacy

(must enable restricted repo)

hope that work (it work for me, i have same mb)

---

### Post by Bruegger on 2007-08-12
Thanx Dib08,
got 3d acceleration on my mobo now.
but compiz-fusion wont work.
is it because of the legacy drivers???
any ideas???

---

