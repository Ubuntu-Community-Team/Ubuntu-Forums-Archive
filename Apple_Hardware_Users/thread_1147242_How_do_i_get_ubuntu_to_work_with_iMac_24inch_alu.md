---
title: "How do i get ubuntu to work with iMac 24inch alu?"
date: 2009-05-03
forum: Apple Hardware Users
---

### Post by noice742 on 2009-05-03
Hello!
Yesterday I installed Ubuntu on my "top of the line" iMac 24 inch that you can buy now from apple.

It went good with bootcamp. But I could not get the graphics or sound to work. I tried posting in a few ubuntu forum's , but didnt get to much help. So i deleted ubuntu. I gave up , from searching on google and asking in forums. 

But I want to try it again, but this time i was thinking that i might try to find out everything before I install it with bootcamp.

So I know what to do from the start.

Can anyone be so kind and nice to tell me how to get everything working with my imac?
Step by step, 'couse i am new to linux.
There must be someone else with the same computer as me, that is running Ubuntu!

Please help :D


My 24inch iMac alu spec is :

3.06 GHz Intel Core 2 Duo
4 GB 1067 MHz DDR3
1 TB HDD 
512 MB NVIDIA GeForce GT 130

Thank you so much for any help!

---

### Post by cyberdork33 on 2009-05-03
probably won't get much specific help unless you install and ask about a specific issue.

General Installation Instructions are here:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

and more specific instruction can be found here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

Unfortunately, there is not a lot of specific info about the iMacs.

---

### Post by noice742 on 2009-05-04
Okay I guess it seems to hard to find out how to make everything to work, when there is no info about the imac i am using. I find it kinda strange, someone must use ubuntu also? 
I have been looking on Linux mint, and i might try that and hope things will work better there.
And yes, I know its based of ubuntu, but i figure i got nothing to loose. 
If that does not help me , i will try ubuntu some more. I really wanna learn how to use it!
:)

---

### Post by jamesey on 2009-05-04
I have an iMac 9,1. I'm assuming if you just bought your iMac off the apple website, you do too. Do the following. 

To determine which version / generation / hardware revision your Mac is:

```
under OSX; either click in OS X on the Apple on the top left, then "About this Mac" -- "More Info...", see the generation in the "Model Identifier" row; or run in a terminal:

sysctl hw.model

under Ubuntu; you can find out what model and generation you have, by typing at the terminal:

sudo dmidecode -s system-product-name
```




1. have you tried using rEFIt? 

2. Your speakers probably wont work even if you do get Ubuntu working. Your headphone jack will. A patch is being worked on that will get released soon and get the speakers working.

---

### Post by noice742 on 2009-05-04
> **jamesey said:**
> I have an iMac 9,1. I'm assuming if you just bought your iMac off the apple website, you do too. Do the following. 

To determine which version / generation / hardware revision your Mac is:

```
under OSX; either click in OS X on the Apple on the top left, then "About this Mac" -- "More Info...", see the generation in the "Model Identifier" row; or run in a terminal:

sysctl hw.model

under Ubuntu; you can find out what model and generation you have, by typing at the terminal:

sudo dmidecode -s system-product-name
```




1. have you tried using rEFIt? 

2. Your speakers probably wont work even if you do get Ubuntu working. Your headphone jack will. A patch is being worked on that will get released soon and get the speakers working.


Hi and thanks for the best answer i have recived so far.
Yes, I have an iMac 9,1 - same as you do.

And yes, I was using rEFIt to be able to choose if i wanted to boot into osx or linux.

Where can I follow the process for the patch, so I can see when it will be released?
I will wait until that day comes, 'couse right now i have only mac osx installed.

---

### Post by noice742 on 2009-05-06
Bump for where I can follow the process about the patch to be released?

---

### Post by cyberdork33 on 2009-05-06
I think this is the bug:
[https://bugs.edge.launchpad.net/mactel-support/+bug/346170](https://bugs.edge.launchpad.net/mactel-support/+bug/346170)

---

### Post by noice742 on 2009-05-07
Thank you.

---

