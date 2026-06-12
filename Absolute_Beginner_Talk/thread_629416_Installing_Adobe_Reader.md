---
title: "Installing Adobe Reader"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by FDDave on 2007-12-02
Yesterday I installed Ubuntu 7.10, and I'm trying to get the Adobe Reader Plugin for Firefox. I followed the download link, but all it did was download an rpm archive. I can go in and see all of the files, but I have no idea what to do with them. There's probably something I'm missing, so I appreciate any help.

---

### Post by Blutack on 2007-12-02
Yep!
Normally in ubuntu you don't download and install packages from the internet.  Instead, you install programs from repositories (like servers full of software).
Unfortunately, because Adobe is not a free piece of software you need to add another repository to your list.
Follow the first set of instructions in this howto.
[http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox-in-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox-in-feisty-fawn.html)

---

### Post by aysiu on 2007-12-02
**Step 1**
Delete the RPM

**Step 2**
Make sure you [extra repositories enabled](http://www.psychocats.net/ubuntu/sources)

**Step 3**
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install acroread acroread-plugins
```

---

### Post by Blutack on 2007-12-02
Just to check, you are aware that Ubuntu ships with a very nice PDF Viewer by default?  You will have to download the pdf, but then double click and it should work fine.  Or open with evince.  Acroread is very slow and bloated, although unfortunately sometimes necessary.

---

### Post by PmDematagoda on 2007-12-02
You can get Acrobat Reader by using the [Medibuntu Repositories]("https://help.ubuntu.com/community/Medibuntu").

After you get the repositories, install Acrobat Reader using:-

```
sudo apt-get install acroread
```

after that is finished, install the plugins using:-
```

sudo apt-get install acroread-plugins
```

---

### Post by dadawan on 2007-12-02
> Yesterday I installed Ubuntu 7.10, and I'm trying to get the Adobe Reader Plugin for Firefox. I followed the download link, but all it did was download an rpm archive. I can go in and see all of the files, but I have no idea what to do with them. There's probably something I'm missing, so I appreciate any help.

  Hi FDave,

   I'm a Linux noob also,  so disregard this if somebody has a better answer.

    Did you try going to System:Adminstration menu, and then Synaptic Package Manager?

    Click on 'Search' and type in 

Adobe Reader

   There are a bunch of packages there.   I would guess that acroread is one you'd want, and maybe mozilla-acroread for one that works with Firefox....
[SIZE="2"][B]
   oops it looks like this is actually in Medibuntu,  so you'd need to add that to your list of repositories etc.[/B][/SIZE]

    For brief info on how to get Medibuntu:

[URL="https://help.ubuntu.com/community/Medibuntu"]
https://help.ubuntu.com/community/Medibuntu[/URL]

    For step by step instructions for Windows users new to Ubuntu, I have a page which describes how to get Medibuntu stuff to show up in the package manager:

[http://www.bornthree.com/HowTo/GutsyEmbelish1/EmbelishingUbuntuGGPart3.html]("http://www.bornthree.com/HowTo/GutsyEmbelish1/EmbelishingUbuntuGGPart3.html")

My tutorial is more about getting MPeg, Mp3 and DVD support, but if the Adobe stuff is part of Medibuntu, you'll need to do those steps anyway.

Hope this helps.

-Kevin

---

### Post by aysiu on 2007-12-02
> **Blutack said:**
> Just to check, you are aware that Ubuntu ships with a very nice PDF Viewer by default?  You will have to download the pdf, but then double click and it should work fine.  Or open with evince.  Acroread is very slow and bloated, although unfortunately sometimes necessary.
Ah, good point. We're all so quick to help out with the Adobe Acrobat installation without reminding the OP about Evince (the default PDF viewer).

Unfortunately, I don't think Evince can do PDF forms, though, if that ends up being what the OP is after (I don't know).

---

### Post by FDDave on 2007-12-02
The medibuntu link was helpful in getting the repositories and aysiu's instructions allowed me to install (or at least, it's installing so far). 

Thanks for all of your help!

---

