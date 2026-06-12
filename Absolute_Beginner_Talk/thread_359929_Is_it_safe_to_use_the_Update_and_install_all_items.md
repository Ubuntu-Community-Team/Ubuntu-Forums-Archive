---
title: "Is it safe to use the Update and install all items on the list?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-12
Is it safe to update everything on the "Update" list if I want some or all of the items listed? :confused:

---

### Post by Paerez on 2007-02-12
All the updates put on the update list are generally (99.9%) safe. If you want the crazy and new unsafe stuff, you have to go out of your way to install ubuntu's betas (the current is feisty fawn). So you can choose to update only the things you want, or just update everything.

I just update everything all the time.

It is probably unsafe to not upgrade the kernel, because there are often security fixes in those. The kernel updates are in the "linux-image-*" packages.

---

### Post by Sunflower1970 on 2007-02-12
If it's a kernel upgrade, just be aware there's a possibility that you may have to reinstall the drivers for your graphics card and wireless.

---

### Post by kittyhawk63 on 2007-02-12
Thanks for this info. If I ever find something "buggy" how do I go about fixing or deleting it from my system?

---

### Post by kittyhawk63 on 2007-02-12
> **Sunflower1970 said:**
> If it's a kernel upgrade, just be aware there's a possibility that you may have to reinstall the drivers for your graphics card and wireless.

What exactly is a "kernel"? I keep seeing that referenced. It is the basic operating system to Linux?

---

### Post by mikewhatever on 2007-02-12
No. People around are having issues with the latest kernel update, which is 2.6.17-10 --> 2.6.17-11. If Ubuntu is your main system, do not update, unless you have the time to fix it, something like over the weekend. You will need to reinstall all third party/propriatory modules previously installed. If you do not know what that is, a good idea is not to update at all, but lock the kernel to prevent any kernel updates. It is kind of a gamble though, since some users, I don't know what percentage, have had not problems at all.:confused:

---

### Post by kittyhawk63 on 2007-02-12
> **mikewhatever said:**
> No. People around are having issues with the latest kernel update, which is 2.6.17-10 --> 2.6.17-11. If Ubuntu is your main system, do not update, unless you have the time to fix it, something like over the weekend. You will need to reinstall all third party/propriatory modules previously installed. If you do not know what that is, a good idea is not to update at all, but lock the kernel to prevent any kernel updates. It is kind of a gamble though, since some users, I don't know what percentage, have had not problems at all.:confused:

How do I "lock" the kernel? What is the kernel anyway? See my last post.

---

### Post by Sunflower1970 on 2007-02-12
This is from wiki:

[http://en.wikipedia.org/wiki/Kernel_(computer_science](http://en.wikipedia.org/wiki/Kernel_(computer_science))

---

### Post by banditti on 2007-02-12
More on the kernel:

[http://en.wikipedia.org/wiki/Kernel_%28computer_science%29]("http://en.wikipedia.org/wiki/Kernel_%28computer_science%29")


My .02 on the upgrade.  I have not had a problem, but many have.

---

### Post by banditti on 2007-02-12
Sunflower, that is funny.  You are obviously a faster typer.

---

### Post by kittyhawk63 on 2007-02-12
[QUOTE=banditti;2146136]More on the kernel:

[http://en.wikipedia.org/wiki/Kernel_%28computer_science%29]("http://en.wikipedia.org/wiki/Kernel_%28computer_science%29")
 
Thanks. Good read. Answered my question.

---

### Post by kittyhawk63 on 2007-02-12
How do I install Mozilla Thunderbird into Ubuntu?

---

### Post by mikewhatever on 2007-02-12
> **Paerez said:**
> All the updates put on the update list are generally (99.9%) safe. If you want the crazy and new unsafe stuff, you have to go out of your way to install ubuntu's betas (the current is feisty fawn). So you can choose to update only the things you want, or just update everything.

I just update everything all the time.

It is probably unsafe to not upgrade the kernel, because there are often security fixes in those. The kernel updates are in the "linux-image-*" packages.

That statement seems to be groundless, in view of numerous problems triggered by the kernel update. It is probably based solely on personal experience, and while I am very glad you haven't had any problems yet, looking through the posts of last few days would show that others are not that lucky.

---

### Post by Sunflower1970 on 2007-02-12
> **banditti said:**
> Sunflower, that is funny.  You are obviously a faster typer.
:biggrin: That's what I do most of the day..Type...

---

### Post by kittyhawk63 on 2007-02-12
If I downolad something, and find it buggy, how do I uninstall it? Do I use the add/remove just like in Windows?

---

### Post by mikewhatever on 2007-02-12
> **kittyhawk63 said:**
> If I downolad something, and find it buggy, how do I uninstall it? Do I use the add/remove just like in Windows?

If that's the kernel update you're talking about, there may not be any add/remove. You may end up against a black screen with funny looking white window saying 'xserver failed to start, do you what to diagnose it', or something of the sort.

---

### Post by bobbob94 on 2007-02-12
Though if you do get problems after the kernel upgrade you should be able to select the previous kernel from the grub boot menu as a temporary way to get your desktop back while you come back here and try and sort it out properly...

---

