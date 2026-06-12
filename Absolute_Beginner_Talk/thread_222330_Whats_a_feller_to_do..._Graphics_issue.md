---
title: "Whats a feller to do... Graphics issue"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by mbrang00 on 2006-07-24
Im on my laptop (currently running Ubuntu), I liked it so much that i wanted to install it onto my desktop and dual boot it with windows...

No problem there, she dual boots like a pro.

My problem is once ubuntu loads into the login screen, my graphics are so screwd that once could not tell what the page was displaying. The only reason i know what it was is because i have it on my laptop.

Knowing that it was the login screen i entered my username and password, then heard music as it was logging in, which is good, that means it was for the most part a clean install, But,

I still cant make anything out, garbage all over the screen.

Specs:

AMD athlon 64 2800+(running 32bit ubuntu)
1.5GB RAM
Gigabyte GA-k8nsxp Mobo
BFG Tech Ge-Force 7800 GS OC (AGP)

This is out om my relm I dont know what to do when i cant see anything
 Please help

---

### Post by orb9220 on 2006-07-24
Well when you are in ubuntu go to system>adminstration>Login window

And see what it looks like there. In fact select another one close and log out and see if it is still doing it.

If it is then it may be something in your etc/X11/xorg.conf file which you can view.

open a term and enter: gedit etc/X11/xorg.conf which will open in gedit since it is not sudo gedit you don't have to worry about changing anything.

Just copy text there and paste to post here and we can take a look at.

It could be something I am not aware of since I am new to so others out there help us out with yer wisdom.

---

### Post by agurk on 2006-07-24
> **orb9220 said:**
> Well when you are in ubuntu go to system>adminstration>Login window
how can he do that if the screen is garbled and completely unreadable? :-k

---

### Post by nalmeth on 2006-07-24
When you get to the login screen, instead of logging in type:
CNTL-ALT-F2 to switch to a virtual terminal (CNTL-ALT-F7 to get back)
login, and enter this command:

sudo dpkg-reconfigure xserver-xorg

When getting to the video driver, pick VESA
Pick defaults for everything else.

sudo reboot

---

### Post by mbrang00 on 2006-07-24
> **agurk said:**
> how can he do that if the screen is garbled and completely unreadable? :-k


You beat me to it...lol 


Nelmeth...im going to try that now...will post results in a little while
thanks for the input

---

### Post by mbrang00 on 2006-07-24
ok i did everything....when i switch back, it is still fubar...
Id like to restart the computer, but i dont know the terminal command to do that


anyone?

---

### Post by mbrang00 on 2006-07-24
well i figued it out.... sudo shutdown "time"

I put in 15 thinking it was seconds...no...its minuts...now i cant do anything for 15 min

---

### Post by mbrang00 on 2006-07-24
I couldnt wait...i did a hard restart...but hey that did the trick... I can see...


Now i need to find a forum to configure the drivers for my video card i guess...

Thanks for your help

---

### Post by nalmeth on 2006-07-24
What kind of video card do you have? 

If it's an Nvidia card and supports 3D, look here:
[http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation](http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation)

If it's an ATI card and supports 3D, look here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Cheers

---

### Post by mbrang00 on 2006-07-24
good links nalmeth, thanks agian
that make 2 for you today.


I should just have you ssh into my computer, but then i wouldnt learn anything




thanks agian

---

### Post by mssever on 2006-07-25
> **mbrang00 said:**
> ok i did everything....when i switch back, it is still fubar...
Id like to restart the computer, but i dont know the terminal command to do that


anyone?

I don't know if this is still relavant to you, but to reboot, you type "sudo reboot" and to turn your computer off you type "sudo poweroff".

The shutdown command is the old school way of doing things. The equivalant to sudo reboot is "sudo shutdown -r now" and the equivalent to sudo poweroff is "sudo shutdown -h now". Of course, you could delay the action for a number of minutes, but that's only useful when there are multiple people logged onto your machine and you want to give them time to save your work.

---

