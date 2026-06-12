---
title: "Request: Looking for cd ripping tool for 64bit OS"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by BjornHaland on 2006-04-13
Hey, I did perform a search for "cd ripping amd64", no good responses there.

Just wanted to ask if someone could recommend me a good cd ripping tool for the 64-bit installation of Dapper?

Btw, would I need to install any extra mp3 codecs for that?

I know there's sound juicer.. it seems so slow, running at 4x or something.

---

### Post by hw-tph on 2006-04-14
Basically all audio CD rippers on Linux are based on cdparanoia III. There are several good ones in the repositories - Grip and abcde come to mind. The first is an advanced Gnome ripper (using cdparanoia) and the latter is a simplistic but very effective Bash script.

As for encoder, I suggest you use Lame. It is the best encoder out there, outperforming all other - both commercial and free mp3 - encoders. You can either grab Lame from the multiverse repository or build it from source. I recommend the latter, since the 3.97 beta version sports a much updated VBR algorithm which is a lot faster and more accurate than the old one. The source distribution even comes with a preconfigured debian subdirectory so you can build a set of .deb packages very simply: Untar the archive, **cd** into the lame-3.97 directory and execute the following: **fakeroot debian/rules binary**
Then install the deb using **dpkg -i lame_3.97-8_i386.deb libmp3lame0_3.97-8_i386.deb libmp3lame0-dev_3.97-8_i386.deb**

To use the new algorithm you need to pass --vbr-new. In Grip I use this encoder command line: **-V 2 --vbr-new %w %m**
This produces VBR mp3's of decent size with excellent quality, and quickly too.

Håkan

---

### Post by BjornHaland on 2006-04-14
That's very nice of you, thanks for taking the time.

---

