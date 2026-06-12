---
title: "[SOLVED] No Internet!.... newb need help!"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by agerfe on 2007-12-08
I've just installed Ubuntu but I'm unable to connect to the Internet.

I have a wired connection and my Ethernet card is Intel(R) 82566DC Gigabit Network Connection.

It's supposed to connect automatically but it doesn't work no matter what I do. :confused:

I have a dual boot system with Windows XP. OS's are on separate HDD's.

I've checked the config with Windows and so far every address is ok (IP, gateway, etc). When I type ipconfig at the command (or ifconfig in Ubuntu) the only differences between Windows and Ubuntu are:

1. Windows says "DHCP enabled:...........No", while Ubuntu uses DHCP

2. Ubuntu displays an address for Broadcast (192.168.1.255) and I can't find Broadcast anywhere in Windows (that is there is no 192.168.1.255 anywhere........ unless that's some kind of default which Windows does not display but does use)

When I ping 82.211.81.158 (following the Help instructions in Ubuntu) I get no answer from the DNS server. However, when I ping ubuntu.com I do get an answer.

The monitor shows a graphic for incomming and outgoing packages. Also, Network tools and ifconfig display the correct addresses (dunno about the broadcast, however).

It seems that THERE IS some kind of connection.......... but I'm unable to connect to the Internet.

I'm really all new to this. Have learned all these terms and concepts in the last 2 days! :lolflag:

Anyone has any idea as to what the problem might be?

I'd appreciate any help! :)

---

### Post by agerfe on 2007-12-08
Have just discovered I'm able to check for security updates and even install app's through the application installer (Applications) but I'm still unable to connect to any website.

I can also ping my DNS server succesfully!

---

### Post by Shazaam on 2007-12-08
What browser are you using in Ubuntu? Try this...
If it's Firefox go to Edit>Preferences>General>Connection Settings. Make sure you have "Direct Connection" ticked. Close and reopen Firefox and you should be fine.

---

### Post by mgmiller on 2007-12-08
It sounds like you have internet connectivity, just Firefox won't work.  Open Firefox and click on Edit > Preferences

Then go to the network tab and in the connections area, click the settings button.

I have mine set as direct connection to the internet.  
You could try each of the others in turn if need be and see if it works.

You may have to close and restart Firefox after each change to see if works.

Good luck.

---

### Post by agerfe on 2007-12-08
Thanks guys! I'm not at home right now but will try that as soon I as I can and will post he result. :)

---

### Post by laidback on 2007-12-08
I would connect via an ethernet cable in the first instance, get that working, then move to wireless. I have used both and they do work in 7.04.

---

### Post by bumanie on 2007-12-08
If you are using ubuntu 7.10, there is a high chance that ipv6 is the culprit. There have been many cases of people being unable to connect to the internet with gutsy due to this.
Interminal type
gksudo gedit /etc/modprobe.d/blacklist
at the end of the list that appears type
blacklist ipv6. 
Save the changes and reboot.

---

### Post by agerfe on 2007-12-08
How do I save the changes?
Is there a command?

---

### Post by agerfe on 2007-12-09
At last!
I did a little research and found a way to disable ipv6 on Firefox.
If anyone has the same issue and reads this thread this is what worked for me:

1.Open Firefox and type > about:config in the address bar.
2. Where it says Filter type > ipv6
3. Change > network.dns.disableIPV6 to true by double clicking where it says false
Quit Firefox and launch it again.
The problem should be fixed.

Thanks to everyone who answered my post for taking some time in trying to help me. :)

---

