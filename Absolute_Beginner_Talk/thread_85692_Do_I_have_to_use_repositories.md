---
title: "Do I have to use repositories?"
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by SunshineSmile on 2005-11-03
Ok, I have figured out how to get programs with the package manager, providing that the programs I am looking for are in the online archives.

Now take this scenario. I have a younger brudda with a stinking Win Me OS, and he is fed up about it. I was thinking; perhaps I could have him try ubuntu on his comp. Now, there is a catch. He has no decent internet connection. So how am I gonna get all the fun shit installed on his comp, like gnomad for his Zen micro, RealPlayer, Vlc etc. How do you install all of this from a cd, and not from a repository?

---

### Post by teaker1s on 2005-11-03
cd rom entry in sources list or you could just copy packages off cd and install from them

---

### Post by raublekick on 2005-11-03
You can use the CD as a repository too. I'm not sure how much is on there, but give it a shot. 

I'd try popping in the Live CD on his computer, but disconnect it from the network/don't try to dial-up. Then go into Add Programs and see what you can do. This will give you a good idea of what is possible on his machine. A lot of stuff on the repos really isn't all that big though.

---

### Post by az on 2005-11-03
Well, you can download the apps on your computer, then backup everything in /var/cache/apt/archives and transfer then to his computer.  You could cd to your usb drive where you saved them and run from a terminal:

sudo dpkg -i *.deb

---

### Post by poofyhairguy on 2005-11-03
Best solution is this one:

[http://ubuntuforums.org/showthread.php?t=78549](http://ubuntuforums.org/showthread.php?t=78549)

---

