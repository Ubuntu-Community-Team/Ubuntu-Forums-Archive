---
title: "ffmpeg"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by Caraethelanea on 2006-06-01
Okay I'm trying to install ffmpeg but this message comes up when I try...

Could Not Mark All Packages For Installation or Ugrade. => The following packages has unresolvable dependecies. Make sure all repositories are added and enabled in the preferences.

ffmpeg:
 Depends: libavcodeccvs51 (>=3:20060430) but it is not installable
 Depends: libavutilcvs49 (>=3:20060430) but it is not installable
  Depends: libogg0 (>=1.1.3) but 1.1.2-1 is to be installed
  Depends: libvorbis0a (>=1.1.2) but 1.1.0-1ubuntu1 is to be installed
  Depends: libvorbisenc2 (>=1.1.2) but 1.1.0-1ubuntu1 is to be installed

I'm completely new to Linux I had a friend help me but now he's really busy... this is a lot to learn so please help me and be patient I'll probably ask a lot of duh questions. Thanks.

~Carae

---

### Post by [S|G] on 2006-06-01
It seems that you have some old packages installed on your system. First, you need to update your repositories. Are you running ubuntu Breezy or Dapper?

In either case, you should check here first: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

After you enable the repositories, go to a terminal and type:
```

sudo apt-get update

```

Then try to install ffmpeg again

---

### Post by %hMa@?b&lt;C on 2006-06-02
if what SG suggested doest work, try 
```
sudo apt-get -f install
```
and if that doesnt work try
```
sudo apt-get build-dep ffmpeg
```
if neither of those work, just respond and i will try to help 
-jeff

---

### Post by tufcamman on 2008-03-24
Hi, I am having this exact same problem and am glad I found this thread.

I have tried the commands from [S|G] and from jeffc313 and still get the same error the thread started with.

I found my way to ffmpeg with the intention of using Cinelerra.  Any more help would be greatly appreciated.  Thanks!

P.S. I am running 7.10 and I have all the Software Sources enabled.

---

### Post by tufcamman on 2008-04-01
Hey, I figured out what was wrong.  I just didn't have the Medibuntu repository enabled.  No big deal.  Works great now

---

### Post by Joeb454 on 2008-04-01
ffmpeg is actually in the ordinary repo's :)

run ```
sudo aptitude install libxine1-ffmpeg[CODE]

or if you want ALL the plugins, [CODE]sudo aptitude install libxine1-all-plugins
``` :D Hope this helps

---

