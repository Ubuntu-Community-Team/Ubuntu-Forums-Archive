---
title: "Ubuntu does not recognize my WMP300N adaptor"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-07-23
Hi,
I needed to get a stronger signal for my desktop and so I bought the Linksys WMP300N wireless adaptor. In Vista, it works well enough, but Ubuntu Feisty does not even recognize the hardware.

I searched and read former posts on this before I bought it and one poster said she did 3 restarts and voila it was there. I tried that and it has still not shown up.

I did read another account where it installed easily in Ubuntu, although the person did not describe how.

I've been trying Ndiswrapper and I have the INF file "Bcmwl5.inf" but when I try to install it thru Ndiswrapper, nothing happens.  ( I use the 'Windows Wireless Drivers' GUI Ndiswrapper-related program from Add/Remove). 

I appreciate any help or assistance. I've worked hard to get Ubuntu in the zone - I just bought a new Nvidia 7600 GS video card and that was a great purchase for Ubuntu and it works well in Vista too.

Now if I can get this going, Ubuntu will be up to speed.

Many Thanks for any assistance, Frank B.

---

### Post by Brightbelt on 2007-07-23
OK, I'm replying to myself both to document what I've tried so far and maybe a bump as well ;). 

There is a bcm4306 ndiswrapper installation guide - See [HTML]http://ubuntuforums.org/showthread.php?t=340689[/HTML] - that is supposed to help with installing the WMP300N, so I followed it. 

I  had trouble with this part where you're supposed to comment out any reference to eth1 using this file:
```
sudo nano /etc/iftab
```

and on this file as well:
```
sudo nano /etc/network/interfaces
```

But I got stuck on these files because there was no way to "save" the changed files. I know that sounds crazy and adding an '#' is certainly easy enough, but I found no way to save the changes, other than pressing enter which didn't seem to do anything.

But I followed the rest of the guide and it has not worked to solve my problem. Ubuntu still does not recognize my WMP300N at all.

If someone could offer any guidance, I'd be grateful. I'm worried at this point, having tried so many things, that maybe I've messed up some files for good. I hope not.

I appreciate any help on this - Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-07-24
Bump

---

### Post by macleod199 on 2007-07-27
Ctrl-O should write the changes.  The stuff at the bottom of the screen in nano tells you which letter to press with CTRL to do the various functions.

---

### Post by Brightbelt on 2007-07-28
Yes I saw the index at the bottom, but I could swear it gave no information about using those keys in conjunction with the Control button.

Thanks for the tip,
Frank

---

