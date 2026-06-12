---
title: "just installed ubuntu, but crashs during boot"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by rrig004 on 2007-01-17
Hi 
I have just install ubuntu onto my laptop along side windows, and now I am experiencing
what I think is the same problem that I had booting off the live CD.

The problem that I had booting off the live CD was that it would crash half way through loading, but I found that if I changed the video setting form VGA to one of the other settings then it loaded into ubuntu without a problem.

Now that I have installed ubuntu I seem to be having the problem, exept now I don't know how to fix it.

I was able to log into ubuntu in tty1, where I entered the following command:
```
sudo dpkg-reconfigure xserver-xorg
```
And followed through the instructions without having any idea as to what I was doing and at the end I got the following error message:



   Configuring xserver-xorg

   No x server known for your video hardware

   Either  you have no video hardware installed on this machine(serial console only?), or  
   the "discover" program was unable to determine which X server is appropriate for your 
   video hardware database, or it could be that your video hardware is simple not 
   supported by any available X.



As I can't get into the GUI of ubuntu I will have to fix the problem from tty1 but as a beginner I am not very familiar with the command line.

I would really appreciated any help so that I can get into ubuntu as soon as possible.

---

### Post by Canis familiaris on 2007-01-17
What graphics card do you use?

---

### Post by bigken on 2007-01-17
try selecting vesa as your driver if it works this will get you to a desktop ;)

---

### Post by rrig004 on 2007-01-17
My graphics card is a nVidia GeForce Go 6150

I just tried selecting vesa, but it made no diference, I still get stuck on a blank screen before desktop is loaded.

---

