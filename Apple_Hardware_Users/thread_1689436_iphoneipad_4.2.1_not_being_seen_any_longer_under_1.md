---
title: "iphone/ipad 4.2.1 not being seen any longer under 10.04"
date: 2011-02-16
forum: Apple Hardware Users
---

### Post by yunone on 2011-02-16
i just upgraded both my iphone and ipad to iOS 4.2.1 and neither are being seen under 10.04. Before they were seen and i was able to search the directories of both devices from the desktop, but not anymore... has anyone else run into this issue? 

the iphone charges fine on USB, the ipad never did...just no longer show up


Windows 7 has no issues with seeing the device and browsing directories, same machine as the Ubuntu 10.04 issue

thanks in advance

---

### Post by yunone on 2011-02-16
confirmed the issue on 10.10 as well

attached is a screenshot of the error i get in 10.10... no error in 10.04

---

### Post by yunone on 2011-02-16
problem solved



To correct this problem, open your terminal and copy/paste the following:

sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade


After this you may have restart your system. Now your iPhone will mount without any errors.

---

### Post by Sudaya on 2011-04-21
I have exactly this problem and the answer given does not work. It seems that the pmcenery ppa has moved. I get 404 not found messages when I try to load them. Any updates? Thanks

---

### Post by yunone on 2011-04-21
> **Sudaya said:**
> I have exactly this problem and the answer given does not work. It seems that the pmcenery ppa has moved. I get 404 not found messages when I try to load them. Any updates? Thanks

doesnt help you with 10.04, but i know in 10.10 the issue is resolved....

---

### Post by Sudaya on 2011-04-21
> **yunone said:**
> doesnt help you with 10.04, but i know in 10.10 the issue is resolved....

Ah, but I am using Joli OS, which is basically 10.04. What is the solution? Thanks

---

### Post by Sudaya on 2011-04-21
> **yunone said:**
> doesnt help you with 10.04, but i know in 10.10 the issue is resolved....

Ah, but I am using Joli OS, which is basically 10.04. What is the solution? 

I have just discovered that SHOTWELL (PHOTO MANAGER) can access the images on my iphone. But Rhythmbox and VLC can't find any music. No connect message appears in Joli. Something IS working, but not enough...
thanks

---

