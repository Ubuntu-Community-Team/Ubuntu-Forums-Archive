---
title: "Need Help with Internet"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Link360 on 2006-09-04
I have recently downloaded Ubuntu for my computer. I also have Windows XP on my computer. On windows I have internet explorer.Can I use that internet browser for Ubuntu? If so how?
If not what do I do? Thank You for Your help.

---

### Post by Miademora on 2006-09-04
You can use Firefox wich does the same as Internet Explorer.

---

### Post by Link360 on 2006-09-04
How do I make Firefox work? Right now it doesnt get anything from the internet.

---

### Post by SvanteH on 2006-09-04
Well are you sure it's _only_ FireFox ? If it's only that try going to *about:config* and search for ipv6 and make that value false.

If it's the whole internet then [www.opendns.com](www.opendns.com)

---

### Post by Link360 on 2006-09-04
do i have to do that while in Ubutu?

---

### Post by Miademora on 2006-09-04
You type it in the Firefox adressbar on the top in Ubuntu.

---

### Post by meng on 2006-09-04
Perhaps the first thing is to establish that you have a working internet connection at all. Can you open a terminal (Applications > Accessories > Terminal) and try
ping google.com
if you see packets sent and returned, then press ctrl+C - we've established that your internet connection works. If you don't see packets return, then you don't have a working internet connection and you need to work through getting that set up. Let us know either way.

---

### Post by Link360 on 2006-09-04
alright i no im really stupid, but whats the firefox address?

---

### Post by Link360 on 2006-09-04
im pretty sure my internet works fine. Im using it right now. Unless it could work for one operating system and not the other, but my connection if great.

---

### Post by Link360 on 2006-09-04
that if means is

---

### Post by meng on 2006-09-04
But if I read your posts right, you have an internet browser working in Windows but an internet browser not working in Linux. It certainly is possible that your connection is working in Windows but not (yet) in Linux. So unless you know something that you haven't shared with us, why not humor me?

---

### Post by Link360 on 2006-09-04
ok ill get into Ubuntu and test my connection.

---

### Post by Link360 on 2006-09-04
i typed what you said in terminal and it said
 
bash:ping google.com:command not found

---

### Post by meng on 2006-09-04
That's strange. I can understand if it said
bash: ping: command not found
but I can't understand why it apparently said
bash: ping google.com: command not found
so I do have to ask (sorry) are you sure you typed it correctly.
Obviously this process would be quicker if you had two computers ...

---

### Post by Link360 on 2006-09-04
one time that i typed it did say bash:ping:command not found.

---

### Post by meng on 2006-09-04
Okay, scratch my suggestion, then, I have a different approach. Go to System > Admin > Networking and see if your network connection is recognized and activated. By the way, what sort of connection is this? Modem? Ethernet card to modem? Wireless?
Also you can look at this thread for suggestions, because this user has a similar problem to yours (I think)
[http://ubuntuforums.org/showthread.php?t=250377](http://ubuntuforums.org/showthread.php?t=250377)

---

### Post by tommcd on 2006-09-04
How do you connect to internet? DSL? Cable?
Is your ethernet connection on under system>administration>network connections? Make sure eth0 is set to enabled and it is set to use DHCP.
If you connect via DSL using PPPoE, open a terminal and type:
'sudo pppoeconf' (without quotes) and follow the prompts (you can answer defaults to anything you are not sure about).

---

### Post by Link360 on 2006-09-04
wireless

do i need to be in Ubuntu to do that?

---

### Post by meng on 2006-09-04
Yes you need to be in Ubuntu.
Wireless huh? Open network? WPA? WEP encryption? You know the ESSID of the network I assume? You need to configure the interface appropriately.

---

### Post by tommcd on 2006-09-04
First, you should probably make sure you can connect with a wired connection in ubuntu. There are several docs on wireless in the wiki:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)
I don't know much about wireless though.

---

