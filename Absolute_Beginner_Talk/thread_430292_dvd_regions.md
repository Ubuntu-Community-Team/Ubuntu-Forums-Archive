---
title: "dvd regions?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by crav on 2007-05-02
Running 7.4 and using VLC [same problem in other viewers, too] I can't play any of my bought and paid for DVDs. They're all region 1. I can, however, play my burned, region free discs. Any possible solutions?

Also: Ironic that when I pay the MPAA they DRM me until I can't use the product. When I don't pay them, everything works great!

---

### Post by simonn on 2007-05-02
You can install libdvdcss, NOTE: this may be illegal where you live. If you search these forums on this you will get more information.

---

### Post by Sef on 2007-05-02
> You can install libdvdcss, NOTE: this may be illegal where you live. If you search these forums on this you will get more information.

Read [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by crav on 2007-05-02
Every way I've tried to install dvdlibcss2 has not be able to find the package

---

### Post by aidanr on 2007-05-02
that's because it's spelled libdvdcss2 not dvdlibcss2 :wink:

also read [this]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#head-780db298b62beea3e785ce27b68ec2f52d443515")

---

### Post by crav on 2007-05-02
Here's the error I get.
```
crav@AlphaCrav:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

```

---

### Post by aidanr on 2007-05-03
gksudo software-properties-gtk # (make sure universe is checked and the medibuntu repository is added in the third-party software tab)
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install libdvdcss2

---

### Post by andrew.46 on 2007-05-05
Hi,

 If you are a little fussy about adding repositories the [Medibuntu page]("https://help.ubuntu.com/community/Medibuntu") has details about adding individual packages as well. I added  libdvdcss2 this way rather than add Medibuntu to my sources list:

```
wget http://medibuntu.sos-sts.com/repo/pool/feisty/non-free/i386/w32codecs_20061022-0medibuntu1+build1_i386.deb
sudo dpkg -i w32codecs_20061022-0medibuntu1+build1_i386.deb
```

 This is for the i386 package only.

         Andrew

---

### Post by tellos on 2007-05-05
Hello

Ok i'm doing as you said (downloading the package with the terminal), but it's very slow... between 3-5 k/s. is that normal???

Thank you

---

### Post by meng on 2007-05-05
Repository downloads can be slow sometimes. If it's downloading at all, count that as a win.

---

### Post by tellos on 2007-05-06
Ok now i can read dvds from any region with VLC, but not with Totem MoviePlayer.
not that i'm using this player, I just want to know if someone has any idea?
It tells me something about plug-ins, should i have a look in the synaptic manager? 

thank you!

---

### Post by udirmusa on 2007-07-09
None of the above works, More suggestions...
Still looking for the very elusive libdvdcss2 ....

---

