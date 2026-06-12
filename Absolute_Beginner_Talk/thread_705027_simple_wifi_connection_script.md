---
title: "simple wifi connection script"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Cha1n5aW on 2008-02-22
Hi, I have to run the following commands every time I turn on my notebook to connect to my wireless network.  For some reason the "nm-applet" doesn't seem to work for wireless networks.  Regardless, I can connect with the following commands.

```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "NETGEAR"
sudo iwconfig wlan0 key XXXXXXXXXXXXXXXXXXXXXXXXXX
sudo iwconfig wlan0 key open
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

I'm wondering if there is a way I can put all this into an bash script so rather than typing it out every time I boot, I can just run the script.  Just in case it matters, I'm running ubuntu 7.10 gutsy build.

Thanks
- Shawn

---

### Post by mbsullivan on 2008-02-22
Hi Shawn,

Yes, this is possible... although it may not be a good idea. As a general rule, you never want to execute any commands that require root permissions in a script, because if somebody modifies your script (i.e. adds some nastiness that reformats your computer, etc), you will most likely blindly execute the script anyway.

That being said, if we are very careful, it should be possible to create a script that can't be modified without root access and will be fine to execute. The easiest way to do this would be to:

(1) Make a script with the following line at the top:

```
#!/bin/sh
```

(2) Place all of your commands afterwards, in the body of the file. The way we are doing things, you shouldn't need the "sudo"s.

(3) Change the permissions of the file to allow it to be executed by the root user, but NOT read and written to:

```
chmod 100 [filename]
```

(4) Change the owner/group of the file to root, so that you need root access to modify permissions/ownership of the file:

```
sudo chown root [filename]; sudo chgrp root [filename]
```

Afterwards, the script should function normally, and you can call it by saying:

```
sudo ./[filename]
```

Hope this helps!
Mike

---

### Post by Cha1n5aW on 2008-02-23
Wow, thanks a million.  I didnt realize it was as simple as adding the #!/bin/sh to the beginning & setting the permissions.  Thanks for the advice about security as well.  I will be doin some learning today about chmod codes and chown syntax.
d(^_^)
- Shawn

---

### Post by lswest on 2008-02-23
also, you can try using a program like WICD or Kwifimanager to connect to networks (i use kwifimanager, because i can save configurations in it for multiple networks) but feel free to try either one, i never liked the nm-applet (never works for me :P)

---

### Post by Cha1n5aW on 2008-02-23
Thanks Lswest, I will give WICD a try.  I've used Kwifimanaged before with backtrack, but as a gnome user, I try to steer clear of kde apps as I prefer not having a bunch of kde libs loading at startup.  I have been toying with switching to kde, but I very much like the gnome interface, spent alot of time customizing it.

---

### Post by lswest on 2008-02-24
i actually run kwifimanager in gnome, just needed to install kdebase along with it so it works, then i hid pretty much all the kde apps XD i don't like KDE all that much, but kwifimanager is definately nice^^  also, no big difference in load time with the KDE libs that aren't really used :P

---

### Post by Cha1n5aW on 2008-02-24
mbsullivan , I tried setting it all up as a script as instructed, and it seems to try to connect, but for some reason it doesnt.  I still connect okay when I type out each command seperately, but when I try to run em all in a script, it doesnt work.  The script I am running looks like this...

```

#!/bin/sh
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "NETGEAR"
sudo iwconfig wlan0 key XXXXXXXXXXXXXXXXXXXXXXXXXX
sudo iwconfig wlan0 key open
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

Any ideas?

- Shawn

---

### Post by SpoonBender on 2008-02-24
So you are using a WEP secured network? Network Manager never worked for me under dapper so i used the Network application under System>Administration>Network and now it is perfect but i don't know how it is in the newer releases:-P

---

### Post by Cha1n5aW on 2008-02-24
I'm running gutsy 7.10 & yes a 128bit WEP, as I'm using an older pcmcia wifi card that doesnt like WPA.  When I go into network through admin menu I get same thing nm-applet leads me to, still doesnt work.  The manual method works great, just a pain to have to type every time.  This system being a notebook I connect to many different networks depending on where I am, so if I can get this script to work, I can make a bunch of different scripts depending on the network.  I got the commands from a thread on here...
[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")
that I found when I couldn't get the gnome network-manager to work.

- Shawn

---

### Post by SpoonBender on 2008-02-24
Oh well wpa is a real pain on linux.:lolflag: I don't know. In the post where you showed your script i read before that you shouldn't need the sudo's in there. Maybe the script just stops waiting for your password or something? I actually tried a script eariler today because my network wasn't working but i tried switching the key type to plain asci and it worked so keep trying. Also, don't know if it will help but are you using ndiswrapper?

---

### Post by mbsullivan on 2008-02-24
> mbsullivan , I tried setting it all up as a script as instructed, and it seems to try to connect, but for some reason it doesnt. I still connect okay when I type out each command seperately, but when I try to run em all in a script, it doesnt work. The script I am running looks like this...

Code:

#!/bin/sh
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "NETGEAR"
sudo iwconfig wlan0 key XXXXXXXXXXXXXXXXXXXXXXXXXX
sudo iwconfig wlan0 key open
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

Any ideas?


Hi Shawn,

What is the output you see? i.e. where does it fail? I assume that you just get no DHCP offers. I'm not sure what's going on (it works for me, if I substitute the commands, but I don't have encryption on my network). 

Although I'm not specifically sure what's going on, here are a couple of things you can try:

(1) Explicitly specify the MAC address of your target router and the channel you want to connect to. Although I don't have your specific information (found from lwlist wlan0 scan), the commands should like like the following:

```
sudo iwconfig wlan0 ap "00:04:E2:D0:D1:96"
sudo iwconfig wlan0 freq 2.437G
```

(2) Try adding "sleep 2" after "sudo iwconfig wlan0 up" and again after "sudo iwconfig wlan0 mode Managed":

```

#!/bin/sh
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sleep 2
sudo iwconfig wlan0 essid "NETGEAR"
sudo iwconfig wlan0 ap [whatever you find]
sudo iwconfig wlan0 freq [whatever you find]
sudo iwconfig wlan0 key XXXXXXXXXXXXXXXXXXXXXXXXXX
sudo iwconfig wlan0 key open
sudo iwconfig wlan0 mode Managed
sleep 2
sudo dhclient wlan0
```

Hope this helps! It may not... could you give the output you see from your script, so that we can further debug the problem?

Mike

---

### Post by SpoonBender on 2008-02-24
Aren't you supposed to do the iwconfig configuration before you do a ```
ifconfig wlan0 up
```?

---

### Post by Cha1n5aW on 2008-02-25
Yes Mike, you are correct, when the script gets to the last command, it just doesnt get any DHCP offers, I've added the sleep commands into the script to try that, will let you know if it works or not.  If it doesn't work I will post the output I get when I try to run it.  SpoonBender, the commands in the script work when I type them out in the order I have them.  I got the manual wifi config instructions from [http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")

Thanks
- Shawn

---

### Post by SpoonBender on 2008-02-25
I never use the actual dhclient, i just completely restart networking ```
sudo /etc/init.d/networking restart 
``` It will probably give errors about eth0 not being present but try that in the script and see if you can get connected
**EDIT Never mind, I just saw the output of dhclient and it's the exact same thing as restarting network
***2nd Edit I checked the bottom of the post that you linked and they show how to add what you want to /etc/rc.local but don't know if you've tried it

---

### Post by mbsullivan on 2008-02-26
> Aren't you supposed to do the iwconfig configuration before you do a
Code:

ifconfig wlan0 up

?

I've never heard that, and I've seen other people do it this way. Specifically [this]("http://ubuntuforums.org/showthread.php?t=571188") (unofficial) guide brings the interface up before setting the settings. I think that wlassistant does it this way, too. 

That's not saying that it's right... if you find some evidence to the contrary, please share!

Mike

---

### Post by SpoonBender on 2008-02-26
Well a couple of days ago i had to do it manually and I found a guide saying to bring it up after the configuration and to me it just seems logical to configure it before you start it.

---

### Post by Cha1n5aW on 2008-02-26
Script still isnt working, here is the output of what I get when I run the script....
```

shawn@compaq:~$ sudo ./NGwlan0
[sudo] password for shawn:
: Unknown host
ifconfig: `--help' gives usage information.
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Bind socket to interface: No such device
sleep: invalid time interval `2\r'
Try `sleep --help' for more information.
sleep: invalid time interval `2\r'
Try `sleep --help' for more information.
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:17:2b:5d:cb
Sending on   LPF/wlan0/00:12:17:2b:5d:cb
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
Trying recorded lease 192.168.0.4
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

As you can see, no connection.
And here is what I get when I type out the commands manually...
```

shawn@compaq:~$ sudo ifconfig wlan0 down
shawn@compaq:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 5669
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:17:2b:5d:cb
Sending on   LPF/wlan0/00:12:17:2b:5d:cb
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
shawn@compaq:~$ sudo ifconfig wlan0 up
shawn@compaq:~$ sudo iwconfig wlan0 essid "NETGEAR"
shawn@compaq:~$ sudo iwconfig wlan0 key XXXXXXXXXXXXXXXXXXXXXXXXXX
shawn@compaq:~$ sudo iwconfig wlan0 key open
shawn@compaq:~$ sudo iwconfig wlan0 mode Managed
shawn@compaq:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:17:2b:5d:cb
Sending on   LPF/wlan0/00:12:17:2b:5d:cb
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.4 -- renewal in 99147 seconds.

```

I've been pouring through it myself to no avail.   I wish there was a way to "echo" the commands in the script so I can better gauge where things are going wrong.

Here is the script again, I believe it's different from what I last posted...

```

#!/bin/sh
ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up
sleep 2
iwconfig wlan0 essid "NETGEAR"
iwconfig wlan0 key 024d952a222d065b0df09ddbcc
iwconfig wlan0 key open
iwconfig wlan0 mode Managed
sleep 2
dhclient wlan0

```

I'm thinking maybe the syntax for the sleep command may be incorrect, & if I get that right, it may work.

Thanks
- Shawn

---

### Post by SpoonBender on 2008-02-26
It might be that you only need the second sleep, because that doesn't seem to show any errors. Try taking that first one out.

---

### Post by mbsullivan on 2008-02-27
Hi all,

I would say that the problem definitely comes from the commands that give the following errors:

> : **Unknown host**
ifconfig: `--help' gives usage information.
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

**Bind socket to interface: No such device**

What commands are executing at that time? You could put echos between the lines to figure it out as a last resort if it's not clear.

> sleep: invalid time interval `2\r'
Try `sleep --help' for more information.
sleep: invalid time interval `2\r'
Try `sleep --help' for more information.

Weird... did you type the script up on a Windows machine, or something? MS Windows uses \r\n for endlines, while Linux uses just \n. That's why there are sometimes boxes @ the end of lines that were made in Notepad if you bring them into Linux. There shouldn't be \r after the 2 unless you made the script in Windows... and apparently it's causing problems? Very strange.

The script works on my machine (without encryption, though) as it is written... I'm not sure what's up, but my guess is the source of those errors is the source of your problem.

Mike

P.S. - You left your encryption key in the quoted script. It probably doesn't matter, but you may want to edit it out.

---

### Post by Cha1n5aW on 2008-02-27
I did everything on this machine, I used gedit to write it out.  It seems like for some reason, when the ifconfig & iwconfig commands are run from the script, wlan0 isn't recognized, but when I type it manually, it's just fine, I've checked the spelling & syntax in the script many times, this is all very puzzling.  I'm going to add the echo commands & change the "sleep" command syntax, maybe that will light things up for me.  I've noticed that when editing the script with gedit, the ifconfig command and the sleep commands are red, not sure, but from experience with c programming, usually red is bad, and I believe its the ifconfig portion of the script that isn't working.

Thanks
- Shawn

---

### Post by Cha1n5aW on 2008-02-27
sorry, not exactly sure how to add in the echo commands, I tried putting it on the line above the command, but that didn't work, and if I put it on the same line as command, command doesnt work.  Is there a way to echo the whole script rather one line at a time?

Thanks
- Shawn

---

### Post by nanotube on 2008-02-27
to see the commands that are being executed, set the "verbose" option.

so your new script would be as follows:
```
#!/bin/bash
set -o verbose
ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up
sleep 2
iwconfig wlan0 essid "NETGEAR"
iwconfig wlan0 key 024d952a222d065b0df09ddbcc
iwconfig wlan0 key open
iwconfig wlan0 mode Managed
sleep 2
dhclient wlan0
```

that will print each command as it is being executed, so that you can see where you are in the script. hope that helps you with troubleshooting. :)

---

### Post by mbsullivan on 2008-02-27
> I've noticed that when editing the script with gedit, the ifconfig command and the sleep commands are red, not sure, but from experience with c programming, usually red is bad, and I believe its the ifconfig portion of the script that isn't working.

In this case, red is fine.

Perhaps your /bin/sh link is messed up in some odd way. Try changing the first line to "#!/bin/bash" or "#!/usr/bin/env bash".

Also, keep us posted once you get verbose output from the script.

Mike

---

### Post by Cha1n5aW on 2008-02-28
> **mbsullivan said:**
> 
P.S. - You left your encryption key in the quoted script. It probably doesn't matter, but you may want to edit it out.

I was gonna edit it out, then got caught up playin' with the script & forgot, now its all over the place.  Not that it really matters, if anyone who reads this forum is ever actually in my neighborhood, then be my guest, welcome to the network, lol.  Also, it's WEP encryption, and everybody knows wep can be easily be cracked in less than 60 seconds with the right software.
[WEP crack tutorial]("http://forums.remote-exploit.org/showthread.php?t=9063")

IMO the best possible wireless encryption you can get on wireless G is a WPA psk made up of random mixed numbers & letters as the only way to crack WPA is using a dictionary file & if your key is random numbers & letters then all the dictionaries in the world ain't gonna brute force it.

Thanks for noticing & reminding me, too late now for me to fix tho, duhh.. lol
Anyways, back on the subect of the script, I'll try the #!/bin/bash rather than #!/bin/sh.  I'll post the output from the new script sometime today.  Glad to hear it works for everybody else, *sob.. lol

- Shawn

---

### Post by SpoonBender on 2008-03-01
You'll never guess who is having this problem now. Me:confused:! I am now running arch linux and kdemod so if you want to go ahead and try it out but it's pretty hard to configure. The worst thing is that there is about 50 different wireless config files but none work. I'll try the script and see if it works on my laptop!

---

### Post by SpoonBender on 2008-03-01
Yes! It worked!:guitar: On my script i was pretty sure that arch didn't have dhclient so I used dhcpcd. If Ubuntu has it try it out! 

Here is the exact script I used:
```
#!/bin/sh
ifconfig wlan0 down
iwconfig wlan0 essid "CON-NET"
iwconfig wlan0 key xxxxxxxxxxxxxxxxxxxxxxxxxx
iwconfig wlan0 key open
iwconfig wlan0 mode Managed
ifconfig wlan0 up
dhcpcd wlan0

```

---

