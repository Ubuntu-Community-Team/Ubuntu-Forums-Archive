---
title: "Slow browsers etc."
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by Paradoxx on 2006-04-05
Hi all. 

I'm very new to Linux. I've installed Kubuntu 5.10, and like it quite much :).
But there are a few things I need your help with.

1. 
My browsers are running extremely slow (Konqueror and Firefox). I don't understand why this is.
The problem is only when I’m surfing at home; I've installed Linux on my laptop and when I connect to my schools internet, are there no problems.
I've all ready tried typing KDE_NO_IPV6=true in /etc/environment, but with out any luck.

2. I have an extern wireless net card (Ovislink WL-8000PCM). How do I get a driver so it will work in Linux?

Hope you can help me... Thanks.

---

### Post by StefanoCole on 2006-04-05
Well, you could try the Dillo web browser, you can find it in the repo (Universe). It is a very small and fast browser.

Stefano

---

### Post by Paradoxx on 2006-04-05
well I could try another browser... but I don't think it's the browser that’s the problem.... and as I said, there was no speed issues on my school with either konqueror or firefox....

---

### Post by jamesr on 2006-04-05
Have you tried other locations. I am assuming that is wireless. Have you checked signal strengh?

---

### Post by meborc on 2006-04-05
for your card, i guess you have to use ndiswrapper... read more - 
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

and there is a card (almost like yours) with a success-story -
[http://www.ubuntuforums.org/showthread.php?t=81003](http://www.ubuntuforums.org/showthread.php?t=81003)

---

### Post by Paradoxx on 2006-04-06
[QUOTE=meborc]for your card, i guess you have to use ndiswrapper... read more - 
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

and there is a card (almost like yours) with a success-story -
[http://www.ubuntuforums.org/showthread.php?t=81003](http://www.ubuntuforums.org/showthread.php?t=81003)[/QUOTE]

Now I've tried to install ndiswrapper using adept, but when I try to run the program "Windows Wireless Drivers" it ask for my password, I type it, the program is loading... and then nothing?

I've also tried running the command: /usr/bin/ndisgtk  but with out any luck... what am I doing wrong?

---

### Post by bionnaki on 2006-04-06
what version of firefox do you have? the 1.0.7 version in the repos is quite slow I have found. update to the latest version with these instructions: [https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29)

---

### Post by Paradoxx on 2006-04-06
[QUOTE=bionnaki]what version of firefox do you have? the 1.0.7 version in the repos is quite slow I have found. update to the latest version with these instructions: [https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29)[/QUOTE]

I got version 1.5.0.1... But I don't think it has anything to do with browsers versions.
We're not just talking slow... it is REALY slooooow. It can take up to 30-40 to open a page... really annoying ](*,)

---

### Post by IYY on 2006-04-06
Open a terminal, and try pinging some sites. For example:

> ping -c5 [www.google.com](www.google.com)

You could also try pinging an IP address:

> ping -c5 72.14.207.99

---

### Post by Paradoxx on 2006-04-06
[QUOTE=IYY]Open a terminal, and try pinging some sites. For example:



You could also try pinging an IP address:[/QUOTE]

PING [www.l.google.com](www.l.google.com) (64.233.183.103) 56(84) bytes of data.
64 bytes from 64.233.183.103: icmp_seq=1 ttl=240 time=39.9 ms
64 bytes from 64.233.183.103: icmp_seq=2 ttl=241 time=41.0 ms
64 bytes from 64.233.183.103: icmp_seq=3 ttl=241 time=41.0 ms
64 bytes from 64.233.183.103: icmp_seq=4 ttl=240 time=39.5 ms
64 bytes from 64.233.183.103: icmp_seq=5 ttl=241 time=40.2 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 20210ms
rtt min/avg/max/mdev = 39.591/40.371/41.027/0.610 ms

jonas@mshome:~$ ping -c5 72.14.207.99
PING 72.14.207.99 (72.14.207.99) 56(84) bytes of data.
64 bytes from 72.14.207.99: icmp_seq=1 ttl=237 time=136 ms
64 bytes from 72.14.207.99: icmp_seq=2 ttl=237 time=139 ms
64 bytes from 72.14.207.99: icmp_seq=3 ttl=237 time=138 ms
64 bytes from 72.14.207.99: icmp_seq=4 ttl=237 time=131 ms
64 bytes from 72.14.207.99: icmp_seq=5 ttl=237 time=133 ms

--- 72.14.207.99 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 131.922/135.998/139.293/3.003 ms

Google looks very slow... but the ip adress is normal speed...

---

### Post by IYY on 2006-04-06
Then you have the same problem I have on my Dapper machine (though mine is less extreme). DNS lookups seem to be slow, but everything else is fast (that IP address is the address of google.com).

I hope you get an answer here, because I haven't been able to figure it out for quite a while!

Try checking if you really disabled ipv6 by typing

>  ifconfig | grep inet6

---

### Post by Paradoxx on 2006-04-07
[QUOTE=IYY]Then you have the same problem I have on my Dapper machine (though mine is less extreme). DNS lookups seem to be slow, but everything else is fast (that IP address is the address of google.com).

I hope you get an answer here, because I haven't been able to figure it out for quite a while!

Try checking if you really disabled ipv6 by typing[/QUOTE] 

jonas@mshome:~$ ifconfig | grep inet6
          inet6 addr: fe80::2c0:9fff:fe68:d6e1/64 Scope:Link
          inet6 addr: ::1/128 Scope:Host

hmmm ? what does this mean ?

---

### Post by IYY on 2006-04-12
Means that you haven't really disabled ipv6 on your entire system, maybe you just did it for firefox.

You could try this:

[http://www.ubuntuforums.org/archive/index.php/t-87798.html](http://www.ubuntuforums.org/archive/index.php/t-87798.html)

But it didn't work for me. ](*,)

(that is, I managed to disable ipv6, but the lookups are still slow)

---

### Post by Paradoxx on 2006-04-14
[QUOTE=IYY]Means that you haven't really disabled ipv6 on your entire system, maybe you just did it for firefox.

You could try this:

[http://www.ubuntuforums.org/archive/index.php/t-87798.html](http://www.ubuntuforums.org/archive/index.php/t-87798.html)

But it didn't work for me. ](*,)

(that is, I managed to disable ipv6, but the lookups are still slow)[/QUOTE]

Now I've tried this.... but when i try i copy the new lines in the file, it says that i don't have permission to change the file.... :(

---

### Post by IYY on 2006-04-14
You should be editing this file with sudo. Like, **sudo nano <filename>**

---

### Post by Paradoxx on 2006-04-14
[QUOTE=IYY]You should be editing this file with sudo. Like, **sudo nano <filename>**[/QUOTE]

Okay... it worked, but when i type the command for ip v.6, it still shows to lines with text...

---

