---
title: "Black screen on Ubuntu 7.10 - worked fine on Live-CD"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by akrty on 2008-02-17
Hello guys.

I recently installed Ubuntu 7.10 in my laptop (Targa 826W MT34 - [http://www.targa.co.uk/index.jsp?SID=0&NAV=236&DOC=&PAGE=1224&PCAT=2&PROD=218&PTUBE=12&PARAMS=undefined&PARAMS2=undefined&SPCAREA=undefined](http://www.targa.co.uk/index.jsp?SID=0&NAV=236&DOC=&PAGE=1224&PCAT=2&PROD=218&PTUBE=12&PARAMS=undefined&PARAMS2=undefined&SPCAREA=undefined)). Well, I had no problems running the Live CD and during the installation. However, everytime I try to load the OS I get a black screen. I don't even see the Ubuntu logo and the loading bar at the startup... 

Anybody helps me?
Thanks :popcorn:

---

### Post by jan quark on 2008-02-17
this happened to me once

then I installed ubuntu with the alternate CD and this never ever happened to me again

but wait for someone else, pehaps there is an easier solution than a new install with the alternate CD

but for the future I would use the alternate CD

---

### Post by tangibleorange on 2008-02-17
Have you tried booting into recovery mode? It should be the second option on the GRUB list when you first start your computer.

---

### Post by Jimcanoa on 2008-02-17
Try removing the boot option "splash" to see where it fails.

To do so go to GRUB menu (press 'ESC' if it prompts you to do so), and select the entry you want to boot, instead of pressing enter, press 'e' to edit the entry... you'll see a couple of lines, one of them starts with kernel ... select that one and press 'e' again to edit it. You'll see a long line with options, it says 'splash' somewhere, manually delete it, then press 'ENTER' to accept, and 'b' to boot.

If this works for you I'll let you know how to automatically boot without the splash option, if you don't know how to.

good luck

**EDIT:
remove quiet too while you are at it... quiet and splah.

---

### Post by akrty on 2008-02-17
> **Jimcanoa said:**
> Try removing the boot option "splash" to see where it fails.

To do so go to GRUB menu (press 'ESC' if it prompts you to do so), and select the entry you want to boot, instead of pressing enter, press 'e' to edit the entry... you'll see a couple of lines, one of them starts with kernel ... select that one and press 'e' again to edit it. You'll see a long line with options, it says 'splash' somewhere, manually delete it, then press 'ENTER' to accept, and 'b' to boot.

If this works for you I'll let you know how to automatically boot without the splash option, if you don't know how to.

good luck

**EDIT:
remove quiet too while you are at it... quiet and splah.

Yes, it worked (thanks :D). But is there a way to hide all those command lines at the startup?

---

### Post by Jimcanoa on 2008-02-17
Glad it worked!

yes, there are things you can do to get the splash screen back and get it to load... Try following this thread: [http://ubuntuforums.org/showthread.php?t=579684](http://ubuntuforums.org/showthread.php?t=579684) . 

I personally hate the splash screen, I like to see how it boots up etc, so I wouldn't be bothered, but follow the above thread if you can't live without the splash screen!

by the way, next time you reboot it will try to boot with the splash screen again and it won't succeed (maybe after a long time). So if you want to fix this you have to remove 'quiet' and 'splash' from /boot/grub/menu.lst

to do so:

1. create a backup copy:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
2. open gedit, look for the words 'splash' and 'screen' in the document, delete them and save the file.
```
gksudo gedit /boot/grub/menu.lst
```
--or--
if you want to remove quiet and splash from the command line do this (no need to open gedit) (don't forget to do a bakcup first, step no.1):
```
sudo sed -i 's/quiet//g' /boot/grub/menu.lst
sudo sed -i 's/splash//g' /boot/grub/menu.lst
```

---

### Post by akrty on 2008-02-17
It's working fine now. Thnks!

---

### Post by ruckstande on 2008-02-17
I actually am having the same issue and it takes about 3 1/2- 4 minutes to get to the logon screen. Might this be related at all?

---

### Post by tangibleorange on 2008-02-17
> **ruckstande said:**
> I actually am having the same issue and it takes about 3 1/2- 4 minutes to get to the logon screen. Might this be related at all?
Did you try the fix detailed above?

---

### Post by Jimcanoa on 2008-02-17
Absolutely! Try removing quiet and splash from the boot options in the grub menu, just like I described in my first post. Chances are it will bootup much quicker... if that's the case, either remove completely quiet and splash from /boot/grub/menu.lst or try and setup usplash for your computer by following the thread I mentioned above...

---

### Post by ruckstande on 2008-02-17
> **Jimcanoa said:**
> Absolutely! Try removing quiet and splash from the boot options in the grub menu, just like I described in my first post. Chances are it will bootup much quicker... if that's the case, either remove completely quiet and splash from /boot/grub/menu.lst or try and setup usplash for your computer by following the thread I mentioned above...

I will try the other method next. I removed the quiet and splash from the menu but it made no difference.

---

### Post by tangibleorange on 2008-02-17
Yeah I haven't looked at that thread but it's probably something like editing your usplash file:

```
sudo gedit /etc/usplash.conf
```

and set it to the resolution of your screen.

---

### Post by ruckstande on 2008-02-17
Thanks, I tried one of the methods mentioned in the other thread and now it boots up in under a minute.

---

