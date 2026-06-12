---
title: "help with wmp codecs"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by mlucian72 on 2007-06-19
Is there any way someone could get the w32codecs and libdvdcss2 from a XP cd that he owns?
 Would that be something illegal?
  And if there is a way, how do you install them in Feisty?
 All the links to the repositories that have these codecs don't work!
 
 Thanks!

---

### Post by qyot27 on 2007-06-19
> **mlucian72 said:**
> Is there any way someone could get the w32codecs and libdvdcss2 from a XP cd that he owns?
Nope.  XP install CDs don't come bundled with that kind of stuff (unless you're talking codecs like Cinepak or MS Video 1, which would mean you're watching some *really* old video files, and besides that, those can be decoded by libavcodec, the decoding core of mplayer and VLC).  libdvdcss2 is also definitely not included with XP install CDs, considering most DVD playing software that comes bundled with XP is commercial software.

Besides, w32codecs and libdvdcss2 are specific packages.  Even if the dll files are the same, you'd need to know how to make a proper install package, etc. (unless for something like mplayer you can just plop it down in a specific folder, but I've never truly understood the way mplayer does that kind of thing, just that they say it can use Win32 codecs).  I can understand the use of libdvdcss2, but the use of w32codecs has escaped me, except in the case of decoders that are better tuned to deal with things compared to libavcodec, like CoreAVC, which isn't part of that package anyway.  It does just seem that libavcodec supports most of what you'd ever want to view, unless it's some obscure format that you'd probably be better off converting to a common format first as it is.

My suggestion would be to try to find a Dapper or Edgy repository that has them if you can't find any specifically for Feisty, and use those to install them.

---

### Post by zanglang on 2007-06-19
Try this one? Seems to be working here:
> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

If you need more detailed instructions check here:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mlucian72 on 2007-06-19
This link does not work either.
 So this means there is no way to play streaming wmp in Ubuntu?
 The stream I'm trying to play with mplayer uses w32 codec.It does not play.
 Anyone knows how to get w32codecs or any other way around this?

 Thanks! :(

---

### Post by NeoLithium on 2007-06-19
Hi :)
For Feisty, you need to make sure you have the proper repositories enabled, and then download them, this guide will walk you through it.   Just follow the guide step by step for enabling the extra repositories:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)
And then downloading the proper codecs:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

---

### Post by mlucian72 on 2007-06-19
Nope. It doesnt works.

---

### Post by NeoLithium on 2007-06-19
Have you enabled the additional repositories? If so, do you get an error message in the terminal window that you could copy and paste?

---

### Post by mlucian72 on 2007-06-19
This is the terminal output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

---

### Post by NeoLithium on 2007-06-19
And did you follow the guide here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)  on how to add the additional repositories?

---

### Post by mlucian72 on 2007-06-19
Yes. All the sources are marked just as the guide said.
 Any ideas?

---

### Post by NeoLithium on 2007-06-19
Hmmm, did you already run this command, after changing the sources.list:
```
sudo aptitude update
```

I know that the repositories work, I had to reinstall this afternoon with the same repos, so there may have just been a step missed somewhere along the line.

---

### Post by mlucian72 on 2007-06-19
still doesn't work...is there another way?

---

### Post by vbmds on 2007-07-03
Install Automatix2 - [http://www.getautomatix.com]("http://www.getautomatix.com") - and get the package via the Codecs and Plugins category.

---

