---
title: "[SOLVED] Is it possible to run a &amp;quot;virtual mac&amp;quot; on my linux desktop?"
date: 2008-07-31
forum: Apple Hardware Users
---

### Post by skelooth on 2008-07-31
**Solution: I'm not going to bother**

Hello all, I tried some googling but the results weren't spectacular or very hopeful. I was hoping maybe one of you know something more than I was able to find.

Basically I'd just like to either run mac in a virtual desktop on top of linux if possible, or duel boot if it's not. I've run into a problem that some of the javascript code I've been writing works well on both windows and linux but bombs out on the macs. I've tried to run it both in safari and firefox on mac but it refuses to work, and I can't sit there and troubleshoot it on a coworker's computer.

Just in case anyone knows: My ajax requests are failing when being called from a child to opener. It works on all other OS's but mac.

---

### Post by skelooth on 2008-07-31
btw I do have access to a legal copy of Mac OS, and would prefer to stay away from any warez. Especially considering this is for a work computer.

---

### Post by toucher5 on 2008-07-31
Have you tried using qemu or virtualbox. it may work. it is available in add/remove program manager. if it is not listed make sure you click the drop down box and select 'all available'. let me know if this works.
:popcorn:

---

### Post by tuxxy on 2008-07-31
I only know of this,

[http://pearpc.sourceforge.net/about.html](http://pearpc.sourceforge.net/about.html)

---

### Post by skelooth on 2008-07-31
Thanks guys, that helps immensely.

---

### Post by cyberdork33 on 2008-07-31
I just want to address the sensitivity here on this issue.

The legality of running Mac OS on non-Apple hardware (even a legal copy of OS X, or in a VM on non-Apple hardware) is a bit of grey area in the law (the EULA forbids this), and it is the Ubuntuforums position (judging on past action) that installing OS X and such on non-Apple hardware is not tolerated. Please keep this in mind while posting.

That being said, there is no _good_ solution as of yet for running OS X in an emulator / VM. PearPC is probably your closest bet.

---

### Post by tuxxy on 2008-07-31
Do you think I should remove the link then

---

### Post by cyberdork33 on 2008-07-31
> **tuxxy said:**
> Do you think I should remove the link then
as long as we are talking about using PearPC on Apple hardware, I think we are OK.

---

### Post by tuxxy on 2008-07-31
Yes I thought that too, I only provided the link in the first place because I assumed he was using apple hardware :)

---

### Post by skelooth on 2008-07-31
You can remove the link if you like. 

I'm having problems mounting the mac os x leopard install disc. I tried mounting it as auto, hfs, and hfsplus but no luck. It worked seemingly randomly with hfs once, but now I can't get it to mount again.

I have a very big quarrel with Apple's business model, especially the restrictive hardware licensing, but that's a political topic far beyond the scope of me just wanting to debug some javascript and css code.

I don't know what I'm going to do at this point... the Mac's are causing a problem for me both on our intranet site and when viewing our company website. It seems like the only thing I'm going to be able to do is sit down and annoy someone who's on a mac.... ?

Why does apple support open source licensing if it's a proponent of the most restrictive hardware licensing laws ever conceived by our generation?

---

