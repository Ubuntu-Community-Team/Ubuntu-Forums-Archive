---
title: "Powerbook 12&quot; 867 -- ubuntu 12.04 install notes"
date: 2013-12-24
forum: Apple Hardware Users
---

### Post by theodore-r on 2013-12-24
I installed a from a 12.04 dvd that I burned when Precise was still new. I had installed on Lucid on this computer before, but had problems with the wireless, and abandoned it. I decided to try it again for some python and java programming since apple PPC stuff was falling way behind.

It installed fine, and even the video worked without a hitch (didn't expect that) and I was able to get the airport card working fine. 

I then performed system update, which was about 7-800M worth of stuff. After that finished it says 

"Not all updates can be installed: 
This can be caused by 
*A previous upgrade which didn't complete 
*Problems with some of the installed software
*Unofficial software packages no provided by ubuntu
*Normal changes of a pre-release version of Ubuntu "

Then if offers to do a "partial upgrade" or to "close"

I keep hitting close until I can get some feedback on why I get this message, and whether to go ahead with "partial upgrade" or keep ignoring it.

Also, as I stated earlier, I want to use it for Java and python programming, which I am currently learning. 

I installed openJDK 7 sdk, with synaptic package manager. I also installed (or tried to) Spyder through the ubuntu software center, but it just stopped installing after a little while, no error message.

So that got me wondering ... would Spyder simply not install if it was x86 only binaries. Also, could I be installing an x86 version of openJDK without knowing it.

Also, if they are x86, can any package manager compile/build them for me or do I need to do that myself. 

Thanks

---

### Post by theodore-r on 2013-12-25
ok ... solved my java question setting up java home. It is PPC.

I'm still searching for the Spyder solution. I think I have to build it using PIP, and fix some line so that it specifies PPC. 

As for the update question ... I just did all the updates, so it isn't a question anymore. I also installed the Lubuntu environment, and have been logging into that instead of the Unity.

A new question: I timed it and it takes 8 minutes to boot up. It takes a similarly long time to log out. Without a full console reading, the semi verbose boot up sequence says there is a soft lockup for 23 seconds. Anybody else run into this?

---

### Post by theodore-r on 2013-12-25
Sorry about all my ignorance. I seem to be answering my own questions as I go along.

Spyder installed just fine with synaptic package manager. Runs nicely also. So I'm guessing that the software center and package manager will only show me PPC stuff. 

Closing the lid doesn't make it sleep. It just shuts it down and I have to reboot. I'll see if I can find anything out about this. Also, the bootup delays might have something to do with the nvidia driver, if I've read correctly.

---

