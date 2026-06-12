---
title: "ubuntu studio installation over feisty"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by gprok on 2007-06-18
I am following the HOW to install ubuntu studio over an existing ubuntu feisty and for the repository when i type this;

sudo su -c &#8217;echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list&#8217;




I GOT:::permission denied

what should do ???

Gprok:popcorn:

---

### Post by reset3x on 2007-06-18
You could go into System/Administration/Software Sources/Third-Party... and add: 

deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main  

Then do: 

wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

In the terminal..... :)

---

### Post by gprok on 2007-06-19
yea i try that but since i have a AMD64 3000+ processor so far nothing is working for me......

ty

Gprok

---

### Post by justin whitaker on 2007-06-19
> **gprok said:**
> yea i try that but since i have a AMD64 3000+ processor so far nothing is working for me......

ty

Gprok

I would download and do a fresh install. I have an AMD64 3200+, and a fresh install of Studio worked fine.

---

### Post by gprok on 2007-06-19
ok i got the dvd installation....can i just install it over feisty ??? i am aware its gonna kill feisty and being replaced by studio.......can you confirm that 



thanks so much

Gprok

---

### Post by p_quarles on 2007-06-19
It will install over Feisty if you tell it to. I guess you could dual-boot if you want to keep your old installation, but probably a lot easier in the long-run to install Studio and then add all the features from Feisty that you want using the package manager.

---

