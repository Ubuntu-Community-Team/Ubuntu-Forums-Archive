---
title: "Synaptic Package Manager - where does it go?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by music_man on 2006-07-14
Hi

I have downloaded several things - like Freeciv using the package manager and I can't find where it has gone.

I tried making a shortcut to launch freeciv-client-gtk but it couldn't find it.

---

### Post by PhilOSparta on 2006-07-14
Go to your Task Bar  Places->Search for Files  and when the screen comes up, select the entire file system, and enter the name of the package.

It should show up with the entire path listing.

This is a life saver when the downloaded package doesn't have a menu position.

Good luck.

---

### Post by music_man on 2006-07-14
It can't find it :(

---

### Post by Third Thoughts on 2006-07-15
Try opening synaptic up again and going to the package you're interested in (in this case freeciv I guess). Click on the package and then click the properties button. (Its the button with the wrench and the peiece of paper.) Click on the "installed files" tab. You'll now see a list of all the installed files. If you're looking for the binary, then look for whatever files are stored under /bin

~Andrew S.

---

### Post by T700 on 2006-07-15
As a work around, try pressing Alt-F2 and then typing:

--deleted--

Advice corrected by [S|G].  Thanks!  :-)

Paul

---

### Post by [S|G] on 2006-07-15
To start freeciv, the command is ```
civclient
``` for the client or ```
civserver
``` for the standalone server.

---

### Post by music_man on 2006-07-15
Ah that worked! Thanks! Is there a quick way of finding out what command it is? Is the binary the executabl;e file?

---

### Post by [S|G] on 2006-07-15
I'm not sure where it is on synaptic, but on adept (kubuntu's package manager) you have a details option on the package that shows all files that the package is installing. There you can take a look to determine what is going to be installed.

And yes, the executable is the binary.

---

### Post by 3rdalbum on 2006-07-15
Another way is to try:

```
man packageName
```

and see what pops up.

In Synaptic, when you're looking for the name of the executable, it actually won't be under /bin. It is much more likely to be under /usr/bin or /usr/local/bin or something like that.

---

### Post by adam.tropics on 2006-07-15
look in /var/cache/apt/archives if you used the package manager

---

### Post by music_man on 2006-07-15
Thanks for all your help. It is so awesome to have such helpful people to provide support for a newbie like myself.

Thanks again.

---

