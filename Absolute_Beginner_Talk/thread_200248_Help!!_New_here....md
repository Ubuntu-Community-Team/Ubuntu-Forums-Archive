---
title: "Help!! New here..."
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Namgyel on 2006-06-20
Hi

I recently tried to use linux instead of windows but ever since I got an aditional graphics and put it in the SLI I can't do anything with any linux... 

Here are the basic specs of my machine:


Biostar N4SLI-A9-A01
2 x MSI 6600GT video cards
AMD 3200+ socket 939 proccy

Any help would be very appreciated


best regards, 
Namgyel


PS: I've also posted a post here [http://www.ubuntuforums.org/showthread.php?t=193542&highlight=Namgyel](http://www.ubuntuforums.org/showthread.php?t=193542&highlight=Namgyel)

---

### Post by nalmeth on 2006-06-20
Did you disable the onboard graphics (if any exist) in your BIOS?

---

### Post by Namgyel on 2006-06-20
What do you mean? Don't know if I have any - really doubt it.... 

The thing is that Ubuntu 5.10 worked on my 6600gt when it was just one. When I added the other one it stopped working.

Do you know any systems besides Ubuntu, Kubuntu... that would work with my computer? Did you see anything similar that would be the problem with other people?

One last thing... Do you know if it's possible to get a dvd non-live version installer for Ubuntu 6.06? Links would be great...


Best regards,
Namgyel

---

### Post by %hMa@?b&lt;C on 2006-06-20
if you are dropped into a terminal that says something like
username@ubuntu $ 
try typing 
```
sudo dpkg-reconfigure xserver-xorgp
```
and select the vesa drivers when you are given an option

---

### Post by Namgyel on 2006-06-20
Tried it now - says I don't have that package... 

I must write sudo apt-get ....?


Best regards

---

### Post by taurus on 2006-06-20
It should be
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Namgyel on 2006-06-20
Didn't work:( ...

Do you know where to get a dvd non-live version installer for Ubuntu 6.06? Links would be great...

---

### Post by bruce89 on 2006-06-20
[QUOTE=Namgyel]Didn't work:( ...[/QUOTE]
You don't seem to have X installed
```
sudo apt-get install ubuntu-desktop
``` should fix it.
[QUOTE=Namgyel]Do you know where to get a dvd non-live version installer for Ubuntu 6.06? Links would be great...[/QUOTE]
See [http://www.ubuntu.com/download/](http://www.ubuntu.com/download/), near the bottom.

---

### Post by Namgyel on 2006-06-20
Tnx - will try downloading it tommorow :) - and reinstalling the X....

---

