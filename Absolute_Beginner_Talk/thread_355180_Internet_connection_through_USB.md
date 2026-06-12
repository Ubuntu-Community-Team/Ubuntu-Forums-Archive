---
title: "Internet connection through USB"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by icyblue on 2007-02-06
Hello!!!

I can't configure my ethernet card in Ubuntu. So, I've planned to connect Internet via USB.. I'm usin a ADSL router... Please tell me how to do it?

Thanks!!!

---

### Post by Mike_Longbow on 2007-02-07
I'm afraid I don't know how to do that, but I know it will be a hard task... 
Well, it all depends on your router: if they got linux drivers it's all right, but if they don't... well, ahm... too bad.
I got a 2WIRE router myself, wich usb interface doesn't support linux :( And I have not found a way to make it work...
I would recommend to use your Ethernet interface, it should be (theorically) the most reliable and troublesafe one.

---

### Post by icyblue on 2007-02-07
I'm using silan SC92031 ethernet card but It's not configured automatically... I read the notes in installation cd for linux, It says to compile a the code sc92031.c and get the output 'sc92031.o' but I'm gettin a lot of errors durin compilation...

---

### Post by Mike_Longbow on 2007-02-07
:-k 
are you trying to compile directly from the cd? If so, try moving the files to compile to a writeable location (i. e. your home dir) and then try to follow the directions on your installation notes.
Also, you may have to get your kernel development files, if you don't have them:
```
sudo apt-get install linux-restricted-modules-nameofyourkernel
```
*Note. To see the name of your kernel, type "uname -r"

I don't know... maybe those are not the problems... before attempting anything, could you post the output of the compiling command?

---

### Post by icyblue on 2007-02-07
No... I compiled it only from 'home' dir... I also used that 'sudo apt-get' but It's already been upgraded...I get a lot of errors so I can't actually send it.... Mostly, It's like 

"In file:.../kernelname/....sys.h":
No such file or directory...

Is there a way to configure my ethernet card automatically without usin these installtion cd's and compilation stuffs?

---

### Post by Mike_Longbow on 2007-02-07
> **icyblue said:**
> "In file:.../kernelname/....sys.h":
No such file or directory...
That looks like  you don't have the development headers for your kernel... Have you tried with:
```
sudo apt-get install linux-headers-kernelname
```
And also a word of advise, commonly, the standard commands to compile and install something from source are:
```
./configure
sudo make
sudo make install
```
I guess there's something like this on your installation manual, isn't it?

> **icyblue said:**
> Is there a way to configure my ethernet card automatically without usin these installtion cd's and compilation stuffs?
I wish there would... all this compiling stuff is because when you need an specific driver or software, and since there are a lot  of computer architectures, they give you the source code, so you can compile it according to your specific machine... 
But don't worry, you don't have to deal with this everytime you want to install something; as I said, this is only when you got a very specific driver/software, most of the time a single clicks on Synaptic will help you installing whatever you want ;)

---

