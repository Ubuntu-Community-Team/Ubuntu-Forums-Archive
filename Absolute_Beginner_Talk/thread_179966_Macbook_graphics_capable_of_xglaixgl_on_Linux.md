---
title: "Macbook graphics capable of xgl/aixgl on Linux?"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by forbes on 2006-05-21
I'm just wondering if the new MacBook (not pro) with the onboard Intel GMA950 will support the xgl or aigxl projects on Linux? I believe that intel graphic chipsets are usually well supported within linux, but have head that there may be a problem with the way the GMA950 on the Mac Minis and MacBooks are configured. Easy test could be with the Kororaa LiveCD maybe.

Which is more likely to succeed, elilo or bootcamp with BIOS emulation?

Any advice (particularly confirmed experiences) or more insight would be wonderful.

many thanks, forbes.

---

### Post by Jeroen Vernooij on 2006-05-21
Yes it is supported, and it runs well!
The GMA 950 chip is excellent, I love it, it is fast enough and doesn't run hot and doesn't require much power, so battery life is prolonged.

---

### Post by forbes on 2006-05-21
thanks Jeroen,

are you running xgl or aigxl?

what drivers are you using? did you have to install any 3rd party binaries ones?

Anyone got any experience with this on Apple gear?

---

### Post by amitofu on 2006-05-30
I have aiglx and compiz running on my MacBook. No binary drivers required. The open source intel ones are great as Jeroen said.

Other than sleep and the iSight, the MacBook is fully supported by Linux. This is all with BIOS emulation, not EFI.

---

### Post by dijitao on 2006-05-30
Can you or someone else who's setup Ubuntu on a Macbook (non-pro) using BIOS emulation write an article in the Wiki documenting the process?  I'm sure I'm not the only person who's on the fence about getting a Macbook and seeing the exact steps needed to do this would help alot.

Also are you doing this using Dapper or 5.10?

---

### Post by forbes on 2006-06-27
Just to let everyone know, in case you are still searching for an answer to this, I installed AIGLX and compiz last night and it flies along quiet happily :) 

Apparently XGL is real slow on the MacBook, but AIGLX certainly works for me.  Either way you still get the great compiz effects :D 

I followed the instructions on this blog and added it to my dual boot black MacBook (with 2GB RAM) last night on an Ubuntu Dapper 6.06 install. Fantastic.

Just find the section under “3D Accelerated Desktop/aiglx compiz:” over here:  

[http://bin-false.org/?p=17]("http://bin-false.org/?p=17")

Only took about 30 minutes.

---

### Post by sooperhooper on 2006-12-15
I've got Edgy running on my MacBook (not pro), and I have a couple of questions:

1. I've tried so many things in the past two hours or so that I can't remember if I've got aiglx or not. How can I tell?

2. I tried the walkthrough for accelerated graphics at [http://bin-false.org/?p=17](http://bin-false.org/?p=17) , and it screwed up X. I've since undone all the changes. What can I do?

Thanks.

---

