---
title: "[SOLVED] DVD Issues"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Lorac1949 on 2007-12-24
I tried to play a DVD and got a message in Totem Movie Player 2.20.0 that said I needed to add the plugins. After going through Synaptic it appears I have all of them.

At one of the forums, someone suggested installing RealPlayer.  I went through the download process for RealPlayer at this site:

[http://www.real.com/linux/](http://www.real.com/linux/)

I couldn't open the BIN file on my desktop so I went through the RealPlayer web site and found the following info:

Question
I cannot install the RealPlayer for Linux BIN file.
Answer
Before attempting to extract/install RealPlayer from the RealPlayerGOLD.bin file, you need to do the following:

chmod +x RealPlayerGOLD.bin

This marks the file as an executable file and is needed before you can attempt to extract the file.

The BIN file I downloaded was RealPlayer10GOLD.bin and I typed that in instead of the text above. However, I got the following message in Terminal:

chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory

I have the 128MB NVDIA GeForce 8400M GS video card.

Any assistance in getting DVDs to play would be appreciated.

---

### Post by taurus on 2007-12-24
Try installing the ubuntu-restricted-extras package.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

p.s.  And why do you have to install RealPlayer if you want to play DVD?  Also, make sure you are in the same directory that you have saved the RealPlayer10GOLD.bin before you try to change the permissions.

---

### Post by Lorac1949 on 2007-12-25
> **taurus said:**
> Try installing the ubuntu-restricted-extras package.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

p.s.  And why do you have to install RealPlayer if you want to play DVD?  Also, make sure you are in the same directory that you have saved the RealPlayer10GOLD.bin before you try to change the permissions.

Thank you, taurus.  The information from the RestrictedFormats was the ticket.  I got sidetracked by one lister's suggestion to install RealPlayer.  Now that I've had a successful installation of libdvdcss2, I don't need RealPlayer and will remove its BIN file.

---

