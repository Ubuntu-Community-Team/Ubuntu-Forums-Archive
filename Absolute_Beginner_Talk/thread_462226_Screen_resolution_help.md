---
title: "Screen resolution help"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by mrFlibble47 on 2007-06-02
I am having trouble getting the screen resolution higher than 1024x768.
Obviously I have already searched these forums and have seen that many other people have had this problem, and I have followed the instructions about editing xorg.conf and yet this hasn't worked. The higher resolution *is* listed in the relevant part of xorg.conf and yet it still wont let me change the resolution. 
I've also tried dpkg-reconfigure -phigh xserver -xorg  and selected vesa and put an asterisk next to 1280x1024 in the list of resolutions and this hasn't helped.
I am now stuck for ideas to try. Can anyone help?
Thanks

---

### Post by MrMatt2532 on 2007-06-02
You could try adding a modeline to the monitor section of xorg.conf. Here is the link for the generator: [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php). For example for 1280x1024x85 the modeline would be: 

# 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
  Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync

This worked for me when I had issues.

---

### Post by bobbocanfly on 2007-06-02
It might be a restraint with your video card. Mine is a few years old and will only run at 1024x768 but on my newer laptop it will run at a high resolution. 

You should check if your video card/monitor can definately handle a higher resolution.

---

### Post by mrFlibble47 on 2007-06-02
Right i've pasted in Modeline..etc into the monitor section of the file. Will see if that makes a diff.

I'm fairly sure the graphics chip will support that resolution (the pc is one i put together a few days ago and the mobo has onboard graphics with shared ram)

---

### Post by mrFlibble47 on 2007-06-02
Tried it, and still it's not giving me the option of increasing above 1024x768 :-(

---

