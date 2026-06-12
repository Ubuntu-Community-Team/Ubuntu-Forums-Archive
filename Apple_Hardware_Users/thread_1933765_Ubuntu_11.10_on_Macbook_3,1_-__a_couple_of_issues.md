---
title: "Ubuntu 11.10 on Macbook 3,1 -  a couple of issues"
date: 2012-03-01
forum: Apple Hardware Users
---

### Post by Sparky88 on 2012-03-01
Ok so I installed 11.10 about a week ago and am liking what I am seeing. However I have a couple issues.

1. this computer is a multi-boot os x lion and ubuntu 11.10. I can see the mac partition, mount it and see folders in it but when i get to a folder past my osx user folder i cant go any further it says i dont have permissions. I have been looking for clear instructions on how to change the permissions so i can read/write to that partitions. I keep finding things that say how to mount but mounting is not the problem.

2. I notice that the red light is coming out of the optical sound port. is ther a way to turn off optical until a optical plug (toslink) is used?

Sorry if there is other threads on this already but search for either item keeps bring back no results

---

### Post by pindar on 2012-03-01
> **Sparky88 said:**
> I can see the mac partition, mount it and see folders in it but when i get to a folder past my osx user folder i cant go any further it says i dont have permissions.
Both the user name and the numeric id should be identical on linux and os x. Have you checked if this is the case for you? By default, os x assigns a uid of 501 to the first user, ubuntu a uid of 1000. You can change it on either side; changing it in linux is somewhat easier, but changing it on os x may be more profitable in the long run (in case you ever want to install or re-install a different linux system).

---

### Post by Sparky88 on 2012-03-01
Ah, thanks man. I had the same user name but didn't think about the UID

---

### Post by WonderWoofy on 2012-04-06
I am having the same issue with the optical light, albeit my mac is 2,1.  I would kind of like to figure that out myself.  

As for the sharing between systems, I figured that out not too long ago myself.

If you want to change it on the Linux side, from the login screen, hit ctrl+alt+F1, and log in as root.  Or you can do this from an alternate user account than the one you are trying to change.  

In /etc/login.defs UID_MIN and GID_MIN need to both be changed to 501.

In /etc/group, the "dialout" value should be changed from 20 to 99.
Also, the line that begins with your username:1000: should be changed from 1000 to 20.

In /etc/passwd, the line with both your real name (long name) and user name (short name) needs to be changed such that the values are 501:20 rather than 1000:1000.

After that it is just a matter of changing the permissions in the/home folder.
$ chown -R 501:20 /home/username

This is of course, all assuming that your user id in OSX is 501 and your group id is 20.

I hope this helps...

---

