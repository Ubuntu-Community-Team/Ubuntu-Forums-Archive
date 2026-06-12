---
title: "Install not possible with 640x480. Now what?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by RamonS on 2006-08-11
Hi,
after booting up from the Ubuntu CD the live version appears fine, but the screen resolution is only at 640x480. That isn't so much the problem except that when I start the Install application the windows are too big and cannot be resized. I also cannot change the resolution.

Any advice on how to force a higher resolution or how to shrink the window size of the Installer application?

Thank you very much in advance.

---

### Post by djsroknrol on 2006-08-11
What's the specs on your video card?..generally, I've found that anything below 32MB video ram will not go above 640X480....might be time for a new card??

---

### Post by RamonS on 2006-08-11
No idea, it was some Matrox PCI card. I put a cheesy ATI AGP in, seems as that one is more liked by Ubuntu, although at 1xAGP speed the performance is probably the same as with the PCI card. Anyhow, seems that the most obvious approach that you suggested works out. Thanks.

---

### Post by chadk on 2006-08-11
I had the same problem with Dapper and I have an ATI x800 with 256mb.  Locked me into 640x480 and I couldn't see the buttons on the installation menus.  I had to use the alternate install CD and do it in TEXT mode. -- problem with that was, it still didn't work right for me.  The video never installed right.  I had to install Breezy which worked great, then dist-upgrade from there to Dapper.

---

### Post by ranti on 2006-08-11
Hi all,

I am having the same problem.  How do I find out the information about the graphic card and what kind of "phrase" I should look for to figure out the model/spec and video ram?  

My machine was used for Windows 2000 before, and I am very sure the screen resolution can go more than 800x600 under Windows.

@chadk: maybe I should use your work around?


thanks,
ranti.

---

### Post by djsroknrol on 2006-08-11
> **RamonS said:**
> No idea, it was some Matrox PCI card. I put a cheesy ATI AGP in, seems as that one is more liked by Ubuntu, although at 1xAGP speed the performance is probably the same as with the PCI card. Anyhow, seems that the most obvious approach that you suggested works out. Thanks.

Glad I could help out...good luck...

---

### Post by Ragazzo on 2006-08-11
This worked for me: Start the terminal in Applications->Accessories->Terminal. Write "sudo dpkg-reconfigure xserver-xorg". Use default values until you come to a screen where you can select resolutions and check what you want. Press Ctrl+Alt+Backspace to restart the GUI. Now you should be able to change the resolution in System->Preferences->Screen Resolution.

---

### Post by Talon2 on 2006-08-15
Same problem here (6.06).  To accomplish the install I had to reboot the cd and select the second item in the initial menu (I forget the exact terminology but it was something like: Install using safe video mode).  That is probably using VESA support instead of mga support.

Video card is a Matrox g550.

Once installed I was able to "dpkg-reconfigure xserver-xorg" and set things up properly.

There are really some rough edges concerning getting video setup.  Not really ready for Joe Average IMHO.

---

