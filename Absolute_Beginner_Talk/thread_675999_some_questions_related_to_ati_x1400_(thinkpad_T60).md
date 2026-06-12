---
title: "some questions related to ati x1400 (thinkpad T60) and gutsy compiz"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by rache1111 on 2008-01-23
Hi there,

I am trying to get compiz to run on an ati radeon x1400 thinkpad T60 laptop. According to this thinkwiki [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_Thinkpad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_Thinkpad_T60), xorg-driver-fglrx driver and xgl needs to be manually installed. I have a few questions that I hope someone can answer. I am sorry if these question sounds noobish, I am a fresh meat when it comes to linux.

1. How do I find out what kind of drivers are already installed on the system? In windows, there is the device manager. Is there a similar kind of mechanism in linux that will show me the hardware devices and drivers I am currently using?

2. According to the thinkwiki website, the new graphics driver for suspend and resume has a bug in Gutsy so that suspend and resume doesn't work. The work around is either to install an relatively new unstable driver, or compile a custom kernel. Is this still the case? How difficult would it be for me, a newcomer, to figure out how to compile and install a custom kernel following the guide?

Edit. After reading through this site describing the ati bug [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653) some one mentioned that they solved the problem using the "hardy kernel".
qoute 
      "IBM Thinkpad T60p, with an ATI Mobility FireGL V5200. Software stack is now a fresh Gutsy install, with the kernel upgraded to the Hardy kernel (2.6.24-4) using the mechanism suggested by Rocko, and the latest (8.01) proprietary ATI fglrx    
      drivers manually installed. I now have working hardware acceleration, with both compiz-fusion (set to full effects) and suspend/resume apparently working cleanly. I will need to wait until I get into the office tomorrow before I can try the VGA 
      port to see if I get a working secondary display too, but at the moment it's looking *extremely* promising."

Can some one be kind enough to explain what this hardy kernel is? Is this some sort of custom kernel that I have to build by myself?

Thank you very much!

---

### Post by Liam-Gorham on 2008-01-23
I'm afraid i cant help you with the second question but i can help you with the first. To find if any of the drivers are already in place go to- system, administrator and then restricted drivers manager. IF nothing appears in there then no drivers are present.

Hope this helps.

---

### Post by rache1111 on 2008-01-23
Thanks for the info Liam-Gorham.

Does anyone know a bit more about this topic?

---

### Post by eggdeng on 2008-01-23
Hardy is short for Hardy Heron, the next long term support release of ubuntu due out in April, hence also known as 8.04. The posters you mentioned were using alpha (pre-release) versions.
To know which driver you are using, type in a terminal
```
cat /etc/X11/xorg.conf | grep Driver
``` You should see an entry specifying ati, radeon or fglrx. The last is the proprietary restricted driver.
If you do have it installed run
```
fglrxinfo
``` 
to see which version.
I am running beryl (previous version of compiz fusion) on 6.06 on an ATIX1400.  My fglrx driver version is 8.25.18 (it works pretty well, except for full-screen DVD and suchlike) and I have never been able to get it to work with more recent drivers.
From what I have seen, this seems to be the general tonic for x1300 and x1400s. Until now, the best advice has been to stick with either this or the previous version.

---

### Post by rache1111 on 2008-01-23
Thank you eggdeng.

I have installed the fglrx restricted driver as well as reinstalled glx. Now compiz fusion seems to be working correctly.

for your info the fglrxinfo output is:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)


However, as expected, suspend doesn't work anymore. The computer will hang when it tries to go into suspension and the only way to get back into the OS is through a hard reset.

I heard that the new driver available on the ati website claimed to have fixed this problem: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html), I will try to install them using this guide

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a)
and let you know if it indeed does fix the suspension problem.

I do have another question:
I heard that there is a catalyst control center for Ubuntu, do I have to install that separately or is that piece of software already available as part of Ubuntu? If so, how can I run it? The reason I am interested in running ccc is to reduce power consumption on battery.

Thanks again!

---

### Post by eggdeng on 2008-01-23
So you got the newer drivers to work, that's interesting. As for the catalyst control center, I have never used it but you might take a look at [http://www2.ati.com/drivers/linux/linux_8.37.6.html]("http://www2.ati.com/drivers/linux/linux_8.37.6.html") I just took a second look at this & I see support for the x1300 but not the x1400.:confused:

---

### Post by rache1111 on 2008-01-23
well, I just finished installing the latest driver from ati and boy its bad! Things became much slower and suspension still doesn't work! I guess there is a reason why they didn't include it into the Ubuntu repository.

Now I just need to find out how to revert back to the original driver...
It saddens me that for every Ubuntu release it seems as though ati graphics cards are never properly supported.

Edit. Help can someone help me with restoring to the previous driver? I followed the instructions on this page:[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9), but the terminal is telling me that I already have the latest driver and wouldn't install again!

---

### Post by unbuntu on 2008-01-24
I have Thinkpad T60p (ATI FireGL 5250)  The suspension never worked and I just learned that the new ATI driver came out this month and supposedly fixed the suspension problem...I was excited until I read your post that the new driver still doesn't work...bummer!

---

### Post by eggdeng on 2008-01-24
You have to make sure you are starting with a clean slate, otherwise the old install will conflict with the new.
```
sudo apt-get --purge remove  fglrx-kernel-source fglrx-control xorg-driver-fglrx xserver-xorg-video-ati
``` should get rid of everything. Then install the driver as you did before.

---

### Post by amd-64 on 2008-04-02
rache1111

I have a T60 with X1400. I can suspend and resume perfectly in Gutsy, although sometimes the laptop sleeps immediately after resume and then resumes properly. See my post [http://ubuntuforums.org/showthread.php?t=729558](http://ubuntuforums.org/showthread.php?t=729558)

I have tried many things so not sure what you are doing differently. You should try the different hibernate methods swsusp, hibernate, suspend2-userui. I attached my config files located in /etc/hibernate for reference. To view the files, first download inside of a temp directory or the desktop, then use gunzip hibernate.gz. To compare to your files, use a  tool such as diff or kdiff3. Please note that my wireless modules and interfaces may be different from yours. 

You do not need to remove ati drivers from linux, you can simply disable the restricted ones from /etc/default/linux-restricted-modules-common

Also, make sure you have the following lines in /etc/hibernate/common.conf

### vbetool
 EnableVbetool yes
 RestoreVbeStateFrom /var/lib/vbetool/vbestate
 VbetoolPost yes
 RestoreVCSAData yes

---

