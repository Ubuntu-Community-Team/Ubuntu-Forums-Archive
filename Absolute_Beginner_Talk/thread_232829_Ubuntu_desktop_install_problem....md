---
title: "Ubuntu desktop install problem..."
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by tempus on 2006-08-09
Ok I have the latest Ubuntu release 6.06 desktop and I am unable to install it permanently. When I select install it begins then I get a message <ACPI: Unable to locate RSDP>. How do I get it to install? TIA:D

---

### Post by xpod on 2006-08-09
Had the exact same problem on my older pc.....Never did find out exactly what it was.Theres a couple of bits and pieces if you google it but not much.

Personally i ended up installing the kbunto alternate cd after many trys with ubunto and even xubunto.

Would still like to know what it was though

---

### Post by bscbrit on 2006-08-09
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=301711](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=301711)

This explains the problem and the cure - it suggests using the Alternative Install CD.

I've got several very old computers that give the same error but they have never stopped me from installing.  Perhaps this is something that has appeared with Dapper?

---

### Post by xpod on 2006-08-09
yeah that was all i found.Even though i got the error message with my initial attempts with ubunto and xbunto it still then went ahead and tried to setup but they just ended up hanging at the latter stages.

I believe i still got the message with the successfull Kbunto live cd setup but i still was able to install okay.

I had to skip a couple of software sections if i remember but you can just rectify that once your up and running

---

### Post by tempus on 2006-08-09
Ok I solved the problem in a left handed fashion. I installed the previous version of Ubuntu and then updated the version via the version updater. It worked like a charm! But now when I boot the computer I have quite a selection of versions to boot to. How does one get rid of the non relevant boot selections in the boot menu?:)

---

### Post by davebgimp on 2006-08-09
> **tempus said:**
> Ok I solved the problem in a left handed fashion. I installed the previous version of Ubuntu and then updated the version via the version updater. It worked like a charm! But now when I boot the computer I have quite a selection of versions to boot to. How does one get rid of the non relevant boot selections in the boot menu?:)

You can remove them via Synaptic. As a rule of thumb, I always leave at least one old one in case something goes awry, I can boot to it until the problem's solved.

Make sure you don't try and remove the kernel you're currently using.

---

### Post by tempus on 2006-08-09
> **davebgimp said:**
> You can remove them via Synaptic. As a rule of thumb, I always leave at least one old one in case something goes awry, I can boot to it until the problem's solved.

Make sure you don't try and remove the kernel you're currently using.

Synaptic? Is that in Ubuntu? I am a dummy when it comes to Linux.](*,)

---

### Post by davebgimp on 2006-08-09
> **tempus said:**
> Synaptic? Is that in Ubuntu? I am a dummy when it comes to Linux.](*,)

Yes, it's a GUI package manager.

My advice since you're unfamiliar with Ubuntu is to let it be for now. Those kernels aren't going to hurt anything. Get to know Synaptic (you'll find it in your program menus) and when you get the hang of it, you can search for linux-image and it will list all the kernel versions, the newest being the one you are using unless you manually change the boot order-which you have not.

---

