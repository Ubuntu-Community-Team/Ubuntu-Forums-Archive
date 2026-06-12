---
title: "Error on booting installation disk"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by lelrod on 2007-10-06
I have made an Ubuntu image disk and I am trying to install it on an HP Pavilion computer that currently has Windows ME.  It appears to be booting from the CD rom (it reads it for 3-4 min and does not go to the hard disk) then I get this:

/----pstk------------rstk-------\
|   :                  |  :                 |
|   :                  |  :                 |
|   :                  |  :                 |
|   :                  |  :                 |
| 0:          0. 0  |  :                 |
| 1:          0. 0  |  :                 |
| 2:          0. 0  |0: ffffffff. 5 |
| 3:          0. 0  |1:   121d.15 |
|---------------------------------|
| err  8                                  |
| ip 11d4:        10.7               |
\---------------------------------/


Is my CD bad?  Is there a hardware problem?  Please help.

LE

---

### Post by lelrod on 2007-10-06
The spaces did not come out on the error messsage, but the info is ther.  The lines actually form a box.

---

### Post by Pumalite on 2007-10-06
Post specs. Did you follow this: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
And this: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
You might need Alternate CD or lighter desktop.

---

### Post by Iendicis on 2007-10-06
Post what your computer's specs are at, and also what speed to recorded the CD to. Typically you want to stay at 4x for CD-R and 2x for CD-RW (It works great for me!).

---

### Post by lelrod on 2007-10-06
The computer is an HP Pavilion with Intel Pentium III and 256MB RAM.  I plan to reformat and get rid of Windows.  Is there too little memory?

CD-RW was burned on a much newer HP Slimline with AMD64 dual processor and Vista Home Premium.  I don't know the speed.

---

### Post by lelrod on 2007-10-06
I did follow the burningIsoHowTo instructions.  The CD appears as it should.  I have scanned the psychocats page, but did not see this problem listed.



I am quite impressed by the rapid replies.  Thanks.

---

### Post by Pumalite on 2007-10-06
256 MB RAM> Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
You might be able to boot a Live CD, but you would have to make 500 MB /swap ahead of time. And then, if it installs it would be too slow.

---

### Post by lelrod on 2007-10-06
I appreciate the advice.  I have downloaded the alternate installer and I am burning the image with InfraRecorder.  I'll let you know if it works.

---

