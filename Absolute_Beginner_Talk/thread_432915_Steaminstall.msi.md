---
title: "Steaminstall.msi"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by PricklySponge on 2007-05-04
Hello, i'm trying to install steam via wine and it doesn't appear to be working. The steaminstall program is located in my /home/makee folder.

This is what is happening.

makee@makee-desktop:~$ /home/makee wine msiexec /i steaminstall.msi
bash: /home/makee: is a directory

After that wine, and steam dont initialize. 
What am I doing wrong?

Thanks,
PricklySponge

---

### Post by uberamd on 2007-05-04
> **PricklySponge said:**
> Hello, i'm trying to install steam via wine and it doesn't appear to be working. The steaminstall program is located in my /home/makee folder.

This is what is happening.

makee@makee-desktop:~$ /home/makee wine msiexec /i steaminstall.msi
bash: /home/makee: is a directory

What am I doing wrong?

Thanks,
PricklySponge

Wouldnt it just be along the lines of: **wine /home/makee/steaminstall.msi**

The /home/makee wine is a invalid command from what I can see.

---

### Post by PricklySponge on 2007-05-04
I'm following the commands from this link
[http://www.winehq.com/pipermail/wine-users/2005-December/020055.html]("http://www.winehq.com/pipermail/wine-users/2005-December/020055.html")


And this is what I got from the code you suggested:

makee@makee-desktop:~$ wine /home/makee/steaminstall.msi
wine: could not load L"H:\\steaminstall.msi": Bad EXE format for 

I'm starting to think it might be a wine configuration issue. Any ideas?

---

### Post by PricklySponge on 2007-05-04
edit: woah, it seems to be installing now. Thanks, guys :)

---

### Post by Terl on 2007-05-04
Excellent.  I did find this link:  [Installing Counterstrike]("https://help.ubuntu.com/community/CounterStrike?highlight=%28steam%29") in which there is a link to get a steam.exe file.  

Hope it works for you.

---

