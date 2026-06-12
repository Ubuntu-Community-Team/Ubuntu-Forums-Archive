---
title: "KDE splash screen"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by zekopeko on 2006-07-16
so i installed kubuntu-desktop package just to see whats the diffrence.

kubuntu replaced my ubuntu splash screen so how do i return it?

i don't want to uninstall kubuntu-desktop because i like some of the programs that came with it.

thnx for any help.

---

### Post by Jucato on 2006-07-16
Simple question first:
Which splash screen are you talking about?
1. The one that you immediately see upon booting your computer, the one with the Ubuntu/Kubuntu name, and lots of scrolling text?

or

2. The splash screen you see after typing in your username and password, where you see icons being displayed as various components are "loading"?


If it's #1, you can try this. 
- In a terminal, type in
```
sudo update-alternatives --config usplash-artwork.so
```
- You will be given a list of existing bootsplash screens. The default (the one with *) will probably be  /usr/lib/usplash/kubuntu-splash.so.
- Type in the number of the line with */usr/lib/usplash/usplash-default.so*. This is the brown Ubuntu boostplash screen.

Hope that helps.

---

### Post by zekopeko on 2006-07-16
it was number 1. thnx!

---

### Post by Hillbilly Tilley on 2006-07-17
Just wondering what the + on number 2 was for?

Thanx

---

### Post by Hillbilly Tilley on 2006-07-18
My splash screen did not change.  I changed the default (*) to 1, which is the unbuntu splash, there was a + still on the 2 kubuntu screen.  After a reboot I still have the kubuntu splash.  Any idea how to change back to the unbuntu splash?

---

### Post by zekopeko on 2006-07-18
it seam that my problem didn't go away. 

when ubuntu loads it shows the kubuntu splash screen , but when i log out it logs with the ubuntu splash screen. very strange.

P.S. by splash screen i mean loading of drivers and mounting filesystem, not logging on to my desktop from the login screen

---

### Post by aysiu on 2006-07-18
These instructions are a bit more comprehensive and may help you:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

---

### Post by Jucato on 2006-07-18
I didn't know about reconfiguring the linux-image for it to take effect... :(

---

### Post by nosam on 2006-07-26
> **zekopeko said:**
> it seam that my problem didn't go away. 

when ubuntu loads it shows the kubuntu splash screen , but when i log out it logs with the ubuntu splash screen. very strange.

P.S. by splash screen i mean loading of drivers and mounting filesystem, not logging on to my desktop from the login screen

I have the exact same problem.

I tried:
```
sudo update-alternatives --config usplash-artwork.so
```

And got:
```
matt@matt:~$ sudo update-alternatives --config usplash-artwork.so

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.
matt@matt:~$

```

Any suggestions?  Thanks.

---

