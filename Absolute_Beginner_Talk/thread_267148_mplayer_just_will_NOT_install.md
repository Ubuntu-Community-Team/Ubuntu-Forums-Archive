---
title: "mplayer just will NOT install"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-09-28
Hi everyone. Well I've been searching for answers and have deleted and then downloaded again for mplayer. I believe I have all the files necessary - as per attached screenshot - But I still just cannot make it install. I've tried  
Automatix, SynPakMan and whatever else I could find. I've tried copying the files to SynPakMan,...I forget all the things I've tried.](*,) Mplayer isn't in the repository system. all the error messages are that the file can't be found!
VLC doesn't work either, Totem works sometimes but poorly, Gxine always works but jumps way too much.
I'm wondering if there is something amiss with my system now after so many attempts to download and install various apps. i may have stuffed something!
Frustrated!! ](*,) 
Any advice welcome.

---

### Post by Kateikyoushi on 2006-09-28
You could just install the package but if you insist to compile it then here is a [howto]("http://www.ubuntuforums.org/showthread.php?t=31061").

---

### Post by croak77 on 2006-09-28
You need multiverse enabled in order to use apt to install mplayer. Can you post your /etc/apt/sources.list?

---

### Post by carloslosgrande on 2006-09-29
Hi. Kateikyoushki, I'm not trying to compile it - I don't know how - I just want to install it and the easiest way is definitely my preference. I had a look at that 'how to' and my eyes boggled.
Croak 77, I'd love to post you that /etc/apt thingy....how do I get it??
even better - how do stick the mplayer download onto synaptic? How do I fix Gxine so it plays properly...etc. I'm not really fixated on mplayer so much as a WORKING dvd app.
Thanks for yor help.

---

### Post by pistcivet on 2006-09-29
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by carloslosgrande on 2006-09-29
Hi Croak 77, Got this /etc/apt/sources.list
It looks to me like its got all the repositories listed.
:confused:

---

### Post by Kilz on 2006-09-29
> **carloslosgrande said:**
> Hi Croak 77, Got this /etc/apt/sources.list
It looks to me like its got all the repositories listed.
:confused:

Have you teried going to the mplayer listing in the [packages database]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fm%2Fmplayer%2Fmplayer_0.99%2B1.0pre7try2%2Bcvs20060117-0ubuntu8_i386.deb&md5sum=e555e36885e8d99dfc4b8dd48df3c216&arch=i386&type=main"), downloading it, double clicking on it to let gdebi install it?

---

### Post by carloslosgrande on 2006-09-29
Hi Kilz, Thank for your help. I tried your idea and it seemed to work well, up to the point shown in the attachment - no Libfaac0 file.
then I did some thinking, went back to the packages and, eventually, found everything! Mplayer is now working!
Thank you very much Kilz for understanding just what it was this dummy needed, and supplying me with the tools I like best - simple ones!:) 
Happy days!
I think this particular thread is at an end.

---

### Post by Kilz on 2006-09-29
> **carloslosgrande said:**
> Hi Kilz, Thank for your help. I tried your idea and it seemed to work well, up to the point shown in the attachment - no Libfaac0 file.
then I did some thinking, went back to the packages and, eventually, found everything! Mplayer is now working!
Thank you very much Kilz for understanding just what it was this dummy needed, and supplying me with the tools I like best - simple ones!:) 
Happy days!
I think this particular thread is at an end.

Your welcome  :D

---

