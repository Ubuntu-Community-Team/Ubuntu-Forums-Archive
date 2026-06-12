---
title: "iPod Nano"
date: 2008-08-05
forum: Apple Hardware Users
---

### Post by abrazafi on 2008-08-05
Hi,

Using Kubuntu 7.10 and I'd like to download songs/photos into
it. Question's:

1- what kind of software should I use, like iTune equivalent
on kubuntu ?

2- Tried to upload some songs and the iPod ddoesn't recognize
my new MP3.

Any help would be apreciated.

Thanks,
Abdon.

---

### Post by y@w on 2008-08-05
I tried connecting my iPod to my Ubuntu box some time ago.. I ended up having to plug the iPod into my Mac and let it wipe it and start over. I haven't tried it in some time, so I can't vouch for how it works now.. But I know you can iTunes under Wine. I've used Wine-Doors to install lots of Windows apps in Ubuntu. It'd be worth a shot.. and kinda fun ;)

---

### Post by sy1 on 2008-08-06
Hi abrazafi,

You need to check into the latest version of Brasero at GetDeb.net
:)

---

### Post by pluviosity on 2008-08-06
I have an iPod 5G that works very well with Kubuntu.  Depending on how new your Nano is, you can use either Amarok or gtkpod to sync music.  Amarok should already be on your computer with Kubuntu, but for gtkpod:

```
sudo apt-get install gtkpod-aac
```

gtkpod-aac allows your to also sync unprotected AACs in addition to MP3s you may have, but you can also install the vanilla version, gtkpod.

Newer iPods require you to install a newer version of libgpod.  Also, attempting to sync without the newer libgpod could cause you to lose data from you iPod, so check [here]("http://amarok.kde.org/wiki/Media_Device:IPod") first.

---

