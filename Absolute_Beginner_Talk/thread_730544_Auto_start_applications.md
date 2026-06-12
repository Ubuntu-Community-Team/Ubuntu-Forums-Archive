---
title: "Auto start applications"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by abhi_10_20 on 2008-03-21
You might have heard of "Auto Power on and shutdown" software in Win.... is there any kinda s/w in Ubuntu?

I wish to use it so that, the system automatically can power at a specified time, then start a particular application at another specified time, then end it specifically when i want it, then the system should turn off( or hibernate). Alll this to be done automatically. Is there any application for this?

---

### Post by igknighted on 2008-03-21
> **abhi_10_20 said:**
> You might have heard of "Auto Power on and shutdown" software in Win.... is there any kinda s/w in Ubuntu?

I wish to use it so that, the system automatically can power at a specified time, then start a particular application at another specified time, then end it specifically when i want it, then the system should turn off( or hibernate). Alll this to be done automatically. Is there any application for this?

In your BIOS (well... in some bioses) you can set a time to automatically turn on.  YMMV with that however.  I'm sure there are apps to shut it down on command, but I don't know them off the top of my head.  I know you can set it to automatically hibernate or suspend when it is idle for a certain amount of time.

---

### Post by abhi_10_20 on 2008-03-21
thanks...and for auto starting, & closing an application "while in ubuntu"...do we have any feature?

---

### Post by mridkash on 2008-03-21
You can set cron jobs to do that. I just know that you can set scheduled tasks using it. How to use it? I dont know.

You can use these commands to do some stuff.

```
 sudo shutdown hh:mm
```
Shuts down the pc safely at the time you set (hh:mm 24 hr)

you can also use sleep command to launch programs after certain time.
like,
```
sleep 10m && firefox
```
Will start firefox after 10 minutes.

All these commands have to be entered on terminal in Applications > Accessories > Terminal

---

### Post by shaunbarlow on 2008-03-21
If you use gnome then open up synaptic and search for gnome-schedule. Install it then start the program from Applications>System Tools>Scheduled Tasks. 

If the program you want to start automatically has a gui then you need to put "export DISPLAY=:0 && " in the command field before the path to the program or script you want to run. Otherwise, the window for the program won't appear on the screen.

I think there's a similar program if you're using KDE, surely a few google searches or someone round here should be able to help out.

As for shutting down at a specific time i think it's just a case of setting a scheduled task to run the command "halt". Although it may require root privileges, if so then you should search google or these forums on how to run cron as root. (cron is the name of the program that "scheduled tasks" controls)

As for starting automatically, it depends on a few things. The scenario that comes to mind requires a few things:
1. another computer (we'll say pc#2) being on in your network at the time you want the scheduled computer (pc#1) to wake.
2. your scheduled computer having "wake-on-lan" capabilities (google should help you, try searching for something like ubuntu wake on lan setup or howto)

If all this works for you then install wakeonlan (search for this in synaptic) on pc#2, test it out by turning pc#1 off and  typing wakeonlan 00:00:00:00:00 (replace the 00:00... with the mac address of pc#1) in to the terminal of pc#2. If this turns pc#1 back on then create a new scheduled task on pc#2 with the command that you just typed into the terminal.

Please let me know if I can be of anymore assistance. Out of interest, what kind of tasks are you getting the computer to run? What is the application of all of this scheduling?

---

### Post by abhi_10_20 on 2008-03-21
thanks...will try this...am workin on corn with root...and its not on lan, just a stand alone pc...

i needed this to handle my torrent client, i got to schedule it to start and run at specific times(late night)  when i get  good bandwidth speeds.. and shut it down in the morning.

---

### Post by abhi_10_20 on 2008-03-21
ok..i used cron to start the app automatically... but fr auto power on the system, i dont hav any feature in the BIOS.. i do hav 'wake on lan' but its of no use bcoz my sys is not connected to a LAN...plz help..

---

### Post by shaunbarlow on 2008-03-22
Abhi,
Glad you got the cron stuff happening. I also have my torrent program scheduled to run only in the wee hours.
As for the auto power on thing, I have a few ideas (albeit hair-brained and elaborate) but maybe someone else can help out with this.
The first thing that comes to mind would be to get a computer somewhere on the net to send the wake-on-lan packets to your computer at the time you want it to turn on.
I googled around a bit and came across these sites:
[http://www.rshut.com/products/wol/](http://www.rshut.com/products/wol/)
[http://systemideasforyou.blogspot.com/2007/12/how-to-remotely-turn-on-computer-from.html](http://systemideasforyou.blogspot.com/2007/12/how-to-remotely-turn-on-computer-from.html)
The first site has a schedule option that sounds like it fits your requirements. Though, you'd probably have to set the schedule maunally every week or something.

If you have a normal home internet connection then you probably have a dynamic ip address, which means the address to your computer from the net is changing often. So to get another computer to communicate with yours on a regular basis you have to use a dynamic dns service to give your computer a reliable host name. Check out [www.dyndns.org](www.dyndns.org) to get this stuff happening.
The thing is though that because your computer is turned off you need to have the dynamic dns service running on your router. My netgear wgr614v6 router has a section where you can enter your username, password and hostname for dynDNS.org, which means everything will work whilst your computer is off. 

Maybe you could also have a dig around and look for some way of automatically waking your computer from standby/sleep/suspend mode at a certain time. This one is just a theory, but if it's possible then you should put your pc into standby instead of turning it off and everything will be shibby. 
Best of luck with it. Let me know how you go. I'll subscribe to the thread this time too ;-)

Cheers,
Shaun

---

