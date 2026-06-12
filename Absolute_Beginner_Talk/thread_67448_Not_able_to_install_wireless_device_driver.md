---
title: "Not able to install wireless device driver"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by mpr67 on 2005-09-20
I am trying to install my wireless Netgear wg111 usb on Ubuntu. I first installed ndiswrapper and believe I was successful because when I type ndiswrapper -l it tells me that no drivers are installed. I copied my windows xp driver (net111v2.inf) to a folder (called "NG") that I created on my desktop. Unsure of the path, I navigated to my driver file and checked its properties. The path is listed as /home/mike/desktop/NG.
After typing ndiswrapper -i /home/mike/desktop/NG/net111v2.inf I get a message that reads Unable to create directory  /etc/ndiswrapper/net111v2.inf. Make sure you are running as root. 
Any help would be appreciated as I have no clue as to what to try next.
Thanks - Mike

P.S. I hope this isn't a duplicate as I tried posting this before and it disappeared when I tried to do a preview.

---

### Post by katu on 2005-09-20
ndiswrapper needs root priviliges to create a directory in /etc/
try running:
```
sudo ndiswrapper -i /home/mike/desktop/NG/net111v2.inf
``` 
this should ask you for your password. And then you should be set to go.
if I remember right, the next thing to do (after checking if the driver was loaded) should be:
```
sudo modprobe ndiswrapper
```
you can then check if:
```

lsmod | grep ndiswrapper 
```
gives any output. if it does, that's good. You can try the network settings, the wireless device should be there.
cheers,
Katu

---

### Post by mpr67 on 2005-09-20
Katu - Thanks for your help. I think the "sudo" business made the difference. I didn't get it to work right away, but after uninstalling and reinstalling and fiddling with the networking settings, I was finally able to get my downstairs computer to connect to my router and internet. Now I can use it and see how I like (Ubunto)Linux. Thanks again!

---

