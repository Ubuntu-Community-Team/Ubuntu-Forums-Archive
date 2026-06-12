---
title: "Glibc error on a Samsung printer installation"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Spikextrem on 2006-02-02
Hi!

It's not the first time I try to install my printer on a linux OS. I did it on Gentoo 3 or 4 times without any problem. But Ubuntu seems to dislike to drivers. It's a Samsung ML-1710 printer. The drivers seems to be kind of old though. I saw that I was not alone to experiment this kind of problem, but I didnt find any solution...

[B]# ./setup.sh
./setup.sh: line 143:  6736 Erreur de segmentation  "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1[/B]

What's the matter with glibc? I downloaded the lastest version last week. 

Note that : "Erreur de segmentation" stands for Segfault :P

Plz help this poor printer to taste to linux again!

---

### Post by Spikextrem on 2006-02-02
To anyone having this trouble.

I was trying to use vnc in remote desktop on my server to install the printer locally. It was conplaining about not having an X server install or something. What I did is 

chmod +X setup.sh

then I logged into remote desktop (NOT SSH because you need a graphical interface to install those drivers). I run the script as a USER in the first place, running it as a root the first time always got me a error... So I run it once in user mode, then quit. I restarted I script as a root and voila, it works fine!

There must be a reason for all this, but I don't really care, it works. Hope that it will help someone one day or another.

---

