---
title: "help to install kubuntu 13.04 on ppc g5 dual 2.0GHZ Geforce 6600"
date: 2013-05-04
forum: Apple Hardware Users
---

### Post by gusduenas on 2013-05-04
Hey there,
 I've been trying to install kubuntu 13.04 from the live cd with no success at all. It crashes at 80% or even less. I have an internet connection working.
So let me guide you about what is happening right now.
1. when I attempt to use the regular live on the boot screen: nothing just black screen with these two sentences
Starting network mount filesystems
stopping network mount filesystems

2. so after  lot of time trying to get into the desktop...I give up and reboot the machine...everything is as always (wrong I mean)

After some workaround and thanks to Macmichigan. I'm doing this now.

1. type live video=offb:off nouveau.modeset=0 single at boot screen

2. screen frozen when the card is detected and I type with extreme care this:
modprobe nvidiafb mode_option=1680x1050-32 which is my monitor resolution (mac cinema 20")

3. after I'm on the terminal and I type:  start lightdm

After that miraculously I'm at the enter screen and I went finally to the desktop, but when I try to install the program onto my 150gb hd formatted free space...the installer crashes at 80% and tells nothing.
Also rekong crashes all the time

IS THAT A BUG? 
If so please tell me how can I fix this....no clues at all. I'm a very newbie, no programmer at all.

Thanks.

My mac is a g5 dual 2GHZ nvidia geforce 6600 with 1gb memory.

---

### Post by gusduenas on 2013-05-04
no ideas yet?

---

### Post by gusduenas on 2013-05-05
Noting yet......please :(

---

### Post by canhoto on 2013-05-06
Have you tried with another cd? Or with another variant? As you probably know from one of my threads, I successfully installed Lubuntu on my G4 with the booting parameters that you used for booting the live cd onto the desktop. I have a problem afterwords (the reboot doesn't work well) but the installation gave me no errors during the process. So, maybe you could try with Lubuntu or with another cd of Kubuntu to see if the installation reaches the end.

---

### Post by str8bs on 2013-05-07
@gusduenas

Aside from your video which it sounds like you got working, your installer sounds like [this bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1172161"). Maybe the comments there can help.

---

