---
title: "how to recompile the kernal?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-23
Hello, i was wondering if somone can shed me some light on how to recompile the kernel, here is the tutorial i am following:



Compile the kernel module:

Code:

Code:

sudo module-assistant prepare,update 
sudo module-assistant build,install fglrx sudo depmod



Note: You have to recompile the kernel module after each kernel update!

Update the xorg.conf file:

Code:

sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv


it is the guide on Howto: Fglrx 8.26.18 Driver Install (works With Xpress Series Cards Now!)


link is : 
[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

---

### Post by pay on 2006-09-23
Type```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
```

---

### Post by bodhi.zazen on 2006-09-23
Ask yourself, Do I feel lucky. Do ya?

I suggest [-o<

Seriously, this is a major undertaking and can not be answered by me in a short space.

[How to complie kernel](http://ubuntuforums.org/showthread.php?t=56835)

---

### Post by pay on 2006-09-23
I don't think that he wants to compile the entire kernal from source. He probably wants to compile the kernel module so he can install the new ATI driver. If thats the case type```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
```into the terminal.

---

### Post by bodhi.zazen on 2006-09-23
My mistake then #-o

---

### Post by rick_1010 on 2006-09-30
Hi, whenever I try to do anything with fglrx I get the message:

"fglrx, what is fglrx?"

- I've done the updates and uncommented all the repositories, am I missing something?

---

