---
title: "Evolution wont send mail, but receives okay"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by SPQQKY on 2007-07-23
Hey all, I did a search on here before posting this and there were a few threads but no one ever got a solution. So I have to ask again, what can I do to get my e-mail to send. I know I have everything set up fine, it's just not sending. 
Any tips would be appreciated. Thanks.

---

### Post by SPQQKY on 2007-07-23
I saw a suggestion to install Thunderbird, but I am having the same problem with it. I do not have a firewall installed ATM.

---

### Post by SPQQKY on 2007-07-23
What, no body e-mails anyone around here?:-k

---

### Post by AndyCinDallas on 2007-07-23
Might sound obvious, but I would reconfirm with your ISP the details of their SMTP-server address, port-number and whether you need to send your username and password along. 

My ISP recently changed all of that, so I speak from experience.

---

### Post by SPQQKY on 2007-07-23
It's configured fine, this I know as I just recently set it up in Outlook 2007 in Vista. Incoming and outgoing server address is correct and the port is correct.

---

### Post by AndyCinDallas on 2007-07-23
The only other thing I can think of is the firewall, but you've already said it's not installed (how about the firewall on your router, if you have one?). 

Apart from the SMTP-server at the ISP being down, I'm out of ideas - sorry :)

---

### Post by SPQQKY on 2007-07-23
I have a router, but it's a simple dlink 604 and I have firewall disabled. This is the first thing I looked at to be sure after I got the time out from Evolution. 
I know with outlook in winblows, it took a few minutes before I could send or receive, so I waited....but I've been waiting all day. LOL. I even added my free e-mail to the accounts and that one won't work either. 
This is frustrating. I hate to have to log into my e-mail web sites each time I want to send or receive mail.

---

### Post by SPQQKY on 2007-07-23
This is rediculous. I really can't be bothered logging in to 3 mail accounts for home and work to get my e-mail. I may have to forget Ubuntu all together for this silly little issue.

---

### Post by SPQQKY on 2007-07-23
Well, almost 500 people browsing this forum and only one person attempts to help out. I guess it's goodbye to Ubuntu. It's a shame really.

---

### Post by anewguy on 2007-07-23
Well, here's the deal:

     I have ATT/Yahoo dsl service and my mail goes through sbcglobal.net, and I know I had to add some things to make mail work that weren't on by default in Evolution or Thunderbird.  I had to be sure the outbound server connection said it was SSL, among other things.

     I think before anyone can think of helping you, you will need to post copies of your account setup page from Windows/Outlook Express and from Ubuntu/Evolution.  You can put something like <private> in place of things you don't want us to know.

     Post these things back here, then I'll see if I can help. :)

---

### Post by SPQQKY on 2007-07-23
Yes, I've done that. One account needs SSL, the others use no filters. Believe me, this has to be something with Ubuntu as I have been at this all day (well, periodically all day anyway).

---

### Post by anewguy on 2007-07-23
If you haven't already seen all the posts for this problem under the "search" option (not the search this forum, but the search), you should.  If so, sorry.  Here is one solution posted to another user with the same problem:

Buster95  
A Carafe of Ubuntu
   Join Date: Mar 2007
Location: Sydney Australia
Beans: 116
Ubuntu 7.04 Feisty Fawn User 

 
Re: Evolution mail receives but doesn't send [resolved] 

--------------------------------------------------------------------------------

Just thought I'd round off this thread by reporting the final outcome.

After trying just about every bit of advice offered on the forum, no success. I ultimately gave up and started using Thunderbird.

Then, just for the hell of it, I tried adding "noapic nolapic" to the kernel at bootup. This solution seems to come up as a cure-all for communications-related total system freezes.

I then activated Evolution as a test and you could have knocked me down with a feather! It actually bounded into action and proceeded to transmit every test message jammed in Outbox ( I've been trying to send various test messages for weeks).

I have absolutely no idea what I've done here. Nor do I know whether this will demonstrate the old proverb "a single swallow doth not the summer make", by seeing the whole thing falling to pieces tomorrow. But there you have it.
Cheers


Here's another reply in another post:
    

vulpes76 
View Public Profile 
Send a private message to vulpes76 
Find all posts by vulpes76 
Add vulpes76 to Your Buddy List 

  #7       February 1st, 2007  
AmandaKerik  
5 Cups of Ubuntu
   Join Date: Jan 2007
Location: West coast of Canada
Beans: 67
Ubuntu 6.06 Dapper User
  

 
Re: thunderbird receives but it won't send 

--------------------------------------------------------------------------------

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)
This is a site with a very easy to use add-on for Thunderbird - it can do hotmail, yahoo, aol, etc. Read and follow the instructions. I find it easier to set up and use compared to ypops (which is a pain to get on linux anyways).
__________________



As a side note, if both Evolution and Thunderbird have this problem I would say it is not either of the programs.  There is something somewhere with the smtp server and/or port either not set, set incorrectly, or in the case of a firewall, the port is being blocked.  Please advise what all of these things have been checked.
 
I'm sure you've also checked, but if your pop or smtp servers need specific ports, they sometimes work okay in Outlook Express without actually setting them, but in Evolution or Thunderbird you have to manually set them.

Keep us posted, we'll keep looking!:)

---

### Post by SPQQKY on 2007-07-23
Yeah, the default ports were incorrect for the different IPS, but I did configure them manually to the correct ports. I just updated the firmware on my router and reconfigured it just to be sure. I still have the same problem atm. I've contacted d-link, we will see what they say (if their tech support is any good and they actually return my e-mail). Thanks for your help. 
I'm sure I'll get it sorted, it's just been very frustrating. I recently moved and had to get the oh so lame sbc (at&t) dsl. I had comcast cable prior to that and it is much easier to work with.

Edit: Just to clarify, I didn't have Ubuntu installed prior to having dsl (so you don't think I had this working in cable). My uncle may be able to help, he used to be network admin for ComEd and now works for the largest lawyer firm in Chicago, maybe he has a tip or two (though at my age, I hate to ask. I hate feeling like a n00b again.....LOL.) Thanks for your support.

---

### Post by anewguy on 2007-07-23
Hey, I have ATT DSL also - did you see their post for the new port addresses for email?  Something like 995 and 425 or some such thing.:)

I originally installed Ubuntu from 6.10 and upgraded to 7.04 and had not mail problems.  Then I did something stupid (I won't go into the dumb details) with the result being I had to reload EVERYTHING - my Windows partition, Ubuntu, et al.  So I just installed straight from the 7.04 LiveCD a few days ago and let it do the updates.  I haven't had problems yet with mail (knock on wood!)

At any rate, good luck and let us know what you find out and we can keep trying if we need to.

BTW - have you tried WAP on your wireless?  I have ATT/Yahoo's 2WIRE dsl modem/wireless router, and just can't get WAP to work with it with Windows or in Linux.

Don't worry about feeling like a newbie again - I have 25+ years of technical experience on everything from large mainframes to pre-CPM populate-the-board yourself "home computers"  (very pre-IBM PC).  I even had some exposure to Unix at work, but got so used to just "using" Windows at home since I went on disability that I don't have a clue about this stuff, and it makes me feel stupid as well.  I mean, I've worked with a LOT of network stuff, etc., and I still get lost in Linux!:)  Oh well, at least since it's not work I can just walk away from it and come back later!

---

### Post by SPQQKY on 2007-07-23
Yeah, I feel pretty stupid now. They did some work on upgrading their tiers and I went on hold with them for the last half an hour. The only person I talked to was someone who couldn't help but she "'thought' that some of the older modems weren't working or something.." and put me on hold to tech. (which I couldn't stand to be on hold any longer). I don't actually use their e-mail, I was trying to set up my existing accounts, this connection was established when I moved in (long story involving my divorce and having to move yet again, yada yada).......sheesh, no wonder I'm flustered.

I haven't booted to windows in days (except to let my son play a game or two) and when I just went into windows......guess what? Outlook doesn't work either. So this is a problem right now with AT&T and I feel real bad for blaming this on the OS.....duh.

Oh well, now I just feel like whiping out info from Evolution and Thunderbird and trying from fresh once they get this sorted. Time to get some sleep. Thanks again for trying to help. Cheers.

---

### Post by northicert on 2007-07-24
If you suspect the port, try 587.

---

