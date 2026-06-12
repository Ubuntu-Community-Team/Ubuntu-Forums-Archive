---
title: "Network file access - Ubuntu / Windows"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by e_james on 2006-07-27
Toshiba Tecra S1 and Ubuntu 6.06 in a part wired, part wireless network of 4 computers using a wireless adsl router.

I think I am missing something obvious but I can't find a way to access my files on other computers when this one is running ubuntu. In my limited linux experience each distribution does it differently. How does ubuntu do it? I can get as far as a window for "Windows Network" but there is nothing in it.

---

### Post by richardward101 on 2006-07-27
try running:
```
nautilus smb://name_of_another_pc
```
from a terminal, see what happens.
BTW, the network icon does take AGES to load (at least on my system) so make sure you're giving it enough chance to load.

---

### Post by e_james on 2006-07-27
Result - error message "The folder contents could not be displayed".

I think there may be a permissions issue in here somewhere.

---

### Post by richardward101 on 2006-07-27
hmmm, could be permissions, one way to find out is to put sudo in front of the nautilus command above. If it still doesn't work, its something else.

try:
```
smbtree
```
leave the password blank. See what happens.

also try pinging the machines to see that they're actually there.

---

### Post by GStubbs43 on 2006-07-27
Make sure you typed the computer name in correctly, I can connect to any of the computers, but if I type in a fake name, it says the same thing that you said. Right click on my computer on the Windows computerr and click properties, then computer name tab and make sure that is the name you enter where it says computer name:

Sorry if that is confusing.... :)

---

### Post by e_james on 2006-07-27
Thanks for the advice guys but, since my last message, I have managed to narrow the problem down a bit. It's something to do with the router and ubuntu and wireless. it has come to my attention before now that there is a distinction between internet and network. On several occasions the router has allowed network but not internet. This one is the other way round. Using the wireless adapter, I can connect to the internet but not to the network. I also can't logon to the router. Using a wired connection everything works including the network file access. More investigation required. I will let you know what I find.

Edit
Problem solved. My own stupid fault. I have been experimenting with different routers because I have been having problems with disconnections of a few seconds and I set all the network adapters to fixed IP addresses. When working in ubuntu the wireless IP duplicated another in use but the wired IP did not. IP changed. Problem resolved. Thanks again for your input.

---

### Post by richardward101 on 2006-07-28
heh, occams razor. Although we'd mock people for it, hands up those who haven't at some time tried for ages to fix something and then realised it wasn't plugged in/switched on etc etc. I know i've done it more than a few times :smile:

---

