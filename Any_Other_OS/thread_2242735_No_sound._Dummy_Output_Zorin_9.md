---
title: "No sound. Dummy Output Zorin 9"
date: 2014-09-03
forum: Any Other OS
---

### Post by miguelkshaw on 2014-09-03
I wanted to try Linux for the first time. I installed Ubuntu 14.04 in a VM with Win 8 as host. I got everything working except for sound. I tried some of the fixes and got nowhere. 
I then uninstalled Ubuntu and installed Zorin 9 to see if there was any difference... There wasn't.

It seems that my soundcard isn't recognized and Dummy Output appears in Sound Settings.

I made sure nothing obvious was muted.

```
mike@Bebbanburg-VM:~$ aplay -l
aplay: device_list:268: no soundcards found...
mike@Bebbanburg-VM:~$ 

```

```
mike@Bebbanburg-VM:~$ alsamixer
cannot open mixer: No such file or directory

```

I'm using an Acer aspire V3 laptop

Any help much appreciated. I really want to give Linux a shot.

---

