---
title: "[SOLVED] Terminal commands"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by ellalan on 2008-03-11
Hi
I am trying to install the scanner drivers from canon. I am using the terminal to install them because canon specifically instructs to install using terminal.
I downloaded the drivers and extracted them to my Desktop, then I tried sudo dpkg -i scangearmp-common_1.10-1_i386deb,
I get the Error:   cannot access archive:no such file or directory, errors were encountered while processing: scangearmp-common_1.10-1_i386.
Previously I tried Synaptic Package Manager to install but my scanner was not recognized.
Could someone help me to solve this problem please. Thank you.

---

### Post by forestpixie on 2008-03-11
change to the directory first - if it's on desktop

cd Desktop
and have another go

---

### Post by bodhi.zazen on 2008-03-11
Please post the exact output of your terminal commands and error messages (you can cut and paste from the terminal).

You post has several syntax errors and I can not tell if your problem is with syntax or, like me, you are a slooy tyoer (lord knows I have had to fix more posts due to slopy typing ...)

---

### Post by ellalan on 2008-03-11
Hi
This is what I get when I try to install:

~$ sudo dpkg -i scangearmp-common_1.10-1_i386.deb
dpkg: error processing scangearmp-common_1.10-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 scangearmp-common_1.10-1_i386.deb

I hope this is more cleare than my previous post, Thanks for the help.

---

### Post by bodhi.zazen on 2008-03-11
First, you can use tab completion to complete commands / file names

Type scan<tab>

Try sudo dpkg -i /full/path/to/scangearmp-common_1.10-1_i386.deb

so, either

```
sudo dpkg -i ./scangearmp-common_1.10-1_i386.deb
```

or

```
sudo dpkg -i /home/<user>/scangearmp-common_1.10-1_i386.deb
```

If that fails, either your download is corrupt or you need to contact the maintainer (ie file a bug report)

---

### Post by ellalan on 2008-03-11
Thank you Guys. **forestpixie'**s method worked for me and I have made a note of **bodhi-zazen'**s for future reference. I hope when I restart my PC it recognizes the scanner. Even if it doesn't work I can be happy with myself as I have learned something new. Thanks again for your help.

---

