---
title: "avis in ubuntu amd64"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Draszz on 2007-02-23
Hi,

I am "absolute begginer" in linux. After hard work, I finally managed to install ubuntu dapper on my brand new amd64 computer...And I don't know whay, this is the only distribution that runs...

Due to my job I had to work with avi files and I am not very confident on which program I should use nor how to install it. 

Can you help me? 

Thanks a lot,

Draszz

---

### Post by Spr0k3t on 2007-02-23
Any idea what application made the AVI files in question?  Sometimes you will find AVI files are renamed divx files, or renamed mp4 files.  Also, do you know if there might be a DRM associated with the files?

Anyway, you may need to dig into the restrictedformats area.  There are several howtos out there which will help you install the codecs you need for these formats.

FreeFormats
[https://help.ubuntu.com/community/FreeFormats](https://help.ubuntu.com/community/FreeFormats)

RestrictedFormats
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mcduck on 2007-02-23
avi is just a container format, and can contain audio & video coded with any format. Your best bet is to install all codecs mentioned in the restricted formats page, and hope that your avi files uses one of the formats those codecs can handle.

(btw, *DivX is not a format*, it's a commercial codec to create MPEG 4 video!)

---

### Post by Draszz on 2007-02-23
Thanks both, 

If it is important, I make the avi videos with MATLAB. What is a DRM?

Yes, I knew that it was a RestrictedFormat, and I had read the propper page, but I am not very confident on which codec to install. I'll test some of them and I'll tell you.

Draszz

---

### Post by Spr0k3t on 2007-02-23
DRM is Digital Rights Management.  You can install the free codecs for AVI if you would like.

As for DivX "format" true, it's not... but they recommend labelling the files .divx instead of .avi.  Why, I couldn't tell you... just the general consensus at the divx.com forums.

---

### Post by mcduck on 2007-02-24
> **Spr0k3t said:**
> As for DivX "format" true, it's not... but they recommend labelling the files .divx instead of .avi.  Why, I couldn't tell you... just the general consensus at the divx.com forums.
Well, they make money out of making people believe that they need DivX for something, so it would of course benefit them to make it seem like something else than normal MPEG 4 ;)

---

### Post by Spr0k3t on 2007-02-24
That makes sense... free advertising I spoze.

---

### Post by mcduck on 2007-02-25
> **Spr0k3t said:**
> That makes sense... free advertising I spoze.

More like fooling people to believe that they need DivX to watch those movies :D

---

