---
title: "k3b headache part II"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Rita G. on 2008-01-08
among other problems with k3b that I had yesterday, it now refuses to copy mp3's to a cd.

after clicking “new audio cd project”

and dragging mp3 down to project area, I get:

Sorry k3b

 ! Problems while adding files to the project.

Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.
/home/rp/Desktop/35074288.mp3

can someone help?     

is this thing worth wasting more time fixing, or can someone recommend a better program?

---

### Post by Lord DarkPat on 2008-01-08
use Brasero, it's equally good, and it's best on GNOME

---

### Post by indytim on 2008-01-08
If you go into the adept (or synaptic) and enter k3b, I think you will find the lib you need to do the mp3->cda thinger in k3b.  Apologies for not being more specific but I'm on Win2k @work right now.

IndyTim

---

### Post by tech9 on 2008-01-08
open terminal and type...

```
sudo apt-get install libk3b2-mp3
```

or download and install the deb from this link...

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fk%2Fk3b%2Flibk3b2-mp3_0.12.10-0ubuntu4_i386.deb&md5sum=034f70bd193191d9ff1f9c8825b1bbdc&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fk%2Fk3b%2Flibk3b2-mp3_0.12.10-0ubuntu4_i386.deb&md5sum=034f70bd193191d9ff1f9c8825b1bbdc&arch=i386&type=main)

this should do it :)

---

### Post by Rita G. on 2008-01-08
ran      sudo apt-get install libk3b2-mp3
        in terminal and got:

$ sudo apt-get install libk3b2-mp3

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

whats this?

---

### Post by monte48lowes on 2008-01-08
Sometimes an error occurs during package installation. This is usually solved by telling dpkg to correct the errors.

```
sudo dpkg --configure -a
```

Mike

---

### Post by tech9 on 2008-01-08
> **Rita G. said:**
> ran      sudo apt-get install libk3b2-mp3
        in terminal and got:

$ sudo apt-get install libk3b2-mp3

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

whats this?

I would do what monte48lowes suggested first, also you can install the deb package manually too if you prefer to do it that way.

---

### Post by Rita G. on 2008-01-08
ok got it!

thank you all for making my day........(until something else comes up, that is)

---

### Post by tech9 on 2008-01-08
> **Rita G. said:**
> ok got it!

thank you all for making my day........(until something else comes up, that is)

your welcome! :)

---

