---
title: "snag installing openchrome"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-02-19
I was installing openchrome for my KM400A per this instruction :

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

I got all the way down to "For chipsets different from K8M890 get the openchrome sourcecode"

When I run "svn co http://svn.openchrome.org/svn/trunk/"  I get the following message :

bash: svn: command not found

Help.....what do I do now?

I have an ABIT VA-20 motherboard with the KM400A on it and my Kernel is 2.6.15-28-386 using Dapper 6.06.1 LTS

---

### Post by rggavubt on 2007-02-19
I got openchrome installed finally.  I checked the packages that I thought I had already installed and found out in synaptic that they were not installed.  I reinstalled all of them and everything went per the instruction.  My graphics are 100% better.  The instruction said to edit the Xorg file and change under the Device section Driver from "blahblah" to "via"....mine was already via so I exited with no changes.  Everything works greeeeaaaaat!

---

### Post by n8bounds on 2007-02-19
I had never even heard of openchrome before reading your post...

---

### Post by rggavubt on 2007-02-20
I have been reading the posts on Unichrome Pro video drivers, which I have and found out that Openchrome is what you install to handle these video drivers.  I was kind of reluctunt to install them because I didn't want to lose my video but it worked out great.  I was afraid that I would come up with a blank screen with no way to fix it.  My video is so much clearer now.

---

