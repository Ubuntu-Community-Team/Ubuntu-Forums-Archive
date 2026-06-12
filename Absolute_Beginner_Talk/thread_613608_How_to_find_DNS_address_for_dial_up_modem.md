---
title: "How to find DNS address for dial up modem"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by teabuntu on 2007-11-15

Hi,
I'm test driving a Gutsy Gibbon Live CD, and when I tried to set up my modem to connect to the internet, I had to put in the DNS address pertaining to my ISP.  How do I go about in finding this information?  Thank you.

---

### Post by mike555 on 2007-11-15
You can use these DNS numbers ...   208.67.222.222 and 208.67.220.220.

---

### Post by SpiritIsReality on 2007-11-15
> **mike555 said:**
> You can use these DNS numbers ...   208.67.222.222 and 208.67.220.220.thanks!!!

---

### Post by teabuntu on 2007-11-15
Hi,
Thanks for the reply, but what do those numbers mean?

---

### Post by mike555 on 2007-11-15
Those numbers are OpenDNS server numbers , in your post you said you needed the numbers for your ISP , I don't know what ISP you have , but these numbers will work .........

---

### Post by Bartender on 2007-11-16
Are you sure you have to manually enter DNS?  

What dialer were you trying to configure?

Reason I ask is because if you were trying to configure pppconfig, it's really easy to choose "Manual DNS" by mistake.  If you fail to set it to Automatic at the appropriate step, pppconfig goes right to the next step, which is asking for Manual DNS numbers.

---

### Post by teabuntu on 2007-11-16
Hi,
Thanks for your replies.  I went to set up the modem so that I can dial up and connect to the internet.  I put in my password and username, the phone number that I should dial,. but I could not get the set up wizard to move forward from that.  I looked at the Help manual and it said that I also needed to know the DNS number for my ISP.

---

### Post by Bartender on 2007-11-16
> **teabuntu said:**
> Hi,
Thanks for your replies.  I went to set up the modem so that I can dial up and connect to the internet.  I put in my password and username, the phone number that I should dial,. but I could not get the set up wizard to move forward from that.  I looked at the Help manual and it said that I also needed to know the DNS number for my ISP.

What set-up wizard?  

You're not trying to set up the modem in Networking, are you?  AFAIK that's still broken.  Has been for over a year now.  They haven't gotten around to fixing nor removing it.
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

---

### Post by teabuntu on 2007-11-16
Hi,
I don't remember the name of the set up qwizard but basically I followed the instructions as per outlined in the Help section in Gutsy Ubuntu.  I'm not sure if you and I are tlaking about teh same thing, but judging by the outcome of what happened when I try to set up the modem to connect to the internet, maybe we are tlaking about the same thing?  So I guess that means that there is no way for me to connect to the internet using my modem? (BTW, I only have dial up to access the internet)  Thanks.

---

### Post by Bartender on 2007-11-16
> **teabuntu said:**
> So I guess that means that there is no way for me to connect to the internet using my modem?

Well, we don't know that yet.  What can you tell us about the modem you're trying to use? 

Dial-up is a neglected problem in Ubuntu.  For years the simplest method was to go out and buy a hardware serial modem.  Where those were available anyways.  The drivers that are available to us now because of Dell's involvement offer a glimmer of hope.  

Speaking of which, I'd sure like to see some reports on which winmodems work well with those drivers!

Anyway, you need to find out what modem chipset you have and then run a search on it.  There are thousands of dial-up posts.

---

### Post by teabuntu on 2007-11-17
Hi,
Thanks for your posts.  I went into Live CD for Gutsy last night and tried to connect to the internet.  I think I went into Administration then Networks and put in the dial up info.  But that didn't allow me to click OK to proceed, so I looked into the ports and I chose the one that said modem (there were other options but the option that I chose had the word modem, all the other options had jsut an alphabet next to them).  Then I was able to close this window where I had put in the dial up info (ISP phone number, user account info).  But, I could not get it to connect to the internet.  I could not find a "Connect to" option or anything resembling that.  

As for the quesiton of my modem, it's a Dell computer, so I believe it's Conexant (not sure about spelling).  

Also, my wi-fi works fine, except that I can't seem to turn it off or disable it like I can in Windows.  The wi-fi indicator keeps on flashing in green, indicating that it's turned on.  I don't use wi-fi so I would like to turn it off, but I could not find a control which would allow me to do this.  Thanks.

---

### Post by Irihapeti on 2007-11-17
I'm not a Gutsy user, nor have I had a chance to see the system, but my experience with Feisty may be of some use.

I found the network manager thing under System-Administration would not work for my dialup. It would connect and then do absolutely nothing. Firefox thought there was no connection. I've noticed that other people have said the same thing.

I installed Gnome PPP. I use the option "Automatic DNS" under Networking. I've also got "Ignore terminal strings (stupid mode)" turned on, because I was getting disconnected when trying to log in. (You may not need to do that - it depends on how your ISP handles the logon process.)

Another option, which is already installed (at least on Feisty) is to open a terminal and type "sudo pppconfig" (without the quotes) and follow the instructions to set up your system. Then you type "pon provider" to connect and "poff" to disconnect.

HTH
Irihapeti

---

### Post by teabuntu on 2007-11-18
Hello,
Thank you for tkaing the time to reply.  I'll look into Gnome PPP.

---

