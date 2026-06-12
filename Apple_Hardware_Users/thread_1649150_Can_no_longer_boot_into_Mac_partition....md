---
title: "Can no longer boot into Mac partition..."
date: 2010-12-19
forum: Apple Hardware Users
---

### Post by Koko98 on 2010-12-19
So yesterday, I installed ubuntu onto a 20gb partition I created on my Macbook pro. Installation went great, but now I can no longer boot into my Mac partition. When booting up if I hold the option key, all that shows up is a lock icon with a white area below which I can type things into. Nothing happens if I do, and there are not hdd showing. The Mac partition is an option on my grub menu, however it hangs when selected and does not end up loading.

Any help?

Note: I am on vacation from school at the moment and my live cds for Mac are in my dorm.

---

### Post by Koko98 on 2010-12-20
Anybody? I have looked everywhere but haven't found anything particularly helpful. I've got a report coming up soon and I need to try and get this fixed as my notes, etc. are on my Mac.

---

### Post by arabis on 2010-12-21
To install Ubuntu on a Mac, you have to follow a special procedure beginning by this page:

[https://help.ubuntu.com/community/MacBookPro]("https://help.ubuntu.com/community/MacBookPro")

Depending of your Macbook pro version, Grub won't be able to boot into osx and it may be necessary to use refit. If you would have your osx dvd, you can boot with it and recover your booting hability. See this link:

[http://hints.macworld.com/article.php?story=20091111185717745]("http://hints.macworld.com/article.php?story=20091111185717745")

Can you boot into Ubuntu? From there you can access your datas in your osx partition. Also,maybe you can use refit from a usbstick to boot into osx:

[http://refit.sourceforge.net/doc/c1s1_install.html]("http://refit.sourceforge.net/doc/c1s1_install.html")

Hope this helps ;)

---

### Post by Koko98 on 2010-12-21
I am going to try the usb thing. I can boot into Ubuntu fine, but I can't seem to access my mac drive. I mount it and can open it, but all the folders show up as empty when I open them.

---

### Post by yugnip on 2010-12-21
Right click the folders on the mac partition and choose 'open as admin'.

---

### Post by Koko98 on 2011-01-03
Well now I'm back on campus and have my Mac OS X install dvd, but for some reason it can't be booted from and instead I get loaded straight into grub.

How do I boot from the cd?

---

### Post by Koko98 on 2011-01-05
Well I can boot from my ubuntu live cd, however my Mac OS X install dvd as well as my Snow Leopard dvd both remain unbootable... even in a virtual machine running on my computer.

---

### Post by arabis on 2011-01-06
Did you try to press "c" when starting your macbook with your livecd of osx?

---

### Post by Koko98 on 2011-01-06
I've tried holding "c" down and it works with my ubuntu live cd, but not my Mac OS X dvd. I've also tried holding down the option key to select boot drives, but instead get a picture of a lock with a password bar underneath (typing "apple" doesn't work).

---

### Post by arabis on 2011-01-08
Maybe you can try to reset your PRAM:

[http://support.apple.com/kb/ht1379]("http://support.apple.com/kb/ht1379")

---

### Post by Koko98 on 2011-01-08
I tried both of those at startup. I was confronted with the initial grey colored screen and then it went straight into Grub. Oh dear.

---

### Post by Koko98 on 2011-01-14
Is there any reason it won't read ONLY my Mac DVDs? They are all legal original copies...

---

### Post by ste.sancri on 2011-01-14
Did you put the Mac OS X install DVD?

Try to insert the other one, is called "Install Applications" if I can remember right.

As you can read over that dvd (on the left of the cd) you can perform an hardware test pressing the "D" button while booting.

Here's the apple's support page

[http://support.apple.com/kb/ht1509](http://support.apple.com/kb/ht1509)

---

### Post by teejmya on 2011-01-14
> **Koko98 said:**
> When booting up if I hold the option key, all that shows up is a lock icon with a white area below which I can type things into. Nothing happens if I do, and there are not hdd showing. 

The lock and text box you see is your firmware password. They're installed using the Mac OS X Install Disc. So either you made one and forgot it, or maybe if you bought it used, it was from the previous owner. Try typing passwords that you use regularly into the box and see if it gives you the boot menu.

---

### Post by teejmya on 2011-01-14
> **Koko98 said:**
> When booting up if I hold the option key, all that shows up is a lock icon with a white area below which I can type things into. Nothing happens if I do, and there are not hdd showing. 

The lock and text box you see is your firmware password. They're installed using the Mac OS X Install Disc. So either you made one and forgot it, or maybe if you bought it used, it was from the previous owner. Try typing passwords that you use regularly into the box and see if it gives you the boot menu.

---

### Post by Koko98 on 2011-01-19
Holding down the D button didn't do much help for me, as nothing happened (it seems to only be with Mac DVDs). I got the computer from my grandfather, so I'll see if he had any passwords setup that I don't know.

---

### Post by uced on 2011-02-09
You can bypass this firmware password:

- open the Mac,
- remove one RAM module,
- close the Mac
- boot and zap PRAM,

You should be able to boot MacOS

- shut down,
- put the RAM back in place.

---

