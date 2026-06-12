---
title: "Macbook Unibody 7.1 Colour Profile"
date: 2011-02-13
forum: Apple Hardware Users
---

### Post by Alex Island on 2011-02-13
Hi All,

My first time using linux (Ubuntu 10.10), made the switch yesterday from osx, I've got it mostly set up, still having an intermittent skip in sound every 20 odd seconds when playing music or watching iPlayer etc but i'll save that one until i'm completely stumped.

Here is my current issue...

I have installed xcalib and have my .icc profile, I can get it on by using the console, but want to have it load by itself each time I start Ubuntu. From what I've read I can write a script to do this. I had a go but it won't load up.

Would anybody be able to let me know what I should be writing in the script text file, and where to put them (.icc and script) or if i'm going the wrong way about this.

Many thanks

---

### Post by Alex Island on 2011-02-15
Really nobody knows how to do this?

Bumpety bumperoids.

---

### Post by Alex Island on 2011-02-15
I've got it to run, but it only comes up for a second (the change in colour) 

Any ideas?

Any help would be much appreciated.

---

### Post by Alex Island on 2011-02-15
SORTED! Problem solved now have my colour profile booting up on startup, O I am a happy happy bunny.

---

### Post by bperdu on 2011-10-17
Hello Alex. It has been a while and you were a bit alone there.

I am facing a similar question to yours, on a Macbook pro 7,1, running 11.10. I have followed your steps using xcalib to import the Color .icc profile from the Macbook Pro settings, and they look great, but I have not found where to insert the xcalib line to get it up every time the machine starts.

Could you help?

---

### Post by bperdu on 2011-10-17
There used to be a simple config of GDM to point it to a .icc screen profile. ([https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Colors](https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Colors)) That worked for Natty as well.

Now, with Oneiric using lightdm, I can't seem to find such a config.

Is it left to other configs? and which?

At this time, I just added one xcalib line to my .bashrc, but this is a poor solution, and requires me to start a shell when opening a session and every time I connect a second screen.

I use the nvidia driver and can start a second screen only through it at the moment. Could there be a better way?

Macbook pro 7,1, Oneiric (updated from a Natty fresh install).

---

