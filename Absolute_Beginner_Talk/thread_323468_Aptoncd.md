---
title: "Aptoncd"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-12-22
Hi everybody.

I've installed Aptoncd and get an iso of the packages I've installed on my pc.  Now a friend of mine has ubuntu as well but without connection to internet; I d'like to install a program -noteedit - which I put on the iso image from my pc to the pc of my friend.
The question is that I don't  know how I can  add that program to my friend's pc  via the iso image .:confused: 
Thanks a lot for any hint

---

### Post by jvc26 on 2006-12-22
What kind of file is this app? is it a .bin? In which cans I believe you can right click, make executable in the permissions and execute it thus installing it. The installation will depend on what sort of file it is: see here for loads of stuff on installing anything in ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Enjoy :)
Il

---

### Post by tagra123 on 2006-12-22
> **helphope said:**
> Hi everybody.

I've installed Aptoncd and get an iso of the packages I've installed on my pc.  Now a friend of mine has ubuntu as well but without connection to internet; I d'like to install a program -noteedit - which I put on the iso image from my pc to the pc of my friend.
The question is that I don't  know how I can  add that program to my friend's pc  via the iso image .:confused: 
Thanks a lot for any hint

I think you can just add the cd that aptoncd created to the /etc/apt/sources.list on your friends computer.

Rather than editing manually it may be easier to use synaptic to add the cd.

---

### Post by helphope on 2006-12-22
Thanks a lot for replying:) 
> **Illuvator said:**
> What kind of file is this app? is it a .bin? In which cans I believe you can right click, make executable in the permissions and execute it thus installing it. The installation will depend on what sort of file it is: see here for loads of stuff on installing anything in ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Enjoy :)
Il

It's a file in the repo good for music job.

> I think you can just add the cd that aptoncd created to the /etc/apt/sources.list on your friends computer.

Rather than editing manually it may be easier to use synaptic to add the cd.
I tried to download the package of noteedit into a usb pen, but eerytime I needed something new: A nreeds B needs C, C needs A and D to be installed and so on.

So once I 've added it to the sources.list via synaptic manager>add Cdrom, I can install it just through synapctic or add/remove tool?

Thanks

---

