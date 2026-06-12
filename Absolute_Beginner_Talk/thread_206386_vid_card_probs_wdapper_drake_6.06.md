---
title: "vid card probs w/dapper drake 6.06"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by Jbirdie1 on 2006-06-30
i am desperately trying to move to ubuntu but with both live and 'real' distros the startup/install process halts at the video section and tells me that i have to reconfigure my vid card using something called X. my machine is 2 months old and has a little ati x300 128mb card. i know this is kinda generic but so is my knowledge of linux. the system processor is a dual core 2.8 ghz. i can load a live version on my other machine its got an ati card too and is a regular 3.2ghz processor. plz help i must get away from the rootkit wankers that are attacking me - 7 formats since saturday :(tkz for any help

---

### Post by ltmon on 2006-06-30
Run a traceroute on those rootkitters for me and I'll hit them with a ping flood from work.... I have about 80Mb/s at my disposal ;)

(OK just kidding)

Whilst I'm surprised that the X300 doesn't work out of the box you could try the following: First use "vesa" drivers to get started, and then install the official ati drivers ("fglrx") once it's up and running for better resolution and 3d performance.

To force use of the vesa drivers start up in "Safe Mode".  This should be an option on the boot loader.  To install the fglrx drivers follow: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).  This howto gives the commands to run in text only mode, so you might not even have to bother with safe mode first.  To enter a virtual console (text mode) press ctrl-alt-F1.

By the way "X" is the name of the graphics system in Linux.  It's an abbreviated version of "Xwindows".  It's configured through the file "etc/X11/xorg.conf", which is what the system is asking you to do.

Hope all this helps.

L.

---

### Post by Jbirdie1 on 2006-06-30
tks for the help...btw i am not jokin when i say if i could ddos these wankers off the net, i would

i had 15 of these keylogger cookies in a really strange and invisible directory.  i traced them using traceroute and most were traceable to an isp in alaska. i sent the admin a message and got a lame reply about how he would forward my request to his abuse dept but i shouldnt not expect a reply (Due to certain privacy concerns and legal restrictions, we often can not share with you the outcome of our investigation or the specific steps we take to address your concerns) - the company is named Fast Colocation & Swift Ventures. your reply puts me in mind of steve gibson and the ddos attack he got from some "script kiddies", all done with 64byte ping commands!
tka again

---

