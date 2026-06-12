---
title: "Rhythmbox won't play MP3 stream"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Bocephus on 2006-07-21
Any ideas why Rhythmbox won't play [this]("http://kexp-mp3-128k.cac.washington.edu:8000/listen.pls") stream? I know that audio works fine on my new install because I hear the login clip for Ubuntu. Whenever I try adding that stream to Rhythmbox and then playing it the application locks up. After trying to play the stream I have to force quit Rhythmbox. Also, the default radio stations that used to be in Rhythmbox disappeared after the first time I had to force quit the application.

---

### Post by Sef on 2006-07-21
Have you installed the codecs?  If not, [click here.]("https://help.ubuntu.com/community/RestrictedFormats")

The codecs allow one to play most audio files but not those that are encrypted files.

---

### Post by Bocephus on 2006-07-21
That link says I need to install the package gstreamer0.10-plugins-ugly. I am currently looking through my Synaptic Package manager and I'm unable to find that package listed. There's a lot of gstreamer0.10-plugins listed and quite a few of them are installed. Just not the gstreamer0.10-plugins-ugly package. Is this the issue? If so, how can I get the package?

---

### Post by scxtt on 2006-07-21
you have to have the universe section of the repositories enabled ...```
:> cat /etc/apt/sources.list | grep universe
## Uncomment the following two lines to add software from the 'universe'
## universe WILL NOT receive any review or updates from the Ubuntu security
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by Bocephus on 2006-07-21
Thanks you guys, that worked (well, kind of). I can now play some Mp3 streams which I was unable to do before, before none of them worked. However, I'm still unable to play the stream I originally posted about:
[http://kexp-mp3-128k.cac.washington.edu:8000/listen.pls]("http://kexp-mp3-128k.cac.washington.edu:8000/listen.pls")
Can anybody verify that this is an issue with this particular version of Rhythmbox and this particular stream? Or am I still missing something?

---

### Post by Sef on 2006-07-21
I got working this way:

1) Downloaded the link.

2) Right clicked on the icon and opened Rhythmbox.

3) Clicked on it under radio in Rhythmbox.

---

