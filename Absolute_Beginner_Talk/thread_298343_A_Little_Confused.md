---
title: "A Little Confused"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by guitarist549 on 2006-11-12
Alright, I'm trying to get the stamina/speed switch working on my vaio... I am told to do this:

To use the Stamina/Speed switch, John Lathouwers (email) has written a little script to switch from one xorg.conf to another depending on the video chipset used. He uses two xorg.conf files in /etc/X11: xorg.conf.stamina and xorg.conf.speed. You then have to create a small script in /etc/init.d (called xorg_conf) with the following content:
VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then
cp -f /etc/X11/xorg.conf.speed /etc/X11/xorg.conf
else
cp -f /etc/X11/xorg.conf.stamina /etc/X11/xorg.conf
fi

Soft linking the script into rc2.d as S12xorg_conf will copy the correct xorg.conf file into place before X starts.

I understand the part about editing xorg, but what about the second part, that talks about softlinking?

---

### Post by christhemonkey on 2006-11-12
You need to make a soft link, also known as a symlink.

The command you need to use is ln, like this:
```
ln [OPTION]... [-T] TARGET LINK_NAME 
```

So for your example:
```
sudo ln -s /etc/init.d/xorg_conf /etc/rc2.d/S12xorg_conf 
```

The -s makes it a symbolic link.

---

### Post by guitarist549 on 2006-11-12
alright, thank you very much... Actually, I thought I knew what the guy was talking about when he said create two xorg files, but I forgot how to get permission to create a file in a protected folder... Could you please tell me?

---

### Post by christhemonkey on 2006-11-12
```
gksudo gedit /etc/X11/xorg.conf.speed
```
or
```
gksudo gedit /etc/X11/xorg.conf.stamina
```

for the respective files.

---

