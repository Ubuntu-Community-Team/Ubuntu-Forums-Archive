---
title: "Problem Starting 6.10-i386"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by mattigreenbay on 2007-02-15
Whenever I try starting Ubuntu on my 2006 "white box" machine it shows the loading bar zooming along, then comes up with a black screen showing " _ ". It stays like this and doesn't do anything else. Please help.  


P.S. I uploaded the .iso from [http://ubuntu-releases.cs.umn.edu/edgy/]("http://ubuntu-releases.cs.umn.edu/edgy/")

---

### Post by PPAAUULL on 2007-02-15
Press Alt-F2. That will give you a command prompt. What does it say there?

---

### Post by mattigreenbay on 2007-02-15
Trying..................... loading.......:popcorn:

---

### Post by mattigreenbay on 2007-02-15
Press it at the menu? When I pressed it at the " _ " it didn't do anything. I'll try the menu.

---

### Post by PPAAUULL on 2007-02-15
I think it is F2 it might be F1 try that if F2 doesn't work. one of them should do it. I haven't used it for a while.

---

### Post by mattigreenbay on 2007-02-15
Pressed F2 While loading, came up with " _ "

---

### Post by mattigreenbay on 2007-02-15
Nevermind.

---

### Post by mattigreenbay on 2007-02-15
Now what.

---

### Post by tronica on 2007-02-15
you could also try booting into safe graphics mode at cd boot.

---

### Post by mattigreenbay on 2007-02-15
Came up with command prompt.

---

### Post by mattigreenbay on 2007-02-15
Quick graphics mode did the same thing.

---

### Post by mattigreenbay on 2007-02-15
There's a message now, says failed to startup X server.

---

### Post by mattigreenbay on 2007-02-15
Pressed yes... Came up with 90814khfaiuy0987jk41h1$^%@ pressed yes... now back to the command prompt.

---

### Post by PPAAUULL on 2007-02-16
Ok just type this into the terminal and follow the instructions "sudo dpkg-reconfigure xserver-xorg" That will reconfigure your graphics and if you do it proporly it should fix your problem.

---

### Post by DJNOVA2006 on 2007-02-16
Ive had this problem too. It seems to be a graphics card problem, i have 3 machines, 2 with ati graphics cars and one without. The one without the graphics card is the only machine i can install ubuntu. The others i have vmware workstation running virual pc's of feisty fawn herd 3, and the other has 6.10

---

