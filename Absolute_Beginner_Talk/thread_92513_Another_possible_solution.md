---
title: "Another possible solution?"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by deNoobius on 2005-11-19
**THIS IS SOLVED**
I've written about my printer woes in another thread.  Is it possible that I could use Wine or something similar to run the Windows drivers for this printer in Ubuntu?  Or would that just lead to more frustration?

Another thing I've thought of is to use an ethernet cable to attach the printer to my wireless router and use CUPS.

---

### Post by thomas.mcmahon on 2005-11-20
Hi there,

Although I don't have a lot of experience using printers with Linux, I have gotten my Girlfriends printer to work using CUPS by printing over the network, so that's what I'd try first.

Good luck :)

---

### Post by deNoobius on 2005-11-20
Thanks--I am working on that idea now.  I've gotten the printer's address from the CUPS page, and applied it in System -- Administration -- Printers.  I am at least getting a response--the following error message:

Ready: Network host '192.168.1.101.631' is busy; will retry in 30 seconds...

This is actually the best I've done and it indicates to me that the system is not finding the printer for some reason.   I'm going to try rebooting everything and see if that fixes things.

Anyone has any other ideas on solving this error, I'd appreciate it.  I can't tell you how grateful I am for the help with my other issues--the dual boot and the FAT 32 shared file, to name the two big ones.

[BORING PERSONAL DETAILS FOLLOW]

I'm THIS CLOSE (holds up two fingers) to having a fully functional Ubuntu system.  I've solved (okay, people responding to me have solved) all my other major issues.  Unfortunately, if I have to keep switching back to Windows to use the printer, Ubuntu won't be that useful for me, although I may play around with it a bit just for the learning experience.

I don't really like having Windows running all the time on a computer I don't actually work at all that much because of the constant need for security patches and the overall risk to the home network, so I was really hoping Ubuntu could largely run this machine without much human intervention, once it was set up.

---

### Post by deNoobius on 2005-11-20
OK, tried rebooting, tried adding a "/" at the end of the printer's address, tried using the CUPS page directly.

What happens now is that the print job seems to go to the printer, the monitoring window shows the job, and the printer just sits there.  

I've tried everything I can think of or find on the web on getting this printer to work (except for using the Windows drivers, which I guess is my next thing)...is it possible it just can't work in Ubuntu?

---

### Post by thomas.mcmahon on 2005-11-20
What is your printer?

---

### Post by deNoobius on 2005-11-20
My printer is the Samsung CLP 510N, which is a relatively inexpensive laser printer.  Thanks for trying to help!

When I try to untar the Linux driver that Samsung provides, here is the result.  Maybe I'm doing something wrong?

$ sudo tar zxf 20050322102424156_lpp-1.1.4-19-i386.tar.gz
tar: image/help/C/config-tool.html: Cannot open: No such file or directory
tar: image/help/C/index.html: Cannot open: No such file or directory
tar: image/help/C/llpr.html: Cannot open: No such file or directory
tar: image/help/C/llpr-properties.html: Cannot open: No such file or directory
tar: image/help/C: Cannot utime: No such file or directory
tar: image/help/C: Cannot change mode to rwxr-xr-x: No such file or directory
tar: image/help/C: Cannot change ownership to uid 0, gid 0: No such file or directory
tar: image/ppd/C/CLP-500splc.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-1210spl.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-1430spl.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-1440spl.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-1450pcl.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-1450ps.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-1450spl.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-1510spl2.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-1710spl2.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-1750spl2.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-2150ps.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-2150spl2.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-6060pcl.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-6060ps.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-7300pcl.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-7300ps.ppd: Cannot open: No such file or directory
tar: image/ppd/C/cms: Cannot mkdir: No such file or directory
tar: image/ppd/C/cms/CLP-500cms: Cannot open: No such file or directory
tar: image/ppd/C/cms/CLP-500cms2: Cannot open: No such file or directory
tar: image/ppd/C/cms/CLP-510cms: Cannot open: No such file or directory
tar: image/ppd/C/cms/CLP-510cms2: Cannot open: No such file or directory
tar: image/ppd/C/ML-2550ps.ppd: Cannot open: No such file or directory
tar: image/ppd/C/CLP-550ps.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-1740spl2.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-2550Sps.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-2550Sspl2.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-2250spl2.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-1520spl2.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-2560ps.ppd: Cannot open: No such file or directory
tar: image/ppd/C/CLP-510splc.ppd: Cannot open: No such file or directory
tar: image/ppd/C/ML-1610spl2.ppd: Cannot open: No such file or directory
tar: image/ppd/C: Cannot utime: No such file or directory
tar: image/ppd/C: Cannot change mode to rwxr-xr-x: No such file or directory
tar: image/ppd/C: Cannot change ownership to uid 0, gid 0: No such file or directory
tar: Error exit delayed from previous errors

---

