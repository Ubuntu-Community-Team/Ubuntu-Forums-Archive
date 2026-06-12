---
title: "Wireless Linksys router - Ubuntu support it?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-07-31
My linksys router works out of the box, plug the external modem into it and other computers can sign in (or plug it with ethernet).  But how do you put WPA and keep it secure?  Can I do it on ubuntu, or do I have to use windows??

---

### Post by GuitarHero on 2006-07-31
Most routers are configured by typing the ip of it in a browser, if thats what you mean that works on any os,

---

### Post by WADemosthenes on 2006-07-31
Really?  How do you do you find out the ip address?  And if I'm new is there anything I can mess up really badly?

---

### Post by tehnad on 2006-07-31
Open a terminal and type: ifconfig to get the default address.  On most Linksys the default is 192.168.1.1 or 192.168.0.1 and yes Ubuntu works just fine with Linksys. I am running my laptop on one right now using wireless.  The only issue that I had was the fact that I had to set a WEP key for security due to issues with the WPA encryption.  I still haven't sorted this issue out yet.  Everything should work fine.  To set your encryption just goto the wireless tab and then click the security tab.  As for messing anyting up, the worst that will happen is that you will have to push the reset button on the back of the router to reset the defaults.

---

### Post by WADemosthenes on 2006-07-31
Using ifconfig... is the "inet addr" the ip?  or something else, becuase that address isn't working, not sure what else to try.  I just put it in the address bar of firefox right?

edit: 192.168.1.1 worked, I think.  I'm at an msn broadband (the modem manager tool?) page, is that right?

---

### Post by tehnad on 2006-07-31
Are you plugged into the modem and not the router?  You should have a page that comes up and says Linksys with blue borders and a gray background.  If you are getting the MSN broadband page I would assume that you are not running through your router. Let me know if this doesn't make snese and I will give you a quick play by play.  As for the inet address, this is your ip address not the default gateway.  Your inet address should be something like 192.168.1.100 if your are running a new Linksys Wireless G router.

---

### Post by teh_chris on 2006-07-31
the linksys config page should make you log in. the manual should tell you what the default credentials are.

you'll know you're a tthe linksys page cuz it will have the linksys logo in the upper left hand corner.

if you are unsure that you are connecting to the right thing, you should plug in to the router directly without using wireless.  you can copy keys and stuff that way.

---

### Post by WADemosthenes on 2006-07-31
I'm wirelessly connected to the router, and it is connected to the external modem.  
...
I don't know what the problem could be, how do I get the ip of the router through ifconfig?

---

### Post by tehnad on 2006-07-31
Look in your manual if you have one and it should tell you the default gateway.  If it is a new Linksys Wireless G router then it is [http://192.168.1.1/](http://192.168.1.1/)
I think that they stopped using 192.168.0.1 after they changed from the B routers.  It will give you a login page and you will have to enter credentials.  Click the link I gave and you should go right to it.

---

### Post by WADemosthenes on 2006-07-31
the link sends me to the modems page :D  Ill look for the manual.

---

### Post by WADemosthenes on 2006-07-31
says to use that exact address.  Oh crap.

---

### Post by WADemosthenes on 2006-08-01
I'm thinking I can either reset the router and see what happens, or I can call linksys.

---

### Post by WADemosthenes on 2006-08-01
Okay, I called linksys and they were extremely helpfull.  It's all working, and I go to 192.168.2.1 :P and it works.

So How do I change the login needed so no one else can get in, and what other things do I need to do to make it secure?

---

### Post by Tomosaur on 2006-08-01
I'm not currently using this PC in wireless mode, but I have done so in the past (with Ubuntu Breezy) and my linksys wireless router + USB receiver (the bit you plug into the computer) worked without a hitch.

---

### Post by WADemosthenes on 2006-08-03
I don't seem to be able to use WPA, do I need encryption anyway?  What do I need to do just to keep safe.  Idealy I'd like to leave something open for a passerby to get access for a short time, as long as they couldn't mess anything up.  But in a small town in Utah, I doubt that there'll be any need for that.

---

### Post by WADemosthenes on 2006-08-09
I'm going to turn off the ssid broadcast and change the ssid name to something really odd.  Won't this deterr most peopel?

---

### Post by happyisland on 2006-08-20
I have a related, but even more basic question: when trying to configure my Linksys Router (#WRK54G, if that helps) I cannot login to the admin page. I type in the address (192.168.1.1) and at the prompt enter the admin/admin combo and press enter. Nothing happens and the username/password thing pops up again. This works flawlessly when I connect my girlfriend's Windows laptop the router. Is there something I am not doing right? It's lame that I have to fire up her laptop every time I want to change the router's configuration.
Thanks in advance for the help and sorry if this is too OT.
HI

---

### Post by MrSweet on 2006-08-20
> **happyisland said:**
> I have a related, but even more basic question: when trying to configure my Linksys Router (#WRK54G, if that helps) I cannot login to the admin page. I type in the address (192.168.1.1) and at the prompt enter the admin/admin combo and press enter. Nothing happens and the username/password thing pops up again. This works flawlessly when I connect my girlfriend's Windows laptop the router. Is there something I am not doing right? It's lame that I have to fire up her laptop every time I want to change the router's configuration.
Thanks in advance for the help and sorry if this is too OT.
HI

I had a similar issue a while back.  I was not able to log into my linksys router using FireFox, however when I used Konqueror I was able to access the router and make any changes I needed too.  I am not sure why this was, as I have used FireFox before on a few different systems without any problems.  Perhpas you can try to use a different browser and see if it works for you.

Mr. Sweet

---

### Post by happyisland on 2006-08-20
Thanks for the quick reply Mr Sweet. I just tried both Mozilla and Epiphany (I am using Gnome) and had the same inability to login that I get when using Firefox. Weird. Any other ideas? 
Please help - every time I have to use my girlfriend's windows computer to fix something in that I can't do in Linux she gets more skeptical and less likely to let me install Ubuntu for her to use too...

---

### Post by happyisland on 2006-09-02
Sorry to bump the thread, but I still have the same inability to login to the router's admin page using ubuntu. Does anyone out there have ANY idea why this could be? I really am at a dead end on this one and have to borrow my girlfriend's laptop to access the router's admin.
Router: WRK54G
Ubuntu I'm using: AMD64
Browsers I've tried: 32 bit Firefox, 64 bit Mozilla, Epiphany.

THANKS!

---

### Post by sailor2001 on 2006-09-02
the login of the router maybe still set at USER: admin or user...password maybe still set at >leave blank<, or if you had set it up, the password you set......did you go to [http://192.168.(2?).1](http://192.168.(2?).1) ?

---

### Post by happyisland on 2006-09-02
yeah, the thing is that I am able to login to the router using a windows machine no problem (ie I've got the right login info). I'm just trying to do the *exact same thing* in linux, and it won't work. Super weird.
When I type 192.168.1.1 it lets me enter login info but then, no matter what, it pops it up again with the fields blank.

---

### Post by rajan on 2006-09-03
i'm not sure this is your problem, but with my new linksys router (WRT54GP2 -- note: not your exact router) it says to enter 192.168.15.1 ..... you might want to try that. it's possible the manufacturers have multiple IP addresses. by the way, i'm in no way, shape, or form an expert. have you tried searching the forums? i think this thread has a lot of useful information:

[http://www.ubuntuforums.org/showthread.php?t=212172](http://www.ubuntuforums.org/showthread.php?t=212172)

have you tried calling/emailing linksys? it seems they have some support that actually helps linux users. tell the gf to read up on microsoft's antitrust violations while she's getting impatient about linux.

---

### Post by happyisland on 2006-09-03
Thanks Rajan, I will try to get in touch with Linksys I guess. It's weird, because I can login in Windows and not in Ubuntu, despite doing the exact same thing. It's really not that big a deal, but I just don't understand how something that is browser-based would work in only one OS. Could it be a cookies setting or something? 
Doggone it,
HI
PS: the gf has plenty of [wireless] networking problems of her own with Windows and is definitely no XP patriot.

---

### Post by rajan on 2006-09-03
have you tried another browser on the windows laptop? it could be that IE has your correct password saved as a cookie or something. i'm just saying that because the reappearing username/password prompt is something i get after i enter the wrong password. hope linksys has a good answer. let us know how this works out. good luck. 



your gf seems more on the linux wagon than mine is. i'm jealous.

---

