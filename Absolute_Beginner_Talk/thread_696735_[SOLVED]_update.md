---
title: "[SOLVED] **update**"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Scut_Farkus on 2008-02-14
**UPDATE**

Well, I have to say that I think I ended up getting ANOTHER bad hard drive! 

Irritating, but Newegg rocks, so I'll just send it back to them. 

My Live CD experiments are working flawlessly. 

I got some really simple instructions to get the 3D Nvidia drivers working from a site called [www.pendrivelinux.com](www.pendrivelinux.com).

Here's what they said to do:
1.) sudo apt-get update <--when I did this on the installed version, I got error messages. No problem with the Live CD.
2.) sudo apt-get install nvidia-glx
3.) sudo apt-get upgrade <--it's still going....it error'd out on me very quickly when I did it before

Hmmm...okay...got an error this time. Perhaps this is because these steps are not meant to be carried out on the Live CD? (I hope, I hope, I hope)

Errors were encountered while processing:
/var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-52_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

4.) sudo dpkg-reconfigure xserver-xorg <--couldn't even do this step on the installed version and I can't do it now. It crashes when I try to configue the xserver at the point where it talks about PowerPC's and multiple video devices. I should be able to simple hit ENTER at this point, but it stops. 

These steps worked with Dapper. I tried it and it worked flawlessly, so perhaps these instructions are only good for Dapper and Gutsy has some other way to do it?

Anyway, despite the errors, I'm encouraged that some newer, perhaps better hardware might ease some of my Ubuntu Gutsy woes.

Thanks everybody! 
__________________

---

### Post by Scut_Farkus on 2008-02-15
Please ignore the instructions I gave regarding the 3D drivers for nVidia cards.  If you've got Gutsy, just be sure to add all the repositories and then activate the proprietary driver for your nVidia card.  

It worked like a charm for me.

**Note:  I only illustrated the instructions in my earlier post because I was having so many problems.  I wanted a simple, project based, illustration to find the differences between a Live CD and the installed version.

---

