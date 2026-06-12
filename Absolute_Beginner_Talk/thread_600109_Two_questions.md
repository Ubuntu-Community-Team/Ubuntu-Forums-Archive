---
title: "Two questions"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Frogsmasher on 2007-11-01
Okay two questions for you guys:

First I bought some new speakers since my old ones were broken, and I need the terminal code to test them. I know I could just run a music file or something, but I don't want to do that I want to test them through the terminal, I have gotten the code before but for got to write it down.

Second Okay here I am on a new OS so I look for MMO's well the big one for Linux is Planeshift. I check the SPM for a planeshift download, and don't find one. Shrugging my shoulders I proceed to the website and download it there, but the first thing I get told when I try to run it is this:


"PlaneShift_CBV0.3.020x86.bin" cannot be opened
No application suitable for automatic installation is available for handling this kind of file.
How do I open this? Did I download the wrong one?

---

### Post by oldos2er on 2007-11-01
How are you trying to run it? I would try "sh ./PlaneShift_CBV0.3.020x86.bin" in a terminal.

---

### Post by Inxsible on 2007-11-01
bin files can be installed by this 2 step process
1) cd to the folder in a terminal
2) run
```
sudo chmod +x *file-name*
``````
./*file-name*
```

---

### Post by Maestro23 on 2007-11-01
For you game, Open a Terminal and navigate to where the file is downloaded (Desktop?)

> cd ~/Desktop

sudo chmod +x PlaneShift_CBV0.3.020x86.bin (makes it executable)

./PlaneShift_CBV0.3.020x86.bin

---

### Post by Frogsmasher on 2007-11-01
Okay I tried this method, and got 

sh /planeshift_cbv0.3.020x86.bin(what i typed)

sh: Can't open /planeshift_cbv0.3.020x86.bin(what I got)

Maestro tried yours and got this:

cd ~/desktop (what I typed)
bash: cd: /home/joel/desktop: No such file or directory(what I go)

---

### Post by Maestro23 on 2007-11-01
> **Frogsmasher said:**
> Okay I tried this method, and got 

sh /planeshift_cbv0.3.020x86.bin(what i typed)

sh: Can't open /planeshift_cbv0.3.020x86.bin(what I got)

Maestro tried yours and got this:

cd ~/desktop (what I typed)
bash: cd: /home/joel/desktop: No such file or directory(what I go)

Linux is Case Sensitive.  Desktop

> cd /home/username/Desktop

---

### Post by Frogsmasher on 2007-11-01
Tried Oldos2er's method with proper caps, and got:
sh: Can't open /PlaneShift_CBV0.3.020x86.bin

Tried your method with proper caps and got:
chmod: missing operand after `+xPlaneShift_CBV0.3.020x86.bin'
Try `chmod --help' for more information.

---

### Post by Maestro23 on 2007-11-01
> **Frogsmasher said:**
> Tried Oldos2er's method with proper caps, and got:
sh: Can't open /PlaneShift_CBV0.3.020x86.bin

Tried your method with proper caps and got:
chmod: missing operand after `+xPlaneShift_CBV0.3.020x86.bin'
Try `chmod --help' for more information.

Space between x and PlaneShift

---

### Post by Frogsmasher on 2007-11-01
After a lot of strugging with the Terminal progams about slight oversights in my typing I finally got it to work thank you guys for being so patient with me and helping me out so much.

---

### Post by Maestro23 on 2007-11-02
> **Frogsmasher said:**
> After a lot of strugging with the Terminal progams about slight oversights in my typing I finally got it to work thank you guys for being so patient with me and helping me out so much.

Don't worry, we all started out like that man.  The key is, you didn't give up.:)

Some links for future ref:

Installing Software in Ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (Other good stuff as well)

---

