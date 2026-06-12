---
title: "Build-essential won't install off CD at all"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by castep_nut on 2007-07-29
I am having considerable trouble installing the build-essential package. I have tried reading previous posts which suggest using the CD/Synaptic Package Manager. I searched for and selected build-essential in the list, and it starts to download the package files. However, after a few minutes the following error pops up:

"W: Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-15.27_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_i386.deb
  File not found


W: Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb
  File not found


W: Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/g/gcc-4.1/g++-4.1_4.1.2-0ubuntu4_i386.deb
  File not found


W: Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/g/gcc-defaults/g++_4.1.2-1ubuntu1_i386.deb
  File not found


W: Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/d/dpkg/dpkg-dev_1.13.24ubuntu6_all.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/pool/main/b/build-essential/build-essential_11.3_i386.deb
  MD5Sum mismatch"

Now you guys will know more than me - but am I right in thinking that there might be some other way of obtaining these 'deb' files.

The ubuntu site for this ([http://packages.ubuntu.com/hoary/devel/build-essential](http://packages.ubuntu.com/hoary/devel/build-essential)) seems down but

[http://packages.debian.org/unstable/devel/build-essential](http://packages.debian.org/unstable/devel/build-essential)

is working. So transferred them across to laptop on CD from this PC (i don't have web access on the ubuntu machine). Could not open these either without ubuntu demanding a CD.

Any help would be greatly appreciated. Thanks

---

### Post by moffa on 2007-07-29
It seems that the CD wasn't burned properly since you have md5 errors.  You can try downloading the deb files from [http://packages.ubuntu.com](http://packages.ubuntu.com) and installing them.  You might have dependency problems but you just need to install those packages too.

---

### Post by Kafao1 on 2007-07-30
Hello! This is Athens calling! 
I tried to install "built-essentials" so as to install ndiswarpper but every time i get the following freaky message "E: couldn't find package built-essentials" 
what the hell should i do? i dont want to leave it as it is and format the disk later when i won't know what to do..... I downloaded the file fron the link that "castep_nut" gave, but i don't know what to do! Any suggestions?
thank you for your time!

---

### Post by Outrunner on 2007-07-30
> **Kafao1 said:**
> Hello! This is Athens calling! 
I tried to install "built-essentials" so as to install ndiswarpper but every time i get the following freaky message "E: couldn't find package built-essentials" 
what the hell should i do? i dont want to leave it as it is and format the disk later when i won't know what to do..... I downloaded the file fron the link that "castep_nut" gave, but i don't know what to do! Any suggestions?
thank you for your time!

That's 'build' not 'built'

---

### Post by Kafao1 on 2007-07-30
sorry, my bad, i typed it wrong here. :)

---

### Post by LaRoza on 2007-07-30
> **Kafao1 said:**
> Hello! This is Athens calling! 
I tried to install "built-essentials" so as to install ndiswarpper but every time i get the following freaky message "E: couldn't find package built-essentials" 
what the hell should i do? i dont want to leave it as it is and format the disk later when i won't know what to do..... I downloaded the file fron the link that "castep_nut" gave, but i don't know what to do! Any suggestions?
thank you for your time!

It is also "essential" not "essentials", that is a common error it seems.

---

### Post by Kafao1 on 2007-07-30
tryed everything but nothing seems to work...... oh boy.....

---

