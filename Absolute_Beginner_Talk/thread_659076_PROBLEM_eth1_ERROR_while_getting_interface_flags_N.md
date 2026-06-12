---
title: "PROBLEM: eth1: ERROR while getting interface flags: No such device"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Canto on 2008-01-05
Hi

As many other ubuntu 7.10 users I have a problem setting up my wireless Broadcom 43xx adapter correctly. I have managed to connect to the internet, but every time I restart my computer I have to reinstall the bcm43xx-fwcutter_006-3_i386.deb package.

When I type
```
sudo ifconfig eth1 up
```

I get the following message:
*eth1: ERROR while getting interface flags: No such device*

To get it working I have to remove the installed package, then reinstall it.

This is getting a bit frustrating, not to mention time consuming... 
I have searched through most of the posts in this forum, but I can't find any solution to my problem. I therefore hope that someone is able to help me out, making the wireless connection to work at boot. 

Thanks in advance

---

### Post by Canto on 2008-01-06
For you who have read the post and thought: "I wish I could help this guy", or "I got the same problem myself", I found a solution.

It looks like I have installed the driver incorrectly, which is not easy to detect since you get no clear warning about this. (When I checked for installation, I got the message that the driver was installed)
> sudo ndiswrapper -i ~/desktop/bcmwl5/bcmwl5.inf
[sudo] password for X:
driver bcmwl5 is already installed


Somehow I had not written the correct path for the driver to be installed, and had to remove it to be able to correct the problem. 
```
sudo ndiswrapper -e bcmwl5

```

---

