---
title: "I'm lost, please help.. [not optimum mode]"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by soMzE on 2007-06-22
Hello all :)

I'm just starting out to use the Ubuntu OS, you should first know i always was a Windows user like many, so i don't know much about it all.. for now.. :)

What i did:

Downloaded Ubuntu 7.04 x86 & x64
I ran the Livecd install cd from the bios, after the spash screen i get this message from my Samsung syncmaster 913n - "Not optimum mode, 1286 x 1024 60 hertz recommended"

I ran the install cd again and i pushed F4 to change the display settings and i was in the installation :cool:
Then there was no mouse pointer, but i managed to install Ubuntu with my keyboard, after the installation was done i got the same message - "Not optimum mode"

I searched the forums and i seen many people having this problem, i found somewhere on this forum that i have to edit the xorg.conf file, but i can't edit it from the livecd because it's locked but have read this in another post:

```
sudo mount /dev/sda1 /mnt
sudo nano /mnt/etc/X11/xorg.conf
```

I do this after pressing ctrl-alt-F2 but the file appears empty, what do i do to edit this file and finally start using Ubuntu?

Thanks,

soMzE :)

My Specs:
- Nvidia 7800GTX
- AMD Athlon X2 3800 Dual Core CPU

---

### Post by sandeep108 on 2007-06-22
Did you not try and change the res./freq in the display preferences? If you can do it from there no need to bother with xorg.conf. Also once you finally install ubuntu on your HDD, you may be able to install the correct display drivers for your system which would then allow you to change the res./freq. modes.

---

### Post by raul_ on 2007-06-22
Why don't you boot from the hard disk if the installation was completed? After that, if you get thrown at a terminal, just type 

"sudo dpkg-reconfigure xserver-xorg"

and answer the questions

---

### Post by soMzE on 2007-06-22
> **sandeep108 said:**
> Did you not try and change the res./freq in the display preferences? If you can do it from there no need to bother with xorg.conf. Also once you finally install ubuntu on your HDD, you may be able to install the correct display drivers for your system which would then allow you to change the res./freq. modes.

Hello and thnx for the quick reply :)

But i can't get in system at all, at least i'm in but cannot see anything.. so no possibility to set the display settings or drivers...

---

### Post by soMzE on 2007-06-22
> **raul_ said:**
> Why don't you boot from the hard disk if the installation was completed? After that, if you get thrown at a terminal, just type 

"sudo dpkg-reconfigure xserver-xorg"

and answer the questions

Thnx going to try this now ;)

---

### Post by soMzE on 2007-06-22
> **raul_ said:**
> Why don't you boot from the hard disk if the installation was completed? After that, if you get thrown at a terminal, just type 

"sudo dpkg-reconfigure xserver-xorg"

and answer the questions

Hmm i think i messed up :( Now the x-server can't be loaded anymore :confused:
I answered all these questions but don't know what i did wrong..

---

### Post by raul_ on 2007-06-22
Try again :) maybe you loaded the wrong video driver

---

