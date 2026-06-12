---
title: "So is the live cd realy your freind"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by nikef on 2008-02-05
I had a problem with my top bar just freezing,i could not do anything,
1 click on it and that was itit froze,i searched the forums it said to put cd in pc and in terminal write

sudo apt - ge update && sudo apt -get-f install ubuntu - desktop 

i did this and it installed some items,now did the cd fix my problem?, i have been able to use the top bar without it freezing

if so,what did the cd do to fix it,please could some1 help me understand

thanks

---

### Post by kpkeerthi on 2008-02-05
> ,i searched the forums it said to put cd in pc and in terminal write

sudo apt - ge update && sudo apt -get-f install ubuntu - desktop

You mean you booted with the Live CD and ran that command? All you did was you reinstalled gnome desktop to your Live Session. I doubt that fixed your problem.

---

### Post by emarkd on 2008-02-05
I think you fixed your problem by rebooting.  The live CD is very useful in many respects, but you have to operate on the OS installed on your hard drive in a bit more low-level manner.  Your commands just affected the session you had running in RAM from the Live CD.

---

### Post by nikef on 2008-02-05
thanks

i rebooted many times yesterday and i still had the problem :confused:

this morning after starting up,i went into software sources and changed it so it installs from cd,then  i popped the cd in my pc and used the the comands in terminal,so it was not the cd then ?

---

### Post by nikef on 2008-02-05
> **kpkeerthi said:**
> You mean you booted with the Live CD and ran that command? All you did was you reinstalled gnome desktop to your Live Session. I doubt that fixed your problem.

No ,i did not boot with the cd,my gusty was on my pc,i just put the cd into drive and wrote that in terminal 

thanks

---

### Post by emarkd on 2008-02-05
> **nikef said:**
> No ,i did not boot with the cd,my gusty was on my pc,i just put the cd into drive and wrote that in terminal 

I misunderstood you to mean that you had booted from the LiveCD, so I guess my previous posts didn't make much sense ;)

There are packages from the live CD, but the same packages, with newer versions of some packages in the repositories.  You should use the newer versions if you can, but there are instances where using older versions are more stable.  I wouldn't expect this to be the case with ubuntu-desktop, though.

My guess is that you had a misconfiguration of some sort and re-installing the package got it straightened.  You could probably have done the same thing using the online package and gotten the same result.  You may want to re-enable all of the repositories and run an update to make sure you've got all of the security patches now.

---

### Post by nikef on 2008-02-05
> **emarkd said:**
> I misunderstood you to mean that you had booted from the LiveCD, so I guess my previous posts didn't make much sense ;)

There are packages from the live CD, but the same packages, with newer versions of some packages in the repositories.  You should use the newer versions if you can, but there are instances where using older versions are more stable.  I wouldn't expect this to be the case with ubuntu-desktop, though.

My guess is that you had a misconfiguration of some sort and re-installing the package got it straightened.  You could probably have done the same thing using the online package and gotten the same result.  You may want to re-enable all of the repositories and run an update to make sure you've got all of the security patches now.

No it was my fault for not explaining properly in my first post,yes i have re-enabled all of the repositories,but i did not run an update,i shall do that now

thanks :)

---

