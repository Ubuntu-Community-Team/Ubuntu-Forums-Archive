---
title: "No Ethernet--Macbook 8,2 Ubuntu 10.04.3 LTS"
date: 2011-08-02
forum: Apple Hardware Users
---

### Post by daryllee on 2011-08-02
I have 10.04.3 LTS up and running on my triple-booted Macbook 8,2.  I can get an internet connection using Bluetooth over my iPhone's Personal Hotspot.  I'm beginning to go through the features list at [https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid), in order of importance to me.  (There are no MacBookPro8-x/Lucid pages yet, so I'm using this as probably the closest match).

The most important thing to me now is to get a wired Ethernet connection going, which I thought would be "out of the box" working, but I must be missing something fundamental.  When I boot, I have no connection at all.  When I click the connections icon in the upper right, I see my Bluetooth option listed, but nothing else.  When I open System->Preferences->Network Connections, I can Add a wired connection, but it doesn't seem to do anything.  It gives the appearance of not knowing I even have ethernet.  Can that be possible?  What else am I overlooking?  I've installed Linux in various forms on 10-15 computers over a 15 year period, and never encountered anything like this.

---

### Post by blane2 on 2011-08-02
why did you go with 10 over 11?

The ethernet works out of the box with your model in Natty.

---

### Post by daryllee on 2011-08-08
... why did you go with 10 over 11? ...

Sorry for the delay; I missed the notification that there was a reply.

I'm using 10.04.3 LTS partly because of the "LTS" but mainly because I have a client who has standardized on 10.4.3, probably until the next LTS comes out.  I want to be sure that when I send them something, I can say "I have the specified version and it works for me."

Believe me, if it weren't for that, I'd upgrade every six months!

As for actually getting it running, I saw an older thread that suggested inspecting the output of "dmesg | grep eth".  I did that and that is empty.  "ifconfig" mentions bnep0 (which I take to be the Bluetooth path I'm using now over my iPhone's Personal Hotspot service) and lo.

That's all I can think of to do at this point.

---

### Post by daryllee on 2011-08-10
Well, if it ain't one thing it's another. :)

I got an okay to upgrade, so I started that.  But probably due to my Personal Hotspot connection, the network connection failed and left my update manager in a broken condition (but already reported).  So I burned an 11.04 CD and booted to it.  Now I get a line in the boot sequence saying "(initramfs) Unable to find a medium containing a live file system" and it hangs.  So I guess this is a good place to wrap up this thread and start a new one in the Installations forum.

Thanks for all the fish.  (Explanation available on demand).

---

