---
title: "sharing a drive"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by roscomain on 2007-12-01
Hi all
I hav an XP PC and an iMac. I am thinking of butiny a second hand PC and putting Ubuntu on it. I want to know if I could share the hard  drive on it and useit as a place to back up files from the XP PC and iMac. Is there a problem with FAT 32. Is it easy to share a Drive on Ubuntu?
Apologies in advance for my ignorance!

---

### Post by webjames on 2007-12-01
yes, this is very possible. don't apologize.
windows uses samba file sharing, this is very easy to set up sharing in ubuntu:
right click on a folder and click share folder, very similar to windows.  then it's just a case of dragging and dropping the files from you window computer to the ubuntu one.

hope this helps, there is automated backup solutions if you search the forums you should find more information.

---

### Post by stoodleysnow on 2007-12-01
(clearly this does require you to network your PCs together)
OR you could (for small scale backup) just us a usb key / drive and transfer files with that.:)

---

### Post by fenian on 2007-12-01
I use samb to share files with 4 other computers (2 mac 1 windows 1 linux) on my home network.A good video tutorial can be found [here]("http://www.youtube.com/watch?v=Ad17kma8rNM").

---

### Post by MrFSL on 2007-12-01
I think that Samba is wonderful software and the Samba project in all has had an amazing impact on the Linux world.... That being said I strongly suggest NOT using it. Windows file sharing --- I don't think it is easy to setup in Linux.

I suggest using ssh. An openssh server is easy to install and configure:
```
sudo apt-get install openssh-server
```
Is cross platform, secure,  and can be graphically "mounted" in all three Operating systems:

---

### Post by webjames on 2007-12-02
roscomain, just a thought. you might need to add a samba user if you want to access the shares from windows. to do this:

```
sudo smbpasswd -a YOUR_USERNAME
```

enter a password for your shares
followed by:

```
sudo smbpasswd -e YOUR_USERNAME
```

this enables that account.

this is what i did, hope this helps

---

### Post by roscomain on 2007-12-02
Many thanks for link to video - really helpful.

---

