---
title: "RDP to WinXP box? or VM WinXP on Ubuntu?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by kimro on 2006-11-22
Hi, I just switched to Ubuntu Edgy because I was really getting sick of refreshing my WinXP system every 3-4 months. 

I've successfully finished setting up my box to my liking. But I do web design work on part time basis and I still prefer Photoshop. I've looked into setting up a VMware server but just realized that I can simply install Creative Suite 2 on my media box (WinXP) and just RDP in. 

Can someone help me evaluate option 1 and option 2? Below are the details.

Environment:
1. Main box: my daily desktop - Ubuntu Edgy running on AMD64 x2 3800, 1gb ram, nVidia 6600GT 128mb
2. Media box: I mainly use this for entertainment purposes and downloads from some websites that utilizes active x based file sharing - WinXP running on AMD64 3200, 512mb ram, nVidia mx400 128mb
3. Linksys router, wire running to my main box and wireless G connection to my media box

Option 1:
Install windows applications I prefer on Media box and RDP in whenever I need it

Option 2:
Install VMware server on my Main box, create WinXP vm and use vm

Thank you!!

---

### Post by davmac on 2006-11-22
I think that the problem you may face here is that graphics performance is one area where both are relatively weak. I suspect that the speed of the wireless connection will mean that RDP will be worse than VMWare. The flip-side is that the RDP solution will be quicker to implement and test.

In your shoes I'd go for RDP first (because I'm a lazy sod) and if that doesn't cut the mustard have a go with VMWare.

Of course if neither of these work you've still got the dual-boot option...

Hope this helps,

Dave Mac

---

### Post by kimro on 2006-11-23
you are right.

i just wanted to ask you guys in case i managed to miss out on a clear cut answer. maybe i should just start learning gimp :-k

---

### Post by davmac on 2006-12-06
I'm a bit of a fan of Gimp, but if you're coming from a Photoshop background have a look at Gimpshop. It's a version of Gimp but the UI mimics Photoshop as closely as possible.

Dave Mac

---

