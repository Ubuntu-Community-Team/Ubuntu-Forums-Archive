---
title: "Ubuntu installation"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by juice13610 on 2007-06-07
I am totally new to Linux, and obviously Ubuntu as well.  I downloaded Ubuntu 7.04 yesterday from what I believe was the official Ubuntu website (actually a mirror download site).  Regardless, I have had nothing but trouble ever since.  Yesterday, I tried installing Ubuntu, assuming it would copy over the Windows partition.  It was giving all kinds of errors and locking up, so I took the CD out and started the PC again (this was AFTER the Ubuntu installation).  It booted back in to Windows 2000.  I then used the recovery console from the Windows 2000 disk to format the C drive.  Windows 2000 booted again.  I then deleted the partition using the CD.  It booted in to Windows 2000, again.  Finally, I used the Windows CD again to delete the partition and then also create a new one.  However, none of my installations have worked regardless.

First of all, Im getting this error on boot (I have not added or modified anything in this error message, it appears exactly how I see it.

***********
There was an error starting the GNOME Settings Daemon

Some thing, such as themes, sounds, or background settings may not work correctly.

The last error message was:
Did not receive a reply.  Possible causes include: the remote application did not send a reply, the 

message bus security policy blocked the reply, the reply timeout expired, or the network connection was 

broken.

GNOME will still try to restart the Settings Daemon next time you log in.
*************

I say, thats fine, and press close...or at least try to, but the mouse is frozen...unresponsive.  5 minutes later the mouse comes alive, and I press close...I have the menu bar across the top, with the Firefox button and all... and 2 icons.  The first say "install" and the other (i dont remember).  

When I try to boot up without the CD in, it won't boot.  I get "Searching for Boot Record from CDROM..Not Found
Searching for Boot Record from Floppy..Not Found
Searching for Boot Record from IDE-0..OK
Invalid partition table."

Is there some way to format to the Linux file system or what?  It repeatedly locks up and is rendered useless.  I have not been able to start a single application or anything!

Any help would be appreciated!

---

### Post by w4ett on 2007-06-07
Can you list your system specs?....it will help diagnosis of the problem.

---

### Post by p_quarles on 2007-06-07
I'm guessing that you're currently using the Live CD for installation. Try downloading and burning the alternate install CD, and see if you don't have more luck with that.

---

### Post by juice13610 on 2007-06-07
I am at a business and picked up a PC that had not been used, and I don't believe I have the specs for it in my inventory work sheet.  My assumption would be 256 mb ram, 20 gig hd, 56x cdrom, pentium 4?

I had also thought that perhaps I was using a LiveCD, and I believe the website just confirmed it.  Where can I find a full download for a full to-the-hd installation?


Thanks again!

---

### Post by p_quarles on 2007-06-07
Go here for a list of mirrors:

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

Choose a location near you, then choose the version you want, and select the "Alternate CD" download (usually at the bottom of the list).

If the PC is running Windows, you'll be able to find the specs under the control panel. Alternately, you can download this: [http://fileforum.betanews.com/detail/Belarc_Advisor/1042897635/1](http://fileforum.betanews.com/detail/Belarc_Advisor/1042897635/1)

That program will create a system profile for you.

EDIT: Duh, short memory. You said you already deleted Windows. Sorry.

---

### Post by w4ett on 2007-06-07
You can also download the iso from here....remember to check the box  for the alternate cd option before downloading.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by juice13610 on 2007-06-07
Thanks a lot guys.

I have an "Alternate CD" download running now.  Hopefully I have better luck with this one.

As far as the system specs, I couldn't retrieve them because I had formatted Windows.  Im actually an IT professional I just have no Linux experience and its a completely different animal to me.  It's all French!
I would like to become Windows-independent one day, but thats far off for now.  I'm going to try to learn Ubuntu the best I can, since it's the version that Dell is sending out now.  I figure there will be a lot more Linux users in a couple of years!

I'm also on the "Down with Microsoft" bandwagon, too.

Tired of seeing them sue everybody.

---

### Post by p_quarles on 2007-06-07
Yeah, I edited my last post a second ago because I remembered that you'd formatted the drive. I'm getting old, I guess. 

By the way, the Live CD won't install properly on a system with lower than 256 MB of memory. So, if this PC has less than that, that would explain a lot.

---

### Post by w4ett on 2007-06-07
There is some useful information here:  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)   for use of the alternate install cd/method.

---

