---
title: "Problems with synaptic package manager and wine"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by delilahjed44 on 2007-04-21
Hello, well this is starting to be a drag, here is the message I am getting to try and open symaptic package manager,

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I dont have a clue what to do, and I cannot open any of my programs as this is what I have in appications,-system tools-wine software uninstaller, then

wine filer, wine browser-wine helper in accessories, 
I cant right clk and open a program that I want to install with wine now???? and I cant open synaptic package manager to get wine from there, it worked easeier with Ubuntu 6.10 now I have Feisty ??? 

and it is no longer in my selection in automatix because I guess I did download it but its not working???

Sherri

---

### Post by zvacet on 2007-04-21
First try to run command in terminal (programs>accessories>terminal)
```
sudo dpkg --configure -a
```

to resolve problems in synaptic,because  until you have problems with synaptic you are not able to download or install anything.When your synaptic work again then you can look is wine installed or not. My choice will be to install with synaptic,because it is easyest way to do it.

---

### Post by delilahjed44 on 2007-04-21
Ok, hey thanks this did work, wine is working ok, but I will double check it, thanks for the reply, I am a bit frustrated as I have programs I would like to use with my mic as I once did very confortably with windows, so I am trying to get that issue and the kinks worked out, so for nothing.  Thanks for this.

Sherri

---

