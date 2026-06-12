---
title: "Problem installing firefox with Mint"
date: 2012-08-22
forum: Any Other OS
---

### Post by tc101 on 2012-08-22
I hope it is OK to ask Mint questions here.  If not, please tell me where I should ask.

I installed the new Mint Cinnamon.  It has firefox 12 and I wanted 14, so I opened the software manager and uninstalled it.   Now I can not install.  I hit the install button and it asks for my password but then does nothing.  Same thing with trying to install Opera and Filezilla.  It did let me install a chess game, so the problem is not with all installs.

---

### Post by tc101 on 2012-08-22
I was able to download firefox from the firefox site, but I don't know how to install it, and anyway, that does not solve the big problem of being unable to install lots of stuff in this version of Mint.

---

### Post by vasa1 on 2012-08-22
There's the other distro section.
There's also the [Mint forum]("http://forums.linuxmint.com/"). I'm pretty surprised that that isn't your first choice for asking Mint-related questions.

---

### Post by NikTh on 2012-08-22
> **vasa1 said:**
> There's the other distro section.
There's also the [Mint forum]("http://forums.linuxmint.com/"). I'm pretty surprised that that isn't your first choice for asking Mint-related questions.
+1 

Also I think that the latest Mint (13) Cinnamon has the Firefox 14 by default. And if is not then with an update the  newest Firefox (and other packages) would installed . 
All steps you mentioned are not necessary. Linux mint follows Ubuntu , is an Ubuntu-based distribution so, same packages  , same kernel , difference is only in desktop environment and some packages and extensions developed by mint developers. 
Thanks

---

### Post by Perfect Storm on 2012-08-22
Moved to Other OS/Distro Talk.

---

### Post by tc101 on 2012-08-23
I did a fresh install.  I went to this webpage

[http://www.linuxmint.com/edition.php?id=103](http://www.linuxmint.com/edition.php?id=103)

and downloaded Mint 13 Mate 32 bit to a DVD.  I used the link to James Madison University to get it.

I installed it on a fresh hard drive.  I opened software manager and tried to install opera. It asked for my password but never installed anything.

Same as before I can install games and tools, but not opera.

It has firefox version 12, not 14.  I don't see any way to upgrade it without removing and reinstalling, which I don't want to do since last time I was not able to reinstall.

---

### Post by synaptix on 2012-08-23
Firefox will be updated via Update Manager in Mint just as it is done in Ubuntu also.

---

### Post by NikTh on 2012-08-23
> **synaptix said:**
> Firefox will be updated via Update Manager in Mint just as it is done in Ubuntu also.

Exactly . 

Ok , maybe I am not remember correctly what version of Firefox is in Linux Mint by  default  , but if you Update your system , then all packages , including Firefox will be updated. 

Just open a terminal and 
```
sudo apt-get update 
sudo apt-get dist-upgrade
``` 
and about Opera when you update your system with above commands , try to install it again.
Thank you.

---

### Post by synaptix on 2012-08-23
> **NikTh said:**
> not remember correctly what version of Firefox is in Linux Mint by  default

Default from my Mint 13 install is Firefox 12 which was promptly updated via Update Manager to Firefox 14.0.1. :)

---

### Post by tc101 on 2012-08-23
Great.  Thanks for your help.  I'll run update manager now.

---

### Post by tc101 on 2012-08-24
Everything is good now.  I just needed to run update manager.  Now I am going to reinstall Mint Cinnamon, run update manager on it, and see if like Mate or Cinnamon better.

Thanks again.

---

### Post by rewyllys on 2012-08-26
> **tc101 said:**
> Everything is good now.  I just needed to run update manager.  Now I am going to reinstall Mint Cinnamon, run update manager on it, and see if like Mate or Cinnamon better.

Thanks again.
Have you made a decision between Mate and Cinnamon yet?  

Personally, I like most of the features of both these DEs, but I've chosen to use Cinnamon because I think it has more promise for the long term.  (But that's just my guess.)

---

### Post by tc101 on 2012-08-26
> Have you made a decision between Mate and Cinnamon yet? 

I like the Cinnamon interface better.  I also tried Xubuntu but I didn't like it as much as Cinnamon.  

Since I am switching to something I will probably stick with for 2 years until the next LTS, I want to take my time and look at what's out there.  I'm not going to try every distro, but I will look at a few more.  What else would you suggest?

---

### Post by madmax75 on 2012-08-29
Regarding the Software Manager in Mint 13...

I've had some trouble with it. It seems to be somewhat buggy - when I installed some programs through it, the bar always got stuck around 16%, and it never told me if the installation actually worked or not, it just sort of... froze. I had to search the installed programs through the menus to see if they really were there.

Synaptic package manager on the other hand works perfectly as far as I can tell. I tend to avoid the Software Manager.

EDIT:

I'm using the MATE desktop environment BTW - I have no experience on Cinnamon. MATE is pretty similar to the classic nome desktop environment. The only gripe I have about it that it has a tendency to freeze up somewhat when I copy large amounts of files to USB sticks. It never crashes, but the freezing up is a bit annoying...

---

### Post by mamamia88 on 2012-08-29
> **tc101 said:**
> I was able to download firefox from the firefox site, but I don't know how to install it, and anyway, that does not solve the big problem of being unable to install lots of stuff in this version of Mint.

you could extract it to your home directory then create a launcher to executable contained within on your desktop or something.

---

