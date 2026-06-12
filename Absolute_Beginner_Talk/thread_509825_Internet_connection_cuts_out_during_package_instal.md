---
title: "Internet connection cuts out during package installs"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by RandomGameR on 2007-07-25
Hi all.  I'm having way more problems than I expected in installing kubuntu on my new laptop.  I am finally almost to a point where I can use my machine.

The laptop is a Toshiba exactly as described here : [http://www.toshibadirect.com/td/b2c/pdet.to?seg=HHO&poid=383433&coid=-33936]("http://www.toshibadirect.com/td/b2c/pdet.to?seg=HHO&poid=383433&coid=-33936")

My current problem that I am focusing on is getting the wireless networking to work properly.  So far I have followed the steps outlined [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty") in order to use ndiswrapper and the drivers appropriate to my card.  That works fine, allowing me to connect to the internet through my router.  The problem is that whenever I try to apt-get or use adept or any package installation programs the connection to the internet cuts out.  I am still seemingly connected to my router and my other computer (windows xp install) still has wireless internet connection that works.  This is making it difficult to update or install software (I haven't had a success yet).

I get no error messages and it doesn't cut out in the same place twice.  Is this a problem anyone else has had?

Thanks in advance,

_Randy

---

### Post by Pragmatist on 2007-07-26
Do you eventually get your connection back when you reboot?

---

### Post by RandomGameR on 2007-07-26
> **Pragmatist said:**
> Do you eventually get your connection back when you reboot?

Well, I had to add ndiswrapper to the modules that get loaded on boot-up but yes it would come back when I reboot.

It would also come back sometimes if I disabled and then re-enabled the wireless connection.  Finally it would come back if I sudo modprobe -r ndiswrapper followed by a sudo modprobe ndiswrapper.  Then I'd have to close and open the KNetworkManager.

At this point, however, I've made things worse.  I clicked manual configuration and modified the settings for the wifi device.  At this point it won't connect at all and I cannot figure out how to get KNetworkManager to reset to the original settings (default button is greyed out).

Anyone have any suggestions?

---

### Post by RandomGameR on 2007-07-27
Sorry to bump this.  Does anyone have any generic network manager trouble shooting or linux network links that they swear by?  I'm at a loss so far.

---

### Post by Pragmatist on 2007-07-27
Have you tried the wiki?
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles)

---

### Post by RandomGameR on 2007-07-27
Hmm, information in the wiki has gotten me back to my original broken state.  Thanks for drawing my attention to it.  I´m still having problems with my network connection cutting out.  I´ve found that when the connection cuts out I can´t access the router´s login page, which would imply that I am not still connected at all.

---

### Post by RandomGameR on 2007-07-27
[This seems to be the same problem as mine.]("https://answers.launchpad.net/ubuntu/+question/8861")  I´m not sure how to solve it still.  What is the stack size that he´s talking about?

---

### Post by Pragmatist on 2007-07-27
> **RandomGameR said:**
> [This seems to be the same problem as mine.]("https://answers.launchpad.net/ubuntu/+question/8861")  I´m not sure how to solve it still.  What is the stack size that he´s talking about?

A "stack" is a data structure (a specific mechanism for storing data).  Memory normally uses a stack.  A stack is a pile and the last thing you put on it (called a "push") is the first thing that comes out (called a "pop"):

INPUT   ---->   STACK (normally this is depicted vertically, but this silly ubuntu editor is getting it wrong)
A                     A
B                     BA
C                     CBA

So with memory, the last information stored is the first information retrieved.  The author of the bug report is hypothesizing that the problem has to do with "stack size".  With ndiswrapper you are simulating the windows driver (a wrapper is a way to make something look "native" to another OS).  Apparently the windows driver expects a stack of one size and the application thinks it is a different size.  This can lead to an "overflow".  Think of a glass of water.  If you are pouring somebody a glass of water, but you think they have a large glass when they really have a small glass, you will pour too much water and it will overflow the glass and spill all over the floor.  If this happens to a program, the program must close, either by crashing or, if it is a well-written program,  by just closing.

I don't know if this  guy is right or not, but that seems to be what he is talking about.

---

### Post by RandomGameR on 2007-07-27
Thank you for the explanation, though that much I think I understand.  The question I have, though, is how do I fix it?

I've done some more searching around and there is mention of a 16kstacksize patch for the linux kernel that I can apply before recompiling the ndiswrapper.  I haven't compiled the kernel before, nor do I know where to get said patch or what implications the patch might have.  Is there good information on this type of thing somewhere?

Thanks again.

---

### Post by Pragmatist on 2007-07-27
> **RandomGameR said:**
> 
Thank you for the explanation, though that much I think I understand.  **The question I have, though, is how do I fix it?**

Your welcome.  Often an OP doesn't ask the question he intends.  *"What is the stack size that he´s talking about?"*  is vague and implies you don't understand what a stack size is.  *"[Here is a link with a similar, but unsolved, problem.]  Does anybody know how to fix it?"* is a clearer question.  Anyway, I'm just pointing this out to save time for you and for others.

> **RandomGameR said:**
> ....I haven't compiled the kernel before....16kstacksize patch for the linux kernel....
Read this:
[https://wiki.ubuntu.com/KernelPatches?highlight=%28kernel%29](https://wiki.ubuntu.com/KernelPatches?highlight=%28kernel%29)

If you still want to do it, you definitely could find instructions using google.

> **RandomGameR said:**
> ....nor do I know where to get said patch or what implications the patch might have. Is there good information on this type of thing somewhere?
I'm sure, google around and you should find what you need.  If you want to see if someone in the forums has done what your trying to do, you'll get more results if you make a new thread with a relevant title ("16stacksize patch for linux kernel" or "how to patch a kernel" or "ndiswrapper and kernel patch" etc....)

---

### Post by RandomGameR on 2007-07-27
Thanks for your suggestions.  I'll post a new thread.  Ultimately I don't want to patch the kernel.  I just want things to work, and right now they don't.  The only two possible fixes I've seen by googling have both required a kernel compilation and one is claimed to be very unstable, while the other (the 16k stacksize patch) seems to be more stable.

Anyway, again, thanks.

---

### Post by ev5unleash1 on 2007-07-27
This may be because Bluetooth Dongle is active on the machine therefore interfearing with the Wi-FI or that Ubuntu does not not have the proper driver for the Wireless Adapter.

---

