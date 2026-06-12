---
title: "Student Project (Demo) Help!"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by kingjimbob on 2007-03-19
Hello all!

I am an undergraduate student doing a networking Unit. We have been set the task to demonstrate a SOHO network (Small LAN) with a Linux server and possible NT or XP workstations.

To the Point:

Firstly I wanted to use Ubuntu (or pref Kubuntu) server (or workstation) to host the following;

Local domain User accounts
File sharing
Internal email
Intranet

My biggest headache at the moment is working out what i need to set up an internal only mail system. Currently looking at the following; Postfix, sendmail and zimbra. Literally all i need to do is demonstrate that mail can be sent in between users. But the comments i have been reading on the above has confused me. 

My Background:

I am a true newbie to Linux, i have been meaning to get myself into Linux for a while now and this is my chance. But i need some guidance! 

So far I have successfully installed Kubuntu and played around with it. In addition i have installed Samba for the file sharing between Linux and XP machines.

However, i will be totally honest... i am out of my depth here and do need spend alot more time getting my head around linux. But i was hoping someone could give me some pointers.

Any feedback would be much appericated!

---

### Post by dmsynck on 2007-03-19
Honestly, I am a Linux newbie also, but from what I have read, I would shy away from Sendmail. From what I understand, the configuration required to get Sendmail working is quite hairy and intimidates even seasoned Linux veterans. Just my two cents, but I would look at one of the other MTA's (Mail Transport Agents).

---

### Post by LanDan on 2007-03-19
postfix is simple to configure and works great, and i use it even if sendmail is the default MTA

p.s.

it also is default in ubuntu

---

### Post by LanDan on 2007-03-19
mmm maybe not what you're looking for but it might give you a different approach to the whole setup and it would address your goals immediately

you could use LTSP. not sure if you know this but it would leave out the need for a file server, mail server (u can use the system mail on your box that already works) and user accounts speak for them selves.

edit:

it would also relieve you of the task of setting up any workstations other then just plugging in the network cables

---

### Post by stalkier on 2007-03-19
First off Kingjimbob do not stress about converting to Ubuntu from XP. It is a bit intimidating at first but I would roam around the forums and print off some info like commands etc. I am also a undergrad but I am more into the design/graphics/web development fields. I am running Ubuntu edgy eft on my laptop full time now with NO partition for XP. I really enjoy having the freedom of not being under Gate's boot. However, that is enough about me. Definatly stick with the Ubuntu forums. The people here are great and you will find your answers. I wish you the best of luck on your project.

---

### Post by tagra123 on 2007-03-19
Might be overkill, but this link looks useful:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

When you are done -- help the community and post a how to. Many will thank you, I'm sure.

---

### Post by kingjimbob on 2007-03-21
Sorry ive not replied sooner, but thanks for the feedback everybody! Ive got a feeling this forum will be handy, you guys are very helpful!

And course, soon as i have a full blown config sorted for this demostration, i will post a how to, need to keep a record of everything i do for the documentation so hopefully be of use to some people.

 I will do a bit of a research into the suggestions so far and get back to you. 

But if anybody has any further feedback, more the merrier

J

---

### Post by kingjimbob on 2007-03-25
Ok this is where project stands at the moment. (please remeber im a newbie to this)

Kubuntu is installed as a workstation (not a server! - wanted to see if could keep the GUI) and have installed Samba. can view and share files. But realised that Samba needs to be installed as a Domain Controller to create user accounts. 

Havn't been able to find a guide as yet for installing Samba as domain controller on Kubuntu. But have for Ubuntu! So this may be the route.

In terms of an Intranet (internal only) email system - no luck. Looking into post fix at the moment and will probably follow these suggestions...
[http://www.experts-exchange.com/Software/Server_Software/Email_Servers/SendMail/Q_22106403.html](http://www.experts-exchange.com/Software/Server_Software/Email_Servers/SendMail/Q_22106403.html)

Getting a bit dis-heatened at the moment. Feel i may have understimated the project.

Any feedback?

---

### Post by Muzik83 on 2007-03-25
Have you checked out SWAT, the Samba Web Administration Tool?

Warning: It will currently erase any comments you have in your smb.conf file, so dont use it if you want to save your comments.

To setup as a domain controller, it's not too difficult with SWAT.  

First install swat (sudo apt-get install swat), then go to [http://localhost:901](http://localhost:901) and log in with your root user and password

Click on the globals and you may need to hit the "Advanced" button to get the full list of fields

(now here's where I get a bit fuzzy, because it's been a while since I setup a PDC on samba)

Look through the options, and if it looks right you can click help and see a description of what the field is for: 
         Domain logons (G)

         If set to yes, the Samba server will provide the netlogon service for Windows 9X network logons for the workgroup it is in. This will also cause the Samba server to act as a domain controller for NT4 style domain services. For more details on setting up this feature see the Domain Control chapter of the Samba HOWTO Collection.

                Default: domain logons = no 

I don't think you want "domain logons", but rather something else but the name has temporarily slipped my mind.

Hope this helps a bit

-sean

---

### Post by Muzik83 on 2007-03-25
I just thought of another great tool for you to try out.

sudo apt-get install webmin

then go to 
[https://localhost:10000](https://localhost:10000)

This gives a configuration interface to configure _TONS_ of different servers.  Samba is one option, however I recommend using SWAT for samba (since it was designed by the samba team, it has much more 'samba-related' help contained within. 

Postfix is a configuration option within webmin, so you may find it easier than editing the postfix configuration files directly (however you would probably gain a better understanding of how everything works by doing the config files)

-sean

---

### Post by kingjimbob on 2007-03-25
Thanks Sean! i will get onto looking into your suggestions!

---

