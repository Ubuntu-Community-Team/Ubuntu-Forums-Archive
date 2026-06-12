---
title: "Necessary for Swap partition?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by pencil86 on 2007-08-25
In windows, you would have a pagefile in the same partition...in Linux, is that possible or do you need to create a separate SWAP partition?

I have 8gigs of ram....what size (in MB) should I set my swap file to?

---

### Post by pgar23 on 2007-08-25
8 GB is way to much...you should need no more than 1 GB. you can go to google and check conversion rates of GB to MB.

Also, excuse my ignorance but what is a pagefile?

---

### Post by chrome307 on 2007-08-25
Linux uses RAM in a different way compared to Windows .......... however 8GB is huge amount of RAM .... maybe you could adjust the size of your SWAP partition with Gparted?

---

### Post by Mogurijin on 2007-08-25
8gigs is a LOT. But how different is a Linux swap file from a Windows pagefile? Also, I know I never seem to use my swap file (System Monitor never shows any usage) and only about 20~25% of my memory at a given time and I only have 1 gig.

---

### Post by NovaAesa on 2007-08-25
I depends what you use your computer for. 8GiB sounds like alot though, so I'd doubt you'll need much swap space. If you want to use hibernate, you should use at least 8GiB swap space, but otherwise set it to something conservative - maybe 512MiB or 1GiB.

---

### Post by AndyCooll on 2007-08-25
The rule of thumb is twice the size of your RAM. However ...and it's a big however ...anything over 1gb is likely to be surplus to requirement. Swap is only used when RAM hungry apps need more memory than your system can cope with. If you have 8gb of RAM this is extremely unlikely to happen in your situation, so set it low.

:cool:

---

### Post by pencil86 on 2007-08-25
I should mention that in my windows installation, I run atleast 2-3 virtual machines (vmware)...I run one for MS SQL 2005 database server, one for IIS and .NET, and another for testing applications.

Do you think 2gig is enough? With Vista Ultimate x64, it set my pagefile (swap in windows) to 12gigs.

---

### Post by jordanmthomas on 2007-08-25
Yes, you can use a swap file instead of a swap partition:
[http://blog.mypapit.net/2007/07/how-to-add-linux-swap-file-if-you-dont-have-swap-partition.html](http://blog.mypapit.net/2007/07/how-to-add-linux-swap-file-if-you-dont-have-swap-partition.html)
Here's how

---

### Post by mcduck on 2007-08-26
While you probably won't ever need any swap with 8GB of RAM, you should keep in mind that using suspend-to-disk requires you to have at least as much swap as you have RAM (because suspend-to-disk writes everything from your RAM to swap)..

---

