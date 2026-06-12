---
title: "video encoding problem (ffmpeg)"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by mangurt on 2008-03-10
Greetings all,
I am trying to convert some avi files to play on my psp.  I have done this before, but for some reason, I am getting an error when I try to use ffmpeg tonight.

Here's the results from ffmpeg

ed@ed-desktop:~$ ffmpeg -i dexters01e05.avi -f psp -r 29.97 -b 768k -ar 24000 -ab 64k -s 320x240 M4V00001.MP4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --prefix=/usr --libdir=${prefix}/lib --shlibdir=${prefix}/lib --incdir=${prefix}/include/ffmpeg --enable-shared --enable-mp3lame --enable-gpl --enable-faad --mandir=${prefix}/share/man --enable-vorbis --enable-pthreads --enable-faac --enable-xvid --enable-dts --enable-amr_nb --enable-amr_wb --enable-pp --enable-libogg --enable-libgsm --enable-x264 --enable-a52 --extra-cflags=-Wall -g -fPIC -DPIC 
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Nov  3 2006 21:14:27, gcc: 3.3.5 (Debian 1:3.3.5-13)
dexters01e05.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.
ed@ed-desktop:~$

I have tried grabbing the lastest version via svn, but I still have the same problem.  The avi file plays fine with mplayer, totem, and vlc.  I am at a loss here...any ideas?

Thanks

---

### Post by lloyd_b on 2008-03-10
Could you run the following and post the results (in the directory with that file):
```
ls -Q 
```

This will produce the file list, with quotation marks around each file.  What I'm wondering is if you've got a leading or trailing space character in the filename (that error you posted is the some one you'll get if you specify a non-existent file).

Another test for this:
```
cp dexters01e05.avi test.avi
```
and see if it gives you a "cannot stat ...: No such file or directory" error.

Lloyd B.

---

### Post by mangurt on 2008-03-11
Ok,
Heres what I get when I do the ls -Q

ed@ed-desktop:~/Videos/dexter_s01$ ls -Q
"dexter07.avi"  "dexter09.avi"  "dexter11.avi"  "dexters01e05.avi"
"dexter08.avi"  "dexter10.avi"  "dexter12.avi"  "test.avi"
ed@ed-desktop:~/Videos/dexter_s01$ 


And as you can see, no problem with the cp command.  Like I said, I am at a loss, because ffmpeg worked before.....

Any ideas now?

---

### Post by lloyd_b on 2008-03-11
I see *a* problem (don't know yet whether it's *the* problem).

From your original post:
```
ed@ed-desktop:~$ ffmpeg -i dexters01e05.avi -f psp -r 29.97 -b 768k -ar 24000 -ab 64k -s 320x240 M4V00001.MP4
```

The "ed@ed-desktop:~$" Indicates that you are in your home ("~") directory.

From your last post:
```
ed@ed-desktop:~/Videos/dexter_s01$ ls -Q
```

The "ed@ed-deskstop:~/Videos/dexter_s01$" indicates that the video in question ("dexters01e05.avi") is in the "~/Videos/dexter_s01" directory.

So you need to do one of two things.  Either provide a full path to that video ("ffmpeg -i ~/Videos/dexter_s01/dexters01e05.avi ..."), or change to that directory ("cd Videos/dexter_s01") before running the "ffmpeg" command.

In short - the command is failing because it doesn't know where to find the input file.

Lloyd B.

---

### Post by mangurt on 2008-03-11
> **lloyd_b said:**
> I see *a* problem (don't know yet whether it's *the* problem).

From your original post:
```
ed@ed-desktop:~$ ffmpeg -i dexters01e05.avi -f psp -r 29.97 -b 768k -ar 24000 -ab 64k -s 320x240 M4V00001.MP4
```

The "ed@ed-desktop:~$" Indicates that you are in your home ("~") directory.

From your last post:
```
ed@ed-desktop:~/Videos/dexter_s01$ ls -Q
```

The "ed@ed-deskstop:~/Videos/dexter_s01$" indicates that the video in question ("dexters01e05.avi") is in the "~/Videos/dexter_s01" directory.

So you need to do one of two things.  Either provide a full path to that video ("ffmpeg -i ~/Videos/dexter_s01/dexters01e05.avi ..."), or change to that directory ("cd Videos/dexter_s01") before running the "ffmpeg" command.

In short - the command is failing because it doesn't know where to find the input file.

Lloyd B.

Thank you for the response.  The other times I have used ffmpeg to convert avi files, I was in the directory the file was (ie /Videos/dexter_s01) and had no problem converting the file.  Odd that I am having the problem now.  I will try providing a full path to the video, and see what I get from that.

---

