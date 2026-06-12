---
title: "does it matter what Operating system for internet?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by chaddiesel on 2007-08-13
I have recently installed ubuntu and I don't have internet yet. 
I called to get my internet connected today and the guy asked me what operating system it is on my computer for the modem. 

I am dual booting my computer and will be putting windows XP on the smaller portion of my hard drive. But I intentionally want to run ubuntu as my primary operating system and actually use the internet on ubuntu.

Does it matter what operating system I am using?:confused:

The internet connection is coming through a phone line, 6Mb/s connection, so I assume that it is DSL.

---

### Post by wolfen69 on 2007-08-13
it should not matter what OS you use. i use DSL with ubuntu.

---

### Post by Hobo Joe on 2007-08-13
It matters if they don't have modem drivers for anything but Windows.

But otherwise, no, it shouldn't matter.

---

### Post by Zalbor on 2007-08-13
You might have problems if they give you a USB modem/router. Always prefer ethernet.

---

### Post by chaddiesel on 2007-08-13
so if the modem I get is only windows then I'm gonna have to use windows in order to get the internet?

I have a DSL connection at work and it seems like the modem worked on its own, seperate from the computer....... 

I don't know enough about it.

---

### Post by Hobo Joe on 2007-08-13
Not necessarily, what is your modem model?

Search around for Ubuntu drivers.

---

### Post by WebSiteGuru on 2007-08-13
> **chaddiesel said:**
> I have recently installed ubuntu and I don't have internet yet. 
I called to get my internet connected today and the guy asked me what operating system it is on my computer for the modem. 

I am dual booting my computer and will be putting windows XP on the smaller portion of my hard drive. But I intentionally want to run ubuntu as my primary operating system and actually use the internet on ubuntu.

Does it matter what operating system I am using?:confused:

The internet connection is coming through a phone line, 6Mb/s connection, so I assume that it is DSL.

It doesnt matter, but what you should have told the person on the other side that you use Linux OS. Cause he/she can direct you to get the right software driver for it. Especially you will primary be using it. Or you could have told the person that you are dual booting and will be needing both software driver.

---

### Post by chaddiesel on 2007-08-13
thanks, i will call the guy back to see if he has both drivers for the modem.:)

I told him that I was using linux and will be dual booting the hard drive but he was more focused on which windows OS i was using. (MT, XP, or 2000)

---

### Post by Tiger-Smith on 2007-08-13
As the connection is above 2mbps it cannot be run through usb cable so it has to be a driver issue with your ether card

---

### Post by chaddiesel on 2007-08-13
My ethernet connection is on my motherboard..... 

does that boil down to just getting the correct driver?

---

### Post by WebSiteGuru on 2007-08-13
> **chaddiesel said:**
> thanks, i will call the guy back to see if he has both drivers for the modem.:)

I told him that I was using linux and will be dual booting the hard drive but he was more focused on which windows OS i was using. (MT, XP, or 2000)

LMAOL! :lolflag: figured. ;) And you are welcome. :D :guitar:

---

### Post by WebSiteGuru on 2007-08-13
> **chaddiesel said:**
> My ethernet connection is on my motherboard..... 

does that boil down to just getting the correct driver?

Go to your mother provider and see if they have a chipset driver for it.

---

### Post by Tiger-Smith on 2007-08-13
as its connecting through an ether cable it will be pointless to contact your service provider as most of them lean towards windows oss the best thing to do would try and find out the name of your ether card in windows as ur dual booting then try and find a linux vers for it

---

### Post by chaddiesel on 2007-08-13
sweetness!  I'll check it out.
:guitar:

---

### Post by ugm6hr on 2007-08-13
Are you getting the modem free with the connection? If not - spend a bit extra (or sometimes less!) and get an ADSL modem-router.  That way - it's almost 100% likely to work with Ubuntu.

Perhaps letting us know which country you are in / which supplier might help find someone who has used their service with Ubuntu before.

---

### Post by chaddiesel on 2007-08-13
I'm in the US.
Using a AT&T for the connection. And the modem is from them.

---

### Post by Tiger-Smith on 2007-08-13
can you access the internet on xp?

---

### Post by chaddiesel on 2007-08-13
I won't have the connection for a week...... I'm on my laptop on a wireless connection right now.

---

### Post by Tiger-Smith on 2007-08-13
its clear that its not a modem issue then, right as before best think to do is look @ the network device name in xp network connections then google the name then try and find the linux vers of the driver

---

### Post by WebSiteGuru on 2007-08-13
> **chaddiesel said:**
> I'm in the US.
Using a AT&T for the connection. And the modem is from them.

Hold your horssie! 

So you are using AT&T DSL Modem, and you connected directly to the computer, right?

I am now agreed with Tiger-Smith. You have ethernet driver issue. You'll need to go to your (again) motherboard provider and fine out if they have the driver for linux. Since Ubuntu does not have it. Or you can use the Windows driver with nisdriver (sorry cant remember the spelling on this).

---

### Post by armandh on 2007-08-13
dsl or cable that has a lan connection should work.
I have a dsl lan and a cable lan in the house [cable is higher speed the DSLis more reliable and came 'free' with the phone package. [no additional cost] ubuntu and windows work fine on both.
drivers are the software that connect the OS to the hardware in your computer. ubuntu has most but the very latest/oldest covered. others should be available

---

### Post by stchman on 2007-08-13
> **chaddiesel said:**
> I have recently installed ubuntu and I don't have internet yet. 
I called to get my internet connected today and the guy asked me what operating system it is on my computer for the modem. 

I am dual booting my computer and will be putting windows XP on the smaller portion of my hard drive. But I intentionally want to run ubuntu as my primary operating system and actually use the internet on ubuntu.

Does it matter what operating system I am using?:confused:

The internet connection is coming through a phone line, 6Mb/s connection, so I assume that it is DSL.

If you are using highspeed (DSL or cable) with a router it does not matter at all.  If you have dialup then you need to make sure your modem is supported under Linux.

---

### Post by schorsch on 2007-08-13
> **WebSiteGuru said:**
> ... Or you can use the Windows driver with [COLOR="Red"]nisdriver[/COLOR] (sorry cant remember the spelling on this).

.... ndiswrapper .... :)

---

### Post by chaddiesel on 2007-08-13
so technically i could run the windows driver and use some sort of "nisdriver" to adapt it to ubuntu?

---

### Post by abrianb on 2007-08-13
If I read this correctly, you don't actually have the internet package yet? I recently got AT&T DSL. They were very interested in what windows system I used so that they could send me a software package that installed the connection. But was primarily a bunch of AT&T Yahoo software to edge you over to using their browser etc.  When I got their package I installed the hardware, booted up Ubuntu which recognized the connection and I was on the net. 
 I don't think you will have much problem with this install.
 By the way, The day that they say you will get DSL is kind of hinky. It starts at midnight. But at the end of the posted day. So if it starts at Midnight of the 14th you won't be on till the 15th has actually started. 
Good Luck.

---

### Post by Gmbrdilos on 2007-08-13
AT&T does not support ubuntu (which is why I had to install windows just for that day to listen to their idiotic steps of activating my connection with their generic username and password (identical steps to windows xp)

after that got back to ubuntu with no additional software installed. happy ending :)

---

### Post by Ripfox on 2007-08-13
If you are going to have xp on a partition, just boot into it, set up your connection with them, boot out of it and Ubuntu should work out of the box with a wired connection (ethernet)

I have never had a wired high speed connection give me any trouble in Ubuntu. Sometimes you have to reboot once to get it to pick up, but thats bout it.

---

### Post by caro on 2007-08-13
> **chaddiesel said:**
> I'm in the US.
Using a AT&T for the connection. And the modem is from them.

As others have said, AT&T only supports Windows because they don't know how to troubleshoot or configure Linux.  I set my DSL up without their install package - I just configured it manually using my browser but it has been about 4 years so things may have changed.  

If you have access to a Windows machine, just use it to set up your DSL modem and then switch to your Ubuntu machine as long as the other issues are worked out.  (Or connect it to a wireless router if you have more than one machine.)

---

### Post by chaddiesel on 2007-08-13
yes, my laptop that I have is XP so it looks as if i'll be covered both ways....access to an XP machine and I am running a wireless router.

:) Rockin!:guitar:

---

### Post by caro on 2007-08-13
> **chaddiesel said:**
> yes, my laptop that I have is XP so it looks as if i'll be covered both ways....access to an XP machine and I am running a wireless router.

:) Rockin!:guitar:

You should be good.  I've had no trouble with my wireless since I first booted my Ubuntu laptop. Good luck!

(I've had to call AT&T once about a problem with my DSL, and I just tell them I'm using my Windows machine -- they'll be difficult if you tell them Linux.)

---

### Post by zek725 on 2007-08-13
> **chaddiesel said:**
> thanks, i will call the guy back to see if he has both drivers for the modem.:)

I told him that I was using linux and will be dual booting the hard drive but he was more focused on which windows OS i was using. (MT, XP, or 2000)

In other words, they don't know Linux. :lolflag:

---

### Post by WebSiteGuru on 2007-08-14
> **zek725 said:**
> In other words, they don't know Linux. :lolflag:

You got that right. :D :lolflag:

---

### Post by stchman on 2007-08-14
> **Gmbrdilos said:**
> AT&T does not support ubuntu (which is why I had to install windows just for that day to listen to their idiotic steps of activating my connection with their generic username and password (identical steps to windows xp)

after that got back to ubuntu with no additional software installed. happy ending :)

What would AT&T do if someone with a Mac called?

The easiest way to get your DSL up ad working is to go get a router.  Most DSL connections use a username and password.  Set the router up using PPoE and be done with it.

---

