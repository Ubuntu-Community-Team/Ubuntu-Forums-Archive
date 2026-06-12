---
title: "Help required connecting Netgear modem router to BT Broadband"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2008-01-11
The computer I put together for my daughter using Ubuntu 7.10 worked fine and connected  to the internet with a new netgear modem router connected to my BT account at my home. BUT when my daughter took this computer to her own home 100 miles away and tried connecting to her new BT phone line and broadband account, it would not connect to the internet. 

She changed her username and password in the netgear control panel to reflect her BT broadband account details and spoke to the BT tech help line four times, who were of no help other than to say that linux would not support her netgear modem router.  They did however confirm that her broadband account was up and running and left it at that.  

Still she is unable to connection to the internet and finds that only the mains light, wireless and one ethernet port light comes on with her modem router. My advice has not helped her so far and now I need to ask others.  Any ideas please.

P.S. One thing I forgot to mention. At my home I first installed the netgear modem router using windows XP using the netgear software which came with it. Now  she only has Ubuntu on this computer at her home,  I'm begining to wonder if she will need to install XP to be able to set up her Netgear modem router again?

---

### Post by mikeyphi on 2008-01-11
You should be able to access the Router using any browser and entering the address
192.168.0.1
then entering the username and password 
once into the router's pages you should be able to set up the user ID  * NB* this is not the normal username but the BT supplied ID (something like - [email]yourname@hg35.btinternet.com[/email]) It is this ID that the router needs in order to 'connect'

---

### Post by a.v.l on 2008-01-11
> **mikeyphi said:**
> You should be able to access the Router using any browser and entering the address
192.168.0.1
then entering the username and password 
once into the router's pages you should be able to set up the user ID  * NB* this is not the normal username but the BT supplied ID (something like - [email]yourname@hg35.btinternet.com[/email]) It is this ID that the router needs in order to 'connect'

Thanks very much. Yes she has entered the router control panel pages from within Firefox and entered her BT username and password suggested by BT but still can't connect. It is interesting that you have given a ID with hg35.btinternet.com being part of it. Is this required when entering  her details? ie should she use:

[email]daughterusername@hg35.btinternet.com[/email]  - for her username

I ask because BT help line told her to use:

[email]daughterusername@btbroadband.com[/email]

and "Broadband1" for her password

these don't work and It is real confusing at the moment.

---

### Post by mikeyphi on 2008-01-11
Of course the system may have changed - but when I first got broadband I was given 3 items of data: Username and password (these are used for email and other things) plus a Network ID - that's the one that had the 'hg' bit in it!! Once it is used to set up the connection it is never used again.

---

### Post by laidback on 2008-01-11
If my memory serves when I played with a Netgear wireless router/modem I found an option that allowed me to check the line from within the router, i.e. once you've logged into the modem (as above). Cannot remember exactly what it said on the screen but it was something fairly obvious like Check Connection. The reason I mention this is to encourage you to split the problem down into 2 pieces, firstly be assured that the router/modem connects to your ISP then worry about the Ubuntu end. Trying to do it all at once will lead to intense frustration, at least it would if I were doing it.
Unfortunately I don't have the modem at home just now, my daughter's taken it to Uni otherwise I'd power it up and have a look for you. It can be helpful to delete all your settings and start again, there should be a reset to factory settings option too.

---

### Post by fiddledd on 2008-01-11
The username is the hg3 one at least mine always has been (i've been on BT Broadband for years). As I understand it, it doesn't matter what OS you are using, the router just assigns you an IP address via DHCP and passes it to the OS. The only time the OS is relevant is if you connect a modem via USB. Don't trust anything BT tech tells you, in my experience they are useless. You are in fact talking to someone in another country in a call center. They are getting all the information from a step by step wizard from a screen in front of them, and most know less about computers than the birds I feed in my garden :)

---

### Post by Paul820 on 2008-01-11
I don't know why BT told you linux will not work with a Netgear router, i have a Netgear DG834G wireless router and it works fine with my bt broadband account running gutsy. To access my account i filled in all the normal details and entered [email]myname@btbroadband.com[/email] but i was never given a password so it's left blank.

---

### Post by jonnywombat on 2008-01-11
Hi there..

Well you better see if bt are telling you the truth then, and that the line is enabled and there is no fault..
This can be done by changing your ASDL account username within your router to 
**bt_test@startup_domain**

It will ignore any password given.. save and restart your modem. once your modem restarts fire up your browser and navigate to [http://www.bt.net/digitaldemo/](http://www.bt.net/digitaldemo/) 

If that works then your line is set up ok and then it will probably be wrong username or password.. If that don't work then most likely cause is a line fault.. You know your router is ok coz you can see it in your browser. 

For a fuller how to on diagnosing asdl faults (uk specific) then check out [http://www.more-solutions.co.uk/support/bt-test-user.html](http://www.more-solutions.co.uk/support/bt-test-user.html)

Hope that helps

Jonny

PS.. I use bt and have a home hub and the full she-bang.. All works with linux just fine apart from the digital vault auto update thingy.. BT tech support sucks with linux.. I rang them not so long ago to ask them to remotely reflash my home hub firmware.. The guy wanted to run some diagnostic first.. Conversation went
BT "cant you click on the start button pls"
ME "no sorry i cannot"
BT "why not?"
ME "because linux does not have a start button"
BT "oh god, I'll get my supervisor"

---

### Post by a.v.l on 2008-01-11
> **mikeyphi said:**
> Of course the system may have changed - but when I first got broadband I was given 3 items of data: Username and password (these are used for email and other things) plus a Network ID - that's the one that had the 'hg' bit in it!! Once it is used to set up the connection it is never used again.

I've kept the details of my old BT broadband accountI have some years ago and since your first comments I decided to dig them out. They do give a username with the (hg) as part of it. My dausghter will need to look for this information to try and get connected. Thanks you for drawing my attention to it.

---

### Post by a.v.l on 2008-01-11
> **laidback said:**
> If my memory serves when I played with a Netgear wireless router/modem I found an option that allowed me to check the line from within the router, i.e. once you've logged into the modem (as above). Cannot remember exactly what it said on the screen but it was something fairly obvious like Check Connection. The reason I mention this is to encourage you to split the problem down into 2 pieces, firstly be assured that the router/modem connects to your ISP then worry about the Ubuntu end. Trying to do it all at once will lead to intense frustration, at least it would if I were doing it.
Unfortunately I don't have the modem at home just now, my daughter's taken it to Uni otherwise I'd power it up and have a look for you. It can be helpful to delete all your settings and start again, there should be a reset to factory settings option too.

Thanks again, We tried the option you mentioned but it said disconnected. We also used the reset button at the back of the modem router and tried setting a new account but no luck.

---

### Post by SteveHillier on 2008-01-11
If it might help.

I recently installed a btbroadband router and the user name was [email]user.name@btbroadband.com[/email] with the password supplied which acts both as service access username and email address.

First things first.

Your daughter I assume has signed up to a bt broadband service?
That service has been activated? [the DSL light on the router is solid green]
The router is switched on and the relevant lights are on?
The laptop wireless connection is enabled?
Can you connect to the ISP using a cable?
If you cannot connect wirelessly have you set up appropriate security at both ends?
If you check the ip address is the assigned address in the same network as the router [run ifconfig and check?  It will probably be 192.168.0.x.
Can you ping the router?

Connecting with Ubuntu of with Windows makes no difference.  I have a mixed network and there is no problem.

Just work through from the beginning and you should be OK.

Failing that BT help line will be at a loss because they only know about Windows.  I could come up and do it for you but that would be at my normal commercial rates for this type of work - £50 per hour.

Hope you find a fix soon.

---

### Post by a.v.l on 2008-01-11
> **fiddledd said:**
> The username is the hg3 one at least mine always has been (i've been on BT Broadband for years). As I understand it, it doesn't matter what OS you are using, the router just assigns you an IP address via DHCP and passes it to the OS. The only time the OS is relevant is if you connect a modem via USB. Don't trust anything BT tech tells you, in my experience they are useless. You are in fact talking to someone in another country in a call center. They are getting all the information from a step by step wizard from a screen in front of them, and most know less about computers than the birds I feed in my garden :)

My daugheters experience with BT helpline was as you suggested. It seems that  to knock up the time she spent on the telephone they had her disconnecting cables from the tower and modem and generally prolonging the experience without providing anything which worked.

---

### Post by a.v.l on 2008-01-11
That looks like another chanel I can investigate and thank you for this very useful information, I'll contact my daughter this evening and hopefully report back with good news.



> **jonnywombat said:**
> Hi there..

Well you better see if bt are telling you the truth then, and that the line is enabled and there is no fault..
This can be done by changing your ASDL account username within your router to 
**bt_test@startup_domain**

It will ignore any password given.. save and restart your modem. once your modem restarts fire up your browser and navigate to [http://www.bt.net/digitaldemo/](http://www.bt.net/digitaldemo/) 

If that works then your line is set up ok and then it will probably be wrong username or password.. If that don't work then most likely cause is a line fault.. You know your router is ok coz you can see it in your browser. 

For a fuller how to on diagnosing asdl faults (uk specific) then check out [http://www.more-solutions.co.uk/support/bt-test-user.html](http://www.more-solutions.co.uk/support/bt-test-user.html)

Hope that helps

Jonny

PS.. I use bt and have a home hub and the full she-bang.. All works with linux just fine apart from the digital vault auto update thingy.. BT tech support sucks with linux.. I rang them not so long ago to ask them to remotely reflash my home hub firmware.. The guy wanted to run some diagnostic first.. Conversation went
BT "cant you click on the start button pls"
ME "no sorry i cannot"
BT "why not?"
ME "because linux does not have a start button"
BT "oh god, I'll get my supervisor"

---

### Post by a.v.l on 2008-01-11
The latest news regarding my daughters inability to connect to BT broadband, is there seems to be a fault on the BT telephone line, even though it was a new install only three days ago. She has been advised to connect and leave connected her modem router in the test point of the master phone socket for 48 hours whilst the engineers try and locate the problem. So hopefully everything will be resolved once this has fault has been corrected. It been a pleasure having your help and advice, thank you all very much indeed.

---

### Post by laidback on 2008-01-12
And this after they had previously said it was working. Perhaps the result to the test we discussed above is indicative of a line fault.
Good luck for the future.

---

