---
title: "opening windows shares"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by dubbedout on 2007-01-28
Ok, I'm pretty new to Ubuntu and I've got everything running pretty smoothly..except for one aspect, file sharing between my other windows machines.  I have installed samba and everything and I can view all my network shares, I can even open JPG files and DOC files but when I try to open an AVI or MP3 it doesn't work.  I've got all the codecs through automatix but it just won't work.

When I try to open a MP3 in RythmBox music player I get an Import error "Cannot read from resource" but I can open a JPG in that same directory...whats the deal!?!?

Thanks!  this forum is awesome, without it I probably would never have gotten anything working!

---

### Post by antiwindows798 on 2007-01-29
It appears that you don't have a problem with your network connection but with codecs that you don't have in Ubuntu open those files.

Try to install RealPlayer.

---

### Post by dubbedout on 2007-01-29
I have tried every media player available I beleive...Here's an update though.  When I copy the file from the Win machine to Ubuntu it will only play the first 4-5 seconds of the song and it stops.  It shows the file size correct though.  Not sure, I know for a fact I can copy a file from Ubuntu to a windows share and play it on windows fine, it just seems like I cant play them on Ubuntu from the windows share...hmmm...this is frustrating!

Please help!

---

### Post by dubbedout on 2007-01-30
bump

anyone???

---

### Post by ultima on 2007-01-30
Check out this page [https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

I can't give an exact answer because I use KDE

---

### Post by akudewan on 2007-01-30
The files won't play directly, at least I haven't found a way to do it yet.

What you can do is or mount the samba share using smbmount, like this:

```

sudo mount -t smbfs //192.168.xx.xx/folder /mnt/temp/

```

You can enter the username and password also, do "man smbmount" for more details.

---

### Post by akudewan on 2007-01-30
Hi,

I discovered another method that can play files, but its a little more tedious.

You can play media files using mplayer, like this:
```

mplayer smb://10.10.19.xxx/folder/filename.avi

```

I don't think there's a way to specify a username or password though...

---

### Post by dubbedout on 2007-02-03
> **akudewan said:**
> The files won't play directly, at least I haven't found a way to do it yet.

What you can do is or mount the samba share using smbmount, like this:

```

sudo mount -t smbfs //192.168.xx.xx/folder /mnt/temp/

```

You can enter the username and password also, do "man smbmount" for more details.

awesome! that worked perfectly!  I also found out something pretty cool that I didnt know about, when you put your mouse over a mp3 it starts playing the song! thats frickin' awesome!  I love Ubuntu more and more everyday!

thanks guys!

---

