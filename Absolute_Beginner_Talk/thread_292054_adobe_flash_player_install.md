---
title: "adobe flash player install"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by albert 12 on 2006-11-03
I have used Opera browser in Windows for some years now, so I downloaded and installed it in Ubuntu.
It says that I need Adobe flash player installed, I have downloaded the targz file, but I need some instructions on how to install it, please keep them simple as I dint even now what a tar gz file is.

---

### Post by justifier on 2006-11-03
double click on the file, which should open archive manager, click on the file and click extract. once the file has been extracted exit archive manager. next open terminal you do this by clicking applications > acessories > terminal in terminal type 

cd <insert path to and directory extracted here (minus the <>)>

next type in terminal

./install<press tab>

follow the instructions

reopen opera

---

### Post by Tamil on 2006-11-03
Extract contents of downloaded file.

In terminal go to extracted folder and type ```
sudo ./flashplayer-installer
``` and answer the questions and it will ask for path to install type ```
/usr/lib/opera
```

---

### Post by albert 12 on 2006-11-03
Sorry to be so thick how do I find where it has been extracted to.

---

### Post by Tamil on 2006-11-03
> **albert 12 said:**
> Sorry to be so thick how do I find where it has been extracted to.Right click the file and extract and it will create new folder in current folder and extract files.

---

### Post by doobit on 2006-11-03
> **albert 12 said:**
> Sorry to be so thick how do I find where it has been extracted to.

You can select where to extract it to. I usually put it in my /home folder which is on a separate partition. That way I don't need to download it again everytime I upgrade.

---

### Post by jaywhy13 on 2006-11-03
Just a tip.... in case people upgrade to Firefox 2.0 and you find that you don't have sound. Ensure that the libflashplayer.so file is copied in .mozilla/plugins folder and <firefoxInstall>/plugins/ folder and copy it to /usr/share/firefox/plugins/ as well if ur not sure about it.

---

