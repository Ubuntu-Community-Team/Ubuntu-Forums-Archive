---
title: "Modem options"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by lee292 on 2007-03-13
I'm a rank beginner in the Linux world.  I've installed Edgy on my old Dell Inspiron 8500, and it seems to work like a charm with the exception of the modem.  A modem is the only way I can get Internet access from my home.  I opened the back and found the modem with the following ID:

PCTEL 3362 11583A
DP/N 0E828

This modem is tiny, only about two inches long and about half as wide.  I have a bad feeling that it's a winmodem, and I'm either going to have to get an external or a PCMCIA card modem.  Can someone walk me through getting a dial-up internet connection to work?  Thanks in advance!

---

### Post by eljalill on 2007-03-13
This is maybe what you are looking for?: 
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by dstew on 2007-03-13
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by lee292 on 2007-03-13
Thanks for replying so quickly!  I'll read these and see if I can get it working.  I'll probably  be baaaaack...:)

---

### Post by lee292 on 2007-03-14
I found a fairly cheap PCMCIA hardware modem, a Zonet at Tiger Direct, that has Linux support.  

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1175065&sku=Z165-1092](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1175065&sku=Z165-1092)

Rather than taking a chance of crashing my system by doing things like compiling and modifying kernels to get Ubuntu to recognize it, I'm leaning toward the above-listed modem.  The tutorials don't say anything about configuring a PCMCIA modem.  Anything I need to look out for?

---

### Post by dstew on 2007-03-14
I think it should work. PCMCIA is the type of slot it goes in. Once the BIOS detects a PCMCIA device, the kernel should be able to handle it.

---

### Post by lee292 on 2007-03-27
I don't know why it didn't, but it didn't.  It doesn't recognize the modem.  Just won a used US Robotics Sportster on eBay.  Once I get a serial cable, I should be in business (I hope)!  A rather large, clunky box is better than no modem at all.

---

### Post by lee292 on 2007-04-05
The old saying "When all else fails, read the instructions" applies here!  I re-read the above links  on how to get a modem working, and I found that I hadn't set it up!  :oops: Seems there's an application called Gnome-ppp that makes connecting a snap.  After installing it and doing a bit of tinkering with the settings, I got both the Sportster and the PCMCIA card modems to work.  I now have the PCMCIA card in my laptop and am saving to Sportster for when I put Edgy on my desktop machine! 

One more question... as I said in my first post, broadband isn't available at my home.  Can I copy gnome-ppp off my laptop onto either a disk or a memory stick to install on my desktop computer after I install Ubuntu Edgy?  What file or files should I get, and how do I go about installing it on my desktop machine?

---

