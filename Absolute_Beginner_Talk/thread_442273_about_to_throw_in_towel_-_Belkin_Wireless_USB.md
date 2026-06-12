---
title: "about to throw in towel - Belkin Wireless USB"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-05-13
Last Monday I posted about how pleased I was that 7.04 loaded up from the CD and everything was working, including my Belkin N1 USB Wireless adapter.

On Friday, however, I went to sign on only to discover that the adapter was no longer working, not recognized by Ubuntu any longer.

I've tried every suggestion I can find on this board, and have re-installed Ubuntu (both 7.04 and 6.10 (that's truly a lost cause with this adapter) from scratch numerous times with no success.

When I install the driver, I get a success message about the driver installation, but a "No" to the "Hardware present" question in the dialog.

Iwconfig shows no association.

I can configure the adapter, and in 7.04, it sees the available wireless networks - but, I cannot get Ubuntu to actually connect the adapter to the network.

Can anyone help?

Thanks.

Caruso

---

### Post by carusoswi on 2007-05-13
. . . but, I am a stubborn old cuss, and I didn't throw in the towel.  I don't know if it will help, but, I got my wireless going again by fiddling with commands at this page:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/)

For some reason, my wireless does not want to maintain its association with the router, and, then it just drops out of sight on my system altogether so that it doesn't show up when you go through 'Network' to try to reconfigure it.  

I found that if I run the command shown on the referenced page to re-associate the adapter:  

iwconfig wlan0 essid ESSID

Where ESSID is the name of the router with which you are trying to associate, that would bring my adapter back to life, although the command, itself, did not re-associate my adapter - I had to go in through 'Network' to (happily) find my adapter once again in the list of possible connections, then, enable it, and then, it worked.

I have not tried to reboot, but will do that shortly to see if the association is maintained.

There is defintely some sort of bug here - don't know if it is 7.04 or my Belkin N1, but they are not getting along, and it has been very, very frustrating.  I have spent most of the day (since 3:00AM) trying to get this going, or at least figure out how to restore it so that I will have connectivity when I leave for the weak (where my wired connection will not be available.

In the course of troubleshooting this, I did follow suggestions to temporarily turn off WEP at the router - not ceretain it helped - not totally certain what I did (or didn't do).  Just kept trying things.

Hope the reference shortens the search to a solution out of this problem for some else.

Caruso

---

### Post by carusoswi on 2007-05-13
Just rebooted.  Seems to be working.  Yea!!
Caruso

---

