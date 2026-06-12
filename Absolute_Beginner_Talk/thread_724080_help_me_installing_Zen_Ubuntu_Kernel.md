---
title: "help me installing Zen Ubuntu Kernel"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by taekr on 2008-03-14
Hi... 

I went to the following link 
[http://ubuntuforums.org/showthread.php?t=623874](http://ubuntuforums.org/showthread.php?t=623874)

and tried to follow the instruction. But like all other documents, it's just too difficult for people like me. 

Please help me get through this. 

I downloaded two files

linux-image-2.6.24-zen4_i386_i386.deb
linux-2.6.24-zen4.tar.bz2

I opened the terminal and typed 

sudo dpkg -i *.deb

Now I have Zen ubuntu kernel on the boot menu..    

Then, I used Envy to install Nvidia card .. but doesn't work. It says something about headers..  failed to install nvidia driver. 

All the instructions say that download the latest driver from Nvidia.. Well it's easier said than done. I visited Nvidia site but I was so lost.. I clicked on 'Download drivers' but my GeforceGo 6800 (inspiron 9300) is not listed..  where do I find the latest driver? Instruction has to be more detailed.. 

Could you help me??

What I need to do..?

---

### Post by mikewhatever on 2008-03-14
First, apologises all around, it's not my business, but, if you can't post the exact error message or find the latest nvidia driver for your card, you shouldn't be messing with kernel installations in the first place.
To try and help you anyway, you need linux-headers, as mentioned in the instructions --> [http://www.mattparnell.com/zen/2.6.24-zen4/i386/linux-headers-2.6.24-zen4_i386_i386.deb](http://www.mattparnell.com/zen/2.6.24-zen4/i386/linux-headers-2.6.24-zen4_i386_i386.deb)

The latest nvidia driver for you card seems to be here [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html). Verify your card is in the list [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html)
Good Luck.

---

