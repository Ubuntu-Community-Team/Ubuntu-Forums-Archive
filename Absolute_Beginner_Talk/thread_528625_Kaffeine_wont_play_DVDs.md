---
title: "Kaffeine wont play DVDs"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by dac10 on 2007-08-18
i cant find a previous thread which has my exact problem, or one which i understand what they are saying :s

when i put a DVD in and select play with kaffeine i just get this error messsage;

"No plugin found to handle this resource (dvd:///dev/hda)

10:08:03: xine: couldn't find demux for >dvd:///dev/hda<
10:08:03: xine: found input plugin : DVD Navigator"

im assuming i dont have the correct codecs installed, but which ones do i need and where can i find them? 

thanks,

---

### Post by Perfect Storm on 2007-08-18
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by RomeReactor on 2007-08-18
Hi. You need to add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories; however, read [this first]("https://help.ubuntu.com/community/RestrictedFormats").

If after reading it you still agree to install the packages needed then open a Konsole (I'm not using KDE right now, so I don't rememeber where it is exactly), and enter the following:
```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
```
to add the Medibuntu repositories. Then:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
to fetch the gpg key and bring your package managers' repository information up to date. And lastly:
```
sudo apt-get install libxine1 libxine1-ffmpeg libxine-extracodecs libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4 w32codecs
```

---

### Post by dac10 on 2007-08-18
> **RomeReactor said:**
> Hi. You need to add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories; however, read [this first]("https://help.ubuntu.com/community/RestrictedFormats").

If after reading it you still agree to install the packages needed then open a Konsole (I'm not using KDE right now, so I don't rememeber where it is exactly), and enter the following:
```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
```
to add the Medibuntu repositories. Then:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
to fetch the gpg key and bring your package managers' repository information up to date. And lastly:
```
sudo apt-get install libxine1 libxine1-ffmpeg libxine-extracodecs libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4 w32codecs
```

jeez you guys are unreal! ive got sooooooooo much to learn :P

i struggled on with the stuff in the first reply, but after running your commands its all working perfect now, thanks :)

im going to study what the terminal was saying cause id love to understand this and be able to do it myself. :KS

---

