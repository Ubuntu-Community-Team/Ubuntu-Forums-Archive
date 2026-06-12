---
title: "How to play mp3s in Amarok"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by milad on 2006-11-28
// Sorry for my poor English


Here's the problem, I installed Amarok on my Ubuntu (Gnome) but it can't play any mp3 file! It asks if I allow it to download mp3 support and then it shows a message saying it has successfully installed it, but it still can't play mp3 files ...

Anyway, it doesn't have any problem with WMA files

I apreciate any help


By the way, what's the most powerful audio player in Linux in your opinion?
I really wish there was something like Foobar2000 in linux.

---

### Post by pay on 2006-11-28
Have a look here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) I really like xmms as a music player because it's lightweight but I use Gentoo and they don't support it anymore so now I use audacious.

---

### Post by nixclusive on 2006-11-28
install extracodecs for xine:

```
sudo apt-get install libxine-extracodecs
```

---

### Post by milad on 2006-11-28
it didn't help :(

milad@milad-desktop:~$ sudo apt-get install libxine-extracodecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxine-extracodecs is already the newest version.
The following packages were automatically installed and are no longer required:
  libgnucrypto-java liblog4j1.2-java libswt3.2-gtk-java libseda-java
  libcommons-cli-java libgtk-jni libcairo-java libbcprov-java libglib-java
  libgtk-java libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
milad@milad-desktop:~$

---

### Post by fhqwhgads on 2006-11-28
I'm a hardcore foobar2000 proponent, and I still use it on my windows box, but I must say that Amarok is far better in most aspects. It's not as lightweight, and the replaygain handling frankly sucks, but I love it dearly all the same. Nothing else comes close unless you want an iTunes clone (Quod Libet), but that navigation method is incredibly painful to me.

---

### Post by zaratustra on 2006-11-28
I'm gentoo&amarok user... I have no trouble with mp3, but no wma could be played... says no suitable demux plugin... what i need for that?

---

### Post by milad on 2006-11-28
Problem Solved! I installed gxine from Sypnatic Package Manager and here it goes

---

### Post by pay on 2006-11-28
@zaratustra  
I think that you need the w32codecs. Try adding USE="win32codecs" to /etc/make.conf```
USE="win32codecs emerge media-libs/xine-lib media-sound/amarok
```but that will only work on x86

---

### Post by zaratustra on 2006-11-29
got xine-lib installed with win32codecs...:/ also, emerging gst-plugins-bad (unmaintained and masked) didn't make any progress
what solved situation is emerging masked version of xine-lib (1.1.3_pre20061119), but thnq for brainstorming anyway

---

### Post by adamkane on 2006-12-05
You need libxine, and you need to disable arts. After you start/stop amarok a couple times, amarok will ask you, if you want to disable arts. Press YES.

---

