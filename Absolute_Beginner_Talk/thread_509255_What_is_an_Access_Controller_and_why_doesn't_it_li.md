---
title: "What is an Access Controller and why doesn't it like me?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by gerryl on 2007-07-25
Yesterday I posted a question about not being able to connect to the Internet – many thanks for the many prompt replies and suggestions.  Unfortunately, none of them worked.  Here is the situation:
Processor – Dell XPN
OS – Ubuntu v7.04
Modem – Westell 6100 modem/router
ISP – Verizon DSL
I cannot establish the PPP link.  I manually run pppoeconfig and get the dreaded “Sorry – I scanned 1 interface but the Access Controller on your provider did not respond…”  :(
I have seen many threads with this problem, and I regret having to add yet another one, but I have not seen a clear explanation of what an Access Controller is and how to solve the problem.  I am able to connect to the modem using Firefox and the 192.168.1.1 address.  It tells me:
Your modem is not ready for Internet access.	
Internet status – not connected	
DSL link – connected 
PPP status – down
I am also able to successfully ping the Verizon ISP at 192.168.1.47.
My setup is as simple as it can get – one computer, one OS (I do not have Windows in a separate partition), no wireless routers.  It would seem to me that since so many posters have the same experience, there should be some common problem that could be easily fixed with some magic setup parameters.  HELP!!!

---

### Post by p_quarles on 2007-07-25
Okay, first, when you refer to another thread, you should link to it:
[http://ubuntuforums.org/showthread.php?t=508466](http://ubuntuforums.org/showthread.php?t=508466)
That way, we can see what solutions you tried that didn't work. 

Anyway, I think I might be able to help. Your ISP doesn't need to "support Linux" in order to support the service you're paying for,  because networking protocols are not OS-specific. 

First, find out if your DSL modem has a web interface. It should and, ironically, it's probably running on embedded Linux. Open your web browser, type the modem's LAN address (192.168.1.47), and you should see the configuration application. Call Verizon and ask them to walk you through setting it up this way. If they ask, tell them you're using Windows.

I had a similar experience with my ISP recently (AT&T -- I'm going to switch soon). I was trying to figure out how to configure the modem for a particular inbound service. I had to explain that, no, I was not using a Linksys router, but a Linux operating system. Eventually I was able to get the very simple information I wanted, but I had to repeatedly insist that my question had nothing to do with my OS. 

It's silly. I'm guessing they do it this way, though, because the vast majority of customer service agents are just given scripts for Windows and Mac users -- things like "press the Start button, and click on networks." Aggrevating, though.

---

### Post by gerryl on 2007-07-25
Thanks for the prompt reply.  Sorry about not including a reference to the prevous thread.

I am posting from my office computer - my problem is with my home computer, so I cannot try your suggestions until this evening.  But I believe I already tried to connect to my ISP at 192.168.1.47 and could not connect.  I am able to connect to my modem at 192.168.1.1 and I do get a configuration page there.

I share your frustration in dealing with "Customer Support."  I have spent many hours on the phone and spoke to half of India trying to convince them (unsuccessfully) that, as you point out, networking is not OS specific.  I guess I'll have to bite the bullet and try again :(

I have seen other threads that address this issue by modifying browser properties - specifically dealing with IPv6 parameters:
[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)
Are you familiar with this and do you have any idea why this might work?

---

### Post by p_quarles on 2007-07-25
I would definitely try using the modem's web interface for configuration. In fact, while you still have net access at work, I would look for any online documentation for the model of your modem. You can probably find step by step instructions for configuring it. You may still need a number or two from Verizon, but it'll be much less frustrating if you know exactly what you need before calling.

In my experience, there is really no need to configure anything on the computer itself to get an ethernet+dsl connection working (EDIT: except for the NIC drivers, but that isn't a problem in Linux). Once the modem is set up, you'll be set.

One other thing: 192.168.1.47 is an internal network address -- if it's not the modem, then it's most likely the address it gave to your computer. The external IP address will be something different.

---

### Post by str8line on 2007-09-07
Sorry I missed this post earlier in the week.  When you accessed the 192.168.1.1 that is your modem interface.  The fact that you can access it is a good thing as that means that you have a connection from your computer to the modem.  

The ISP connection down means that the modem is missing the PPPoE connection in it.  Depending on the firm ware of the modem the steps are different.

Some questions:

1) which modem is it?

2) the main screen what is the basic lay out (a blue and white back ground, a red and black background or a blue back ground with icons in the top bar for navigation?

---

