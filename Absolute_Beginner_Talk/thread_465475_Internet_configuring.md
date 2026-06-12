---
title: "Internet configuring"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by LostArt on 2007-06-05
I just instaled Ubuntu studio, and I can't figure out how to set up the internet, I don't even no where to start, so I'd live it if someone could help me. During the install I skipped this stage because it wouldn't auto configure.

---

### Post by KIAaze on 2007-06-05
How do you plan to connect to the internet?
dial-up modem? ethernet modem?

Is it DHCP (automatic IP address attribution)?

If you also have Windows, how do you connect to the internet with it?

---

### Post by LostArt on 2007-06-05
an ethernet modem, but I'm not sure about DHCP or how it connects with windows, it just does.

---

### Post by KIAaze on 2007-06-05
Then it's probably DHCP, otherwise you would have had to configure some things in windows too (or installed some software from the ISP which did that for you).

DHCP over an ethernet modem. It should be easy. I've never encountered any problems with such a setup.

1)Try typing ```
sudo dhclient
``` at a command-line.
That should theoretically renew your IP.

If dhclient is not installed, install it. But as far as I know, it's there by default.
(and since you don't have internet under Ubuntu, just download the .deb under windows, reboot into ubuntu, get the .deb file from the windows partition and double-click on it to install it)

edit: Hum, dhclient doesn't seem to be in the ubuntu repositories. Well, as I said, it really should be there by default.

re-edit:
2)Another thing to check if sudo dhclient didn't work:
Can you connect to your ethernet modem by typing some special address like 192.168.2.1 or other (look in the modem manual if you have one) in a browser window?
Or ping the address by doing > ping 192.168.x.x.

I think this only works if it's a modem-router or something like that, but at least that way you'll be sure that Ubuntu can use the ethernet port to communicate.

3)Other probable problem: pinging IP addresses works, but not accessing websites by typing their URL => DNS not working
To diagnose this try pinging google by one of its IP addresses for example:
> nslookup google.com
Server:         140.181.96.11
Address:        140.181.96.11#53

Non-authoritative answer:
Name:   google.com
Address: 72.14.207.99
Name:   google.com
Address: 64.233.167.99
Name:   google.com
Address: 64.233.187.99

ex:
> ping 64.233.187.99

(The nslookup command also exists in Windows. And you can also enter the IP address in a browser to access the website.)

---

### Post by LostArt on 2007-06-05
I'll try what you said later today

---

### Post by LostArt on 2007-06-05
Only thing is my windows and Ubuntu are on seperate computers, and I only have one ethernet cord, so I keep having to change it out till I make the whole house wireless, will the stuff you told me still work??

---

### Post by KIAaze on 2007-06-05
If you have two separate PCs, you can still transfer data between them using a USBkey (to install missing programs from .deb files for example).
If you have a crossover cable, you could first try to setup a direct connection between both PCs by giving to different fix IP addresses.
I have never done this myself between a Windows and a GNU/Linux PC, but pinging should be OS independant I think.

The command lines should all work on ubuntu since this is completely independant of Windows.

The main commands (I know of) to diagnose network problems under Ubuntu are:
> ping
nslookup
ifconfig
iwconfig


Use "man <command>" to learn more about them.

And maybe you should also have a look at this [Internet Howto]("https://help.ubuntu.com/community/InternetHowto").

Don't forget there's also the GUI in Ubuntu to try to solve your network problems of course. ;)

---

### Post by LostArt on 2007-06-05
I was going to try connecting it to the internet, and using your advise/trial and error, I'll keep you posted

---

