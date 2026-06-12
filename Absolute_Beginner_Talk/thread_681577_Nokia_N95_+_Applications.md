---
title: "Nokia N95 + Applications"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2008-01-29
Running Ubuntu 7.10

This doesn't seem to have been properly covered, or at least I was not hundred percent convinced. I will soon be getting the nokia n95 (not the N95 8GB). I was wondering how I could:

a) update software on the phone (as on the website it requires I use the PC suite program)
b) Install new apps (again on the site it looks like I need the PC suite application)
c) install a VPN client on the nokia so I can connect to my uni wireless network (usually connecting to the network here requires a BROWSER password login).
d) what is the best way to use skype? as I notice skype mobile works on symbian phones.

Any thoughts?

Regards

---

### Post by infinitejones on 2008-01-29
> a) update software on the phone (as on the website it requires I use the PC suite program)

You can't! You're stuck with having to use Windows. Maybe running XP or Win2K in VMWare might work, but my PC's not powerful enough to do that very well so I haven't tried.

> b) Install new apps (again on the site it looks like I need the PC suite application)

See above!

> c) install a VPN client on the nokia so I can connect to my uni wireless network (usually connecting to the network here requires a BROWSER password login).

Google will be your friend here - I've never tried but it took me 60 secs with Google to find this: [www.n95users.com/forum/third-party-apps/1584-nokia-n95-vpn-software.html]("http://www.n95users.com/forum/third-party-apps/1584-nokia-n95-vpn-software.html")

> d) what is the best way to use skype? as I notice skype mobile works on symbian phones.

My Nokia N95 had Skype pre-installed (I'm in Australia) - I assume yours would too so fire it up and give it a go. Usually works pretty well for me.

---

### Post by Joeb454 on 2008-01-29
I've got an N95, and I can answer you questions accordingly (only a bit of info from what I've gathered using mine):

a) Run Windows In a virtual machine/dual boot, because PC Suite hates Linux :(
b) See above
c) I have no Idea, you could try downloading Opera for your mobile? It's surprisingly good :)
d) I think you need the Nokia standard firmware for that, not a network carrier's firmware

EDIT: :lolflag: Nice to see somebody agree's with me, but was beaten to it :p

---

### Post by LeAstrale on 2008-01-29
im the happy owner of a Nokia N95 myself.. unfortunately this phone does not appear linux happy at all.. i cant even access the MicroSD card without taking it out of the phone and in to a seperate card reader.
i haven't been able to find any programs that could conenct and use the phone successfully unfortunately.

/Astral-1

---

### Post by infinitejones on 2008-01-29
> **astral-1 said:**
> i cant even access the MicroSD card without taking it out of the phone and in to a seperate card reader.

I can access the MicroSD card with the USB cable that came with my phone - just set the phone to "mass storage" mode when it asks you after connecting. It mounts like any other USB storage device so you can just copy and paste in both directions.

---

### Post by Joeb454 on 2008-01-29
I don't use the USB cable, I always connect to mine Via bluetooth. This is where I miss the PC suite, because when I'm using Windows with the PC Suite Installed, I can send and receive text messages on my phone, but using the computer :D

---

### Post by abhiroopb on 2008-01-29
I'm fine with not being able to use the SD card, or even if it is a hassle...i have an iPod so I don't see myself really transfering music or video...maybe the occasional picture taken with the camera. 

I use virtualbox, I actually tried connecting my sony erricson w850i using virtualbox and although it would show up on the devices list the PC suite software would not recognise it. Anyone have any luck with that?

Any other tips/apps that would be useful?

Thanks a lot for the replies.

---

### Post by abhiroopb on 2008-01-29
Also what about syncing with evolution.

For contact syncing i use zyb.com (really easy to use!)

For calendars I use google calendar and have google sms me the events. But I have got evolution downloading the events. So if I can I would like to have it sync with the N95.

---

### Post by LeAstrale on 2008-01-29
i have an app called goocalendar that syncronises directly with the google calender to the phone.

---

### Post by Nighto on 2008-02-08
> **abhiroopb said:**
> Running Ubuntu 7.10

This doesn't seem to have been properly covered, or at least I was not hundred percent convinced. I will soon be getting the nokia n95 (not the N95 8GB). I was wondering how I could:

a) update software on the phone (as on the website it requires I use the PC suite program)
b) Install new apps (again on the site it looks like I need the PC suite application)
c) install a VPN client on the nokia so I can connect to my uni wireless network (usually connecting to the network here requires a BROWSER password login).
d) what is the best way to use skype? as I notice skype mobile works on symbian phones.

Any thoughts?

Regards

Hi.I have an N95-3 V 10.2.006 (you can check your version typing *#0000#). So, some answers to your questions:
a) the best solution is to use an windows pc, either by dualbooting yours or using someones else just to this purpose (i understand that by "update software" you mean updating the phone's firmware, which is not a frequent thing as there are not frequently releases of firmware). I'm currently trying to use VirtualBox (the closed-source, because the open source edition does not support usb), but without too much success.
b) to install new apps, or install newer versions of previously installed apps, i generally either 1. go to the app's website on the phone via wifi and download it from here or 2. download the app on my pc and transfer it via bluetooth. some apps require a process of signing the applications, to install that you need either sign them on a Windows PC (dual boot or emulated are OK, tried run the app with wine without success). There's an app called GenialSis that allows signing on the phone, but i didn't work with me.
c) AFAIK when there's a password login page, you are already navigating on that network, but are limited to that page. because of this, i suppose that, granted that you are logged before trying to use something else like upload media or check emails, nokia wifi use will run without problems.
d) Fring. It's a software that supports skype, msn, yahoo and google talk.

> **astral-1 said:**
> im the happy owner of a Nokia N95 myself.. unfortunately this phone does not appear linux happy at all.. i cant even access the MicroSD card without taking it out of the phone and in to a seperate card reader.
i haven't been able to find any programs that could conenct and use the phone successfully unfortunately.

/Astral-1

Here all i have to do is choosing data transfer when plugging the cable.

---

### Post by abhiroopb on 2008-02-09
Thanks for the help, got most things workuing. However i got a CD with a lot of .sis apps  on it. I understand the N95 requires .sisx, is there any way to run the .sis apps? if not where can i find .sisx apps?

mainly i want to use im+ to connect my various im clients

---

### Post by olavjunior on 2008-02-24
You can install sis files as long as they are for third edition (just try them)

The absolute best way to use voip is to use the built in support for voip. Register at one of the many voip-services (ex voipdiscount). Great sound quality and very cheep calls! That's the thing I love the most about n95

It would be real nice if someone could resolve the bugs connecting n95 through VirtualBox though :(

---

