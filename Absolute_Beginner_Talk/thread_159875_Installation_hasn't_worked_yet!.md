---
title: "Installation hasn't worked yet!"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by kchukchukchu on 2006-04-13
Hello all, 
first thanks for all your help last night, I successfully burned a CD image.

But now, when the installation was going on,   the installation halted and gave an error message saying can't load initrd/ something.. either during the loading CD after the language selection (before the paritioning) or after partitioning when it was actually "installing the system." 

 I have tried more than 10 times to install and somehow the error of looading happens at these different places.  

I "checked CD integrity" and it said at different places that some file failed the MD5 sum check.

I am planning to reburn another CD, but if any of you have any idea what is going on and what I need to do, I'd greatly appreciate your help.

I also want to ask which linux kernal or which partitioning method I should choose to install, does that matter?  I think I had 3 choices in both cases, and I don't know what the differences are. I'll look it up too but just thought to ask.  

THANKS TONNEs!
K

---

### Post by spiderbatdad on 2006-04-13
sounds like you need to download the iso again, verify it, then burn another cd

---

### Post by kchukchukchu on 2006-04-13
Hello, spiderbatdad, thanks for your quick reply.

I am trying to do that right now,  how do I verify it before I burn it though?

thanks,
k

---

### Post by Mustard on 2006-04-13
This is a general guide...
[https://wiki.ubuntu.com/VerifyIsoHowto](https://wiki.ubuntu.com/VerifyIsoHowto)

Basically you need some type of md5sum checker and you get it to generate the md5 'hash' for the ISO, and compare it to the 'hashes' that are available from the webpage you downloaded the ISO from.  The hashes are a series of numbers and letters.  If the hashes are identical then the ISO has been downloaded succesfully (without corruption).  On windows you could probably find any number of freeware md5sum checkers.  Try looking around on popular freeware websites.

I believe that bittorrent downloads do md5sum checks as they download, so a successful download using bittorrent should ensure that the download is good, without the need for a separate md5sum check.

Then after burning the ISO (at the lowest possible speed), you would verify that burn was succesful, by choosing the verify media options in the install process.

---

### Post by Bartender on 2006-04-13
Kchu -
Are you doing this on a Windows machine?  Herman recently added a Windows-based guide to his site

[http://users.bigpond.net.au/hermanzone/p1.htm](http://users.bigpond.net.au/hermanzone/p1.htm)

Click on the md5 checksum link.  His description is based on the steps you'd take with Md5Summer, one of many Windows-based checksum utilities out there.  We liked it cause it was easy.

---

### Post by kchukchukchu on 2006-04-13
Hello Mustard,

Thank you for your response and explanation!  

OK, I am quite sure that my old CD is corrupt then, because I did use the MD5 checksum on the installation CD to check that CD itself, and it gave me an error.

I just read the link you sent, but I am not sure how to use the script there on a Mac.  I guess I need to find a MD5 checksum for MAC to do this.

OK, I'll go at it again:) !
Kay

---

### Post by kchukchukchu on 2006-04-13
Hi bartender,

Cool, the link that you sent discussed exactly the problem I was having!  THANKS!  

It seems to me that I can just type md5sum as a command in a terminal in MAC OS.   

I am still downloading the iso again, and then I'll check to see if I can just use the MD5sum on the MAC. If it doesn't work, I'll need help again:).  

THANKS A LOT!
 And thanks a lot everyone!

KAY

---

