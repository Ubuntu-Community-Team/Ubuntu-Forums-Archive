---
title: "Where's beryl in the synaptic?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by nickhuddleston on 2007-01-28
Hi,
  This is my first post and first question. My brother-in-law sparked my interest in Ubuntu when he showed me a video of the Ubuntu + Beryl. So I decided to try to install and put beryl on my Dell Inspiron E1505. Why should I pay Microsoft for their crappy upgrade when I can get a cool free one on the web. So, I successfully installed Ubuntu 6.10 today.

My problem I think is pretty simple to answer, but maybe not... Here goes...
I installed Ubuntu and found an easy to follow guide on how to install beryl. So i followed it and all was going smoothly until this step: "Now we need to find and install 4 key packages xserver-xgl, emerald-themes, beryl and xorg-driver-fglrx, the easiest way to do this is by searching and selecting as show on Now we need to find and install 4 key packages xserver-xgl, emerald-themes, beryl and xorg-driver-fglrx, the easiest way to do this is by searching and selecting as show on the pictures.the pictures." The picture shows synaptic installing all of these. So I opened up the Synaptic and found the first and the last package that it mentioned, but I could not find through Synaptic "emerald-themes or beryl" to install them on my system. I am guessing that these are pretty essential to the installation of beryl, so how can i get these files onto my computer if Synaptic will not find them?
Thanks,
Nick

---

### Post by hyper_ch on 2007-01-28
Have a look here... I followed the 6.10 guide for Xubuntu Edgy and it works fine:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

---

### Post by Waappu on 2007-01-28
Hi

You need add Beryl repository to your /etc/apt/sources.list file. I think that is mentioned in guide you have followed so far.

---

### Post by Tux Aubrey on 2007-01-28
My guess is that you haven't enabled the repositories where the official beryl packages are kept - the two packages you got are fairly generic (used by other software) so are in the "normal" repositories.  That wiki link in the post above will guide you enabling the beryl repository and installing the "gpg key" you'll also need.  You will quickly get the hang of this stuff.

Good luck - and welcome to Ubuntu!

---

### Post by jvc26 on 2007-01-28
I'd take a peek at [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851) as it mentions how to get the newer versions, as 0.1.2 was the highest you could get on one of the old set of repos, I changed them and now have 0.1.4 and 0.1.5.
Il

---

### Post by x64Jimbo on 2007-01-28
There's an even easier way to do this now. Both nVidia and ATI cards are now supported with fully automated installer scripts. Don't bother with the how-to's - just get the script and run it!

---

