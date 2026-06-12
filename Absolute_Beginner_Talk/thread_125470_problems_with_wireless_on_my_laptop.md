---
title: "problems with wireless on my laptop"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by shadowfist on 2006-02-04
I have been having a problem with just about every live version of linux I have tried and I also have the same  problem with my installed version of ubuntu. (breezy) the problem I am having is this.. whenever I boot up a verison of linux my wireless card works for about 4 minutes and then just stops sending and receiving packets. :( 

the interesting part is that my wireless works just fine in windows (dual boot). and for the first couple of minutes my wireless works with absolutely no problems.

but the more interesting part is that if I boot up linux/ubuntu and have the wireless quit on me and THEN warm boot windows up after that. the wireless wont work in windows either. it requires a complete cold boot to get the wireless to work again.:-?

---

### Post by bscbrit on 2006-02-04
Is there anything in the logs to indicate what is happening, perhaps /var/log/syslog has some useful hints?

It certainly sounds as though the settings are changing a several minutes and I'll assume that it is in the computer NIC rather than the modem/router or whatever.  What programs are you running? Try Applications -> System Tools -> System Monitor and see if it can identify a program that is running quietly somewhere.

---

### Post by shadowfist on 2006-02-04
[QUOTE=bscbrit]Is there anything in the logs to indicate what is happening, perhaps /var/log/syslog has some useful hints?

It certainly sounds as though the settings are changing a several minutes and I'll assume that it is in the computer NIC rather than the modem/router or whatever.  What programs are you running? Try Applications -> System Tools -> System Monitor and see if it can identify a program that is running quietly somewhere.[/QUOTE]

I havent looked at the system logs yet but it happens with a clean install of ubuntu, the live ubuntu, kanotix, knoppix (kde distro), and a couple of other live disks and it does the same thing with all of them so I wouldn't think its a program but I will check.

---

### Post by shadowfist on 2006-02-07
I looked at the logs and the running programs. nothing seemed abnormal :neutral: any ideas of things to look for?

---

### Post by HokeyFry on 2006-02-07
well, if it's affectiong windows as well, maybe its not ubuntu. it could be your wireless router. I have the same problem, except that it will just at random quit on me. My solution is to reboot twice and it works. I haven't been able to find a tool for linux meant to repair a wireless connection, so if anyone knows, it may help us all out.

---

### Post by shadowfist on 2006-02-09
[QUOTE=HokeyFry]well, if it's affectiong windows as well, maybe its not ubuntu. it could be your wireless router. I have the same problem, except that it will just at random quit on me. My solution is to reboot twice and it works. I haven't been able to find a tool for linux meant to repair a wireless connection, so if anyone knows, it may help us all out.[/QUOTE]

well that is a good idea but it happens within 5 minutes of booting ubuntu. and I can use windows for days straight without failing. 

it seems that the error affects the hardware so if i dont power down all the way it will carry over to windows.

---

### Post by bscbrit on 2006-02-09
Which sounds like a configuration setting in the router is being corrupted when using Ubuntu but not when using windows - but that doesn't make sense.  You shouldn't have to configure your router again after it has been set up.  All the routers that I know keep their settings when powered down (although I do not know many people that power down their routers!).  And nothing that you do to configure the wifi card should have any effect on the router.....

So, please confirm that I have understood:

The connection fails when using the wifi network under various flavours of linux but works reliably when using windows?

Once the problem has occured then the only way to recover is to cold boot the system?

And now some questions:

How do you allocate IP numbers to your network - static or DHCP?  If the latter, what settings do you use under both linux and windows please.

If you try to recover - what exactly do you do ('sudo /etc/init.d/networking restart', 'sudo ifup ethx' or what?).

Are you running NetworkManager ?

---

### Post by shadowfist on 2006-02-09
[QUOTE=bscbrit]Which sounds like a configuration setting in the router is being corrupted when using Ubuntu but not when using windows - but that doesn't make sense.[/quote]
and I have annother computer that the wirless works at the same time that my laptop is having problems

[QUOTE=bscbrit]
So, please confirm that I have understood:

The connection fails when using the wifi network under various flavours of linux but works reliably when using windows?[/quote]
correct
[QUOTE=bscbrit]
Once the problem has occured then the only way to recover is to cold boot the system?[/quote]
correct

[QUOTE=bscbrit]
And now some questions:

How do you allocate IP numbers to your network - static or DHCP?  If the latter, what settings do you use under both linux and windows please.[/quote]

I use dhcp and it seems that the ubuntu machine is pulling a correct address. I am not quite sure what you mean by "settings"

[QUOTE=bscbrit]
If you try to recover - what exactly do you do ('sudo /etc/init.d/networking restart', 'sudo ifup ethx' or what?).[/quote]
umm... I dont realy know what steps to try I have tried whatever it is that releases the address and then renews the address. but I dont remember which command that is. and it fails to renew the address by the way...

[QUOTE=bscbrit]
Are you running NetworkManager ?[/QUOTE]
unless it is installed on a fresh ubuntu install, no. what does it do?

---

### Post by bscbrit on 2006-02-09
OK. next time the problem occurs in Ubuntu, go to the terminal/command line and type:

sudo /etc/init.d/networking restart

and watch for any error messages or even simply a ok/fail message.  If you get the 'ok' does your network come back to life?

> 
 I am not quite sure what you mean by "settings"
 

DHCP issues IP addresses with a lease duration.  It should be measured in hours or days but I was wondering if yours was set at a particularly low value and the IP address was failing to be renewed.  It was just a guess on my part and it is something we can look at when we have tried the more obvious problems.

I'm still not sure what you do to try to reset the system - you don't sound too sure yourself! :-D

---

### Post by bscbrit on 2006-02-09
We can also assume from your answers that you are only cold-booting the computer and not the router?  That was my misunderstanding.  Therefore the problem is definitely in your computer.

---

### Post by shadowfist on 2006-02-10
[QUOTE=bscbrit]We can also assume from your answers that you are only cold-booting the computer and not the router? Therefore the problem is definitely in your computer.[/QUOTE]

yeah that is my deduction :-)

I am getting home tomarrow so I will try to do the restarting networking thing then.

and as far as lease duration and stuff its just the default ubuntu settings so I wolud think the're pretty standard.

thanks for your help!!!

---

### Post by shadowfist on 2006-02-12
[QUOTE=bscbrit]OK. next time the problem occurs in Ubuntu, go to the terminal/command line and type:

sudo /etc/init.d/networking restart

and watch for any error messages or even simply a ok/fail message.  If you get the 'ok' does your network come back to life?[/QUOTE]

ok tried the networking restart. it took a little while and then came back "OK" no error messages or anything. it did not bring the network connection back to life though.

I did discover something interesting though. the death of my connectivity is definately not time related but rather something to do with the ammount of data sent and received or the number of packets or something like that. I booted up ubuntu today and I was bussy doing other things so after I logged on it went into the screen saver for about a half hour. then i went and tried the internet and it worked fine for a few minutes. but when I started flipping through pages it died after maybee 30-45 seconds. I have no idea what this means though.

---

