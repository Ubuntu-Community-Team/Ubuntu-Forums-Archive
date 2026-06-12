---
title: "Help with DVD codecs"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Miss Karen on 2008-03-03
I know there's probably been a thousand posts on this, but my problem is a bit trickier...

You guys showed me how to install the multimedia codecs ages ago (THANKYOU)!

Now I installed them last night, but there were about eleven that wouldn't install, saying that I needed extra packages but of course my laptop isn't connected to the internet, so it wouldn't find them.

Totem now plays video clips and assorted sounds, it just won't play DVDs. Help? Did I miss something?

---

### Post by RussellGee on 2008-03-03
The only way you could do this if you dont have internet access is by identfying the packages you need then to manually download them from the ubuntu servers and install them.

Do you know what packages you need?

---

### Post by Miss Karen on 2008-03-03
No I don't, sorry - I'll have to check tonight and come back tomorrow :confused::confused::confused:

---

### Post by Hospadar on 2008-03-03
To play dvd's you'll need libdvdcss2 from medibuntu.  since you don't have an internet connection, you'll have to download it from a different machine and copy it over.  I don't think it has any pre-requisites, but try installing it, and if it tells you to get some packages, go get those packages.

You can download libdvdcss2 manually [here]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/").  then just double click it on your desktop to install it. (you may have to right-click and say Open With->Gdebi Package Installer).  Download the latest version of libdvdcss2 (not libdvdcss2-dev, that's if you are writing or compiling code that needs the library)

That should be all you need to play dvds.  If dvds still don't work, try getting some different mpeg videos and see if those will play.  Your system should already have the necesarry codecs to play mpegs (I think) so you just need libdvdcss to decrypt the dvds.

EDIT:
you may need the Gstreamer "bad" and "ugly" gstreamer plugins as well
[http://packages.ubuntu.com/gutsy/gstreamer0.10-plugins-bad](http://packages.ubuntu.com/gutsy/gstreamer0.10-plugins-bad)
[http://packages.ubuntu.com/gutsy/gstreamer0.10-plugins-ugly](http://packages.ubuntu.com/gutsy/gstreamer0.10-plugins-ugly)
Just click the link for your architecture (probably i386 unless you installed 64 bit ubuntu) to get the deb

the pre-reqs for these are listed on the pages, there are a pretty frightening amount of pre-reqs for some, but probably most of the pre-requisites are already installed.  you may want to try just installing the libraries themselves, then see what missing dependencies they complain about when you try to install them (if your internet connection is nearby and convenient)

Hope this helps!

---

### Post by Miss Karen on 2008-03-03
So I just have to download all of those?

---

### Post by Miss Karen on 2008-03-05
Umm, it didn't work. I have a full list of the packages needed and if anyone could tell me where to find them, I would be most grateful...

---

### Post by Moop on 2008-03-05
I'm not sure which packages you're looking for but you can download packages from medibuntu here. [http://packages.medibuntu.org/pool/](http://packages.medibuntu.org/pool/)

---

### Post by Miss Karen on 2008-03-05
I essentially need a whole bunch of "lib" ones, things like "libjinglep2p0.30" and so forth, the whole list is really long...

Any directions to this?

---

### Post by Moop on 2008-03-05
You should find what you need here. [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Miss Karen on 2008-03-05
Hey, thanks mate! I got them all except one

It wouldn't find libdisplay1

---

