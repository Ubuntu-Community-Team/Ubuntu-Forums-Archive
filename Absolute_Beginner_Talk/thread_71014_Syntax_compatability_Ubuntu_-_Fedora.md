---
title: "Syntax compatability Ubuntu - Fedora"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by happychap on 2005-10-02
The instructions at this location:
[http://users.tpg.com.au/johnd/dsl200.html](http://users.tpg.com.au/johnd/dsl200.html)
covers the requirements I need to get my usb modem up and running - I use both the same modem and the same ISP.

As I am a total noob to both Linux and Ubuntu, would some kind person be good enough to review the file and let me know if the syntax in the file - it was written for Fedora - is compatible with Ubuntu.

Much appreciated.

---

### Post by UbuWu on 2005-10-02
Wow, those instructions don't look easy, success! One difference would be that on Ubuntu you have to use sudo instead of being root. So if it says you need to do something as root, you type 'sudo command-you-want-to-run'.

---

### Post by GTvulse on 2005-10-02
Those instructions are outdated. In principle, you should download, compile and install eciadsl 0.11 set it up with the correct firmware file and be done with it. You **don't need** rp-pppoe, because pppd (the version included with Ubuntu since Warty) already had the pppoe driver incorporated as a dynamic module. 

Search for my posts in this forum and you'll find instructions that work (else i wouldn't be typing this from Breezy...) :-)

---

### Post by happychap on 2005-10-02
Thank you for these replies. I must admit the instructions in that file looked quite daunting. It's good to know that with Ubuntu it's a lot simpler.

Dradul,
I'll follow up with searching through for you posts.
Last night I did download the eciadsl 0.11 file posted as stable since 24/09/05, and tried installing that, without success. I somehow think I may have a problem in the bootup of Ubuntu, as there are 4 things that 'fail' during the bootup process. They scroll through so quickly, and I have a Dell (read darker screen image) monitor, that it is very difficult to read just exactly what those items are.

I will persist, though - I've had more than enough of Windows, and Ubuntu and alll you people are great.
Again many thanks.

---

