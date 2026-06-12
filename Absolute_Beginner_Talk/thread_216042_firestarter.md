---
title: "firestarter"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by firebird45331 on 2006-07-14
how do I know it's running?  when I open the firestarter thing there's a blue circle with an arrow in my system message section. but if I close the firestarter thing it disappears. does it run continually now that I have it set up?  even if the arrow isn't there?

---

### Post by scxtt on 2006-07-14
it's *always* running - what you see is just the way to configure it ...

---

### Post by Anduu on 2006-07-14
When you shut down or reboot you will notice a "shutting down firestarter firewall" message as well.

---

### Post by firebird45331 on 2006-07-14
thank you

---

### Post by struess on 2006-07-14
there's also an option in firestarter under prefs-->interface to "minimize to tray on window close".  if you want to keep the program configuration handy (for checking events, changing policies, whatnot), make sure that's checked.  otherwise...poof.

---

### Post by Ann667 on 2006-07-24
> **scxtt said:**
> it's *always* running - what you see is just the way to configure it ...

OK, that’s what I was looking for.  The documentation on the Firestarter website talks about the persistence of the firewall, and that it runs as a system program.  But I want to make sure I have this 100% correct.  (I apologize in advance..... I’ve done many searches and found a lot of good info, but I just want to verify that I understand this correctly.)

The firewall itself is integral with the OS, and Firestarter is simply a graphical interface for configuration (it is not the firewall itself).  Once I have installed Firestarter and have run the wizard, the firewall is configured.  When I boot up, no matter what user I log in as, the firewall is running according the configuration set by Firestarter.  (I do not need to actually start Firestarter for the firewall to be running.  It is running even if I’m logged in as my regular user [no administrative rights], I just can’t see it and I can’t change any settings.  To change settings I have to open up Firestarter as the administrative user.)  Is this correct?

I’m certain I understand this correctly, it would just give me a little extra peace of mind to know for sure that I understand this correctly, and if I don’t, please correct me where I am wrong.   

Thanks.

---

### Post by T700 on 2006-07-24
You are correct.

Paul

---

### Post by Ann667 on 2006-07-24
Thanks T700.  (Love your avatar, by the way.)

It helps to know for certain that the firewall is up and running.  

I forgot to ask, there is a setting in the preferences "Start/restart firewall on program startup".  If this is selected and I have Firestarter configured for a cable modem, it is only *restarting* the firewall when I open Firestarter.  The firewall is still active when I boot up.  I don't have to start Firestarter for the firewall to be active with this option selected.  Correct?  (Again, I just want to make sure I have this set up right and I understand what it is doing.)

Thanks again.

---

### Post by Thiesen on 2006-07-24
Firestarter is a graphical frontend to iptables which is a way (it's some kind of scripted language I think) to communicate with Netfilter (this is the real firewall/router/trafficshaper) which is fundamentaly tied into the linux kernel. That makes it (Netfilter) to be always running whether or not you have Firestarter up and running.
 
Have a search on this forum for things like "graphical frontend iptables". That will reveal that there are other kinds of graphical ways to configure iptables but Firestarter is the easiest by far.
 
Now I am sure that someone will things like "make your own iptables script you n00b!!111!!!oneoneone". To tell you the truth; that isn't easy, that requires ALOT of learning. Therefore we have great programs like Firestarter that makes it easy for us.
 
While Firestarter is one of the more easy ways of configuring the firewall (for us newbies) it could be much improved on and I have good hope that in the future we might see another version of Firestarter.
 
I hope that you too can see the light better now... :-)

---

### Post by Ann667 on 2006-07-24
> **Thiesen said:**
> Now I am sure that someone will things like "make your own iptables script you n00b!!111!!!oneoneone". To tell you the truth; that isn't easy, that requires ALOT of learning. Therefore we have great programs like Firestarter that makes it easy for us.

I don’t think I’ll be doing anything like that any time soon… I simply do not possess the knowledge necessary to attempt such a thing right now.

Anyway, I think I answered my last question myself.  I reread the Firestarter documentation [(fs-security)]("http://www.fs-security.com/docs.php#docsdownload") specifically the preferences section.  (I linked it in case anyone else has a similar question and comes across this thread.)  It explained what those options do, and it does *re*load.  I think I’ve made this whole firewall issue a lot more complicated than necessary.  

Thanks

---

### Post by Handyman's Special on 2006-07-24
Thanks for the thread and the link. I have downloaded FS and want to learn how to apply it.

Cheers,
HS

---

### Post by Handyman's Special on 2006-07-24
Sorry, solved the problem.

Glad to have the program.

HS

---

### Post by petersjm on 2006-07-24
> **Handyman's Special said:**
> Just downloaded Firestarter - where can I find it to set preferences? I have looked in all the nooks and crannies. Is it accessed from the Termional?

Visited the website you listed and they show a 'Wizzard' but don't mention how to get to it.

Help,
HS

It should be under Applications > Internet > Firestarter

---

### Post by scxtt on 2006-07-24
it also shows up under System --> Administration --> Firestarter

---

### Post by T700 on 2006-07-24
You can also open a terminal window and type: ```
gksudo firestarter
``` and press Enter.

Paul

---

### Post by Christopher on 2006-07-26
I notice the Firestarter icon in my sys tray turns red and when i put my arrow over it it says "hit from and gives an ip addy's"  should i worry or is this normal internet traffic?:confused:  Thank you in advance.

---

### Post by scxtt on 2006-07-26
it might be 'people' trying to sniff out your box, but they're blocked connections - so it's nothing to worry about ...

---

### Post by Christopher on 2006-07-26
> **scxtt said:**
> it might be 'people' trying to sniff out your box, but they're blocked connections - so it's nothing to worry about ...

Ok thank you. :D

---

### Post by Handyman's Special on 2006-07-26
Even though the Blue Firestarter icon turns red, I am still 'protected?' No action is required on my part? It is unnerving to see it turn red. Paranoia runs rampant. Please set my mind at ease.

regards,
HS

---

### Post by scxtt on 2006-07-26
click on the red lightning icon, go to the "Events" tab, you'll see that it says "Blocked Connections" ...

---

### Post by Christopher on 2006-07-26
> **scxtt said:**
> click on the red lightning icon, go to the "Events" tab, you'll see that it says "Blocked Connections" ...



It doesnt say blocked anywhere. :confused:


**UPDATED**

I found where it says Blocked Connections. ;)

---

### Post by Handyman's Special on 2006-07-27
> **scxtt said:**
> click on the red lightning icon, go to the "Events" tab, you'll see that it says "Blocked Connections" ...

Thank you! If it was a snake, it would have bitten me! I was focusing on the tiny print and missed the BLOCKED.

Whew! I feel much better.

HS

---

### Post by redicqlus on 2006-07-29
no idea if anyone here can help me, but I've had some trouble with running firestarter as a startup program in sessions so that I can see the GUI.  My post is the last one here: [http://ubuntuforums.org/showthread.php?p=1313160#post1313160](http://ubuntuforums.org/showthread.php?p=1313160#post1313160)

I'd love a few tips !

-red

---

### Post by lechbialek on 2006-07-31
Firestarter fails [fail] at boot on my laptop, I think it's because I use WiFi (with WPA and Networkmanager) the network devices aren't connected/up during boot. 

If I check if its's running with *sudo /etc/init.d/firestarter *status it says firestarter is stoped!!!

Interesting fact is that *iptables --list ***doesn't show any rules!** after I start the firestarter GUI and check both again. *sudo /etc/init.d/firestarter * says its running, and only then does *iptables --list * shows a list of rules.

So I think that firestarter only modifies iptables if the service is actualy running.

Any suggestions on how to get firestarter to run on boot, I used BUM to check out the boot settings and firestarter is set to S20.

Lech

---

### Post by Apple 101 on 2006-07-31
This happens to me as well.  Sometimes Firestarter is running after bootup, and sometimes it is 'stopped'.

---

