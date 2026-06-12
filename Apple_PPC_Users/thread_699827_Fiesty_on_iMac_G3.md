---
title: "Fiesty on iMac G3"
date: 2008-02-17
forum: Apple PPC Users
---

### Post by Drakeb on 2008-02-17
hello,

I have an iMac G3 (m5521) that I want to install Festy or Gutsy on. I have tried to install both but I am having boot problems. I have read the "Do not hit the Update Button in Gutsy" and it seems like I am not the only one who is having problems installing on an iMac G3.

I have 320mb of RAM, and a 20 GB Harddrive. 
When I boot from the CD, it brings me to a screen that it wants me to load an image, I have hit both install and install video=ofonly and i still have had problems. It will load them to that point and then will turn of the Harddrive and sit there with its power light glowing stupidly at me. I have even tried download the image again. 

I have used slow burn speeds as well as better media. I just hope that this is not another PLBKAC moment.

Any help would be appreciated.
Thanks in advance

Drakeb

---

### Post by stmiller on 2008-02-17
Check out the powerpcfaq for Ubuntu at the sticky at the top of the forum. There are some specific hints to get the install going on a G3 iMac.

---

### Post by stream303 on 2008-02-18
I wonder if your G3 is suffering from that 8GB partition limitation?

Can you try partitioning the disk so that Ubuntu resides in say the first 7.5 gb or so of the disk and try again?

Just guessing, but this has been a known issue for the Rev A/B/C/D early G3 iMacs.

---

### Post by Drakeb on 2008-02-18
Thanks. 
 I don't think it is a partioning problem because it only boots to the yaboot loader and when I hit enter, it says something to the effect of please wait. It then shuts down and the power light/switch just glows.

my next step is to goto the powerpc faq. I will see if that helps

thanks
Drakeb

---

### Post by stream303 on 2008-02-18
You're right.  I found an article here and the last message in the thread indicates that you shouldn't have the 8gb limitation with the M5521:

[http://forums.macosxhints.com/showthread.php?t=76474](http://forums.macosxhints.com/showthread.php?t=76474)

Although it does point to a firmware update for OSX.  Not sure if this would affect Ubuntu.

[http://docs.info.apple.com/article.html?artnum=75130](http://docs.info.apple.com/article.html?artnum=75130)

---

