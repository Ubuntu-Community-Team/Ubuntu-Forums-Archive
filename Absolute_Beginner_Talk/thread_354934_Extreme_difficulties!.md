---
title: "Extreme difficulties!"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by naoise on 2007-02-06
Ok, so I have a few problems, none of which I have the slightest clue about, including whether or not I should uninstall and reinstall once I'm more ready to learn all this. So here goes the complaints following my system specs:

AMD X2 4400+
Nvidia 7800 GT 


When I boot, it shows both 386 and generic Kernals. Is this Ok? How do I remove the wrong one? Which is the wrong one? Should I be on an AMD specific? Is the 386 only for intel?

Next,

When I installed linux, it looked like poop, so when I tried to install the nVidia updated driver, I had an issue with the monitor I believe. When I rebooted, it is covered in a bright blue color, but I can still see my desktop. I'm using a Toshiba 21" HDTV hooked up via Composite cables (something that I found a forum post on nVidia forums). Apparently I need to fix this, but when I tried, the code didn't copy right, and it ended up having to restore an old xorg.conf.

This is all the problems for now..but I'm sure ill have many in the future.

Is there any *best* place to visit to get a newbie started? I"m making the switch from Windows mid-semester and I'm starting to think its more of a project than I had expected.


Thank you so much in advance, if you could also give me advice on how to make it to the IRC, I could probably get more resolved faster.

---

### Post by harlan on 2007-02-06
You don't have any wrong kernel. You simply have 2. If you have boot the generic kernel (the first in the grub menu list) go to system/admin/synaptic and search linux-image-xxx-386 and remove it.

A good web for a newbie is [www.psychocats.net](www.psychocats.net)

I can't help you with the rest. Sorry

---

### Post by shareMenaPeace on 2007-02-06
> **harlan said:**
> You don't have any wrong kernel. You simply have 2. If you have boot the generic kernel (the first in the grub menu list) go to system/admin/synaptic and search linux-image-xxx-386 and remove it.
Why should i remove 1? Isnt their a purpose for this? (Have 2 too).

---

### Post by naoise on 2007-02-06
Is there? How can I get to IRC so I can get a constant flow of help, i'm going insane. 

Should my AMD system have a 386? Isn't that supposed to be for intel?

---

### Post by mcduck on 2007-02-06
No, there's no need to have many kernels. Feel free to uninstall the 386-kernel.

Anyway, all modern CPU's are x86-compliant, and that's what the '386' in the kernel name is for. 386 works for all, 686 works for new Intel and AMD CPUs and K7 works for new AMD CPUs only. Then there's SMP kernels for multi-CPU/multi-core machines. But in Edgy the generic kernel handles these all.

---

### Post by naoise on 2007-02-06
Thank you! And does anyone have a clue about how to fix my video problem?

---

### Post by shadowboxer_k on 2007-02-06
hey, 

sorry i can't help you with the video problem, as i am a total newbie myself (i just installed ubuntu 3 hours ago), but here's a helpful link about how to get to irc. 

[https://help.ubuntu.com/community/XChatHowto](https://help.ubuntu.com/community/XChatHowto)

good luck!

---

