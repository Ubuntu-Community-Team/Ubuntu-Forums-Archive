---
title: "Ubuntu problem - can't access repos, yet i can browse the web"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by ComplexNumber on 2006-09-04
i've just installed ubuntu for my dad. i can browse the web using firefox, but i can't access the software repositories. this leads me to believe that the firewall is blocking ftp whilst allowing http. i've gone through all the menus in ubuntu and i can't for the life of me find any way of allow ftp. if only canonical provided a gui firewall frontend like firestarter. i guess that means that i'll have to configure it using iptables on the command line. does anyone know of of a way to allow me to access the software repositories because i'd really like to get ubuntu up and running for my dad? thanks.

---

### Post by bluefrog on 2006-09-04
if you haven't installed it yourself there is no firewall in ubuntu out of the box.

In synaptic you may need to "enable" universe repository to access the software you may see in the "add/remove programs

Please be more specific as what you do to try to install programs.

James

---

### Post by ComplexNumber on 2006-09-04
the only software i've installed is that which came on the ubuntu cd. what i have installed is exactly the same as what everyone else has installed when they first install ubuntu. i haven't installed any software from the repos....and thats the problem.  i can browse the web using firefox(hence, there is an internet connection), but i can't access the software repos either using apt-get on the command line or using synaptic. it jsut times out because itcan't connect. it must be an ftp problem. it was only 30-45 minutes ago when i put my  password in fror the first time. although i've used ubuntu before. i know how to do what i need to do in fedora, but i can't find a way to do so in ubuntu.
i'm not quite sure if i've made it clear or anything, but i hope so :)

---

### Post by bluefrog on 2006-09-04
what repo does it try to reach. It may be down for whatever reason.

edit /etc/apt/sources.list and change the repo to archive.ubuntu.com or fr.archive.ubuntu.com or whatever country code in front of archive.
then 
sudo apt-get update

James

---

### Post by xpod on 2006-09-04
Correct me if im wrong BUT aint it the case that firestarter is indeed just a "frontend gui" for "iptables" which is in fact already on ubunto??

Im only going on what ive been reading myself so i could be wrong??

EDIT: > f you haven't installed it yourself there is no firewall in ubuntu out of the box.

Sorry i forgot that

---

### Post by ComplexNumber on 2006-09-04
> Correct me if im wrong BUT aint it the case that firestarter is indeed just a "frontend gui" for "iptables" which is in fact already on ubunto??
yes it is. its just a frontend for iptables, but i don't know the syntax for iptables at all, so i'd rather deal with the GUI in this case.




here is the first few linux of /etc/apt/sources.list. also, here is a screenshot of what happens in download manager when i try to reload the package information from the repos

> 
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

---

### Post by bluefrog on 2006-09-04
close add/remove program, open a console and try
sudo apt-get update
post results please

james

---

### Post by ComplexNumber on 2006-09-04
> **bluefrog said:**
> close add/remove program, open a console and try
sudo apt-get update
post results please

james
yup, done that already. immediately after entering my password, it shows the following, but it doesn't do anything else (ie it stays on 0%):
> 0% [Connecting to gb.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubun 
i'm pretty certain its something to do with iptables not allowing ftp but allowing http. i'll have a root around the /etc directory because i'm sure the solution lies there.




EDIT: now it shows this on the command line:
> Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://gb.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to gb.archive.ubuntu.com (1.0.0.0)]

---

### Post by bluefrog on 2006-09-04
1.0.0.0 is a weird IP for the least :).

check your network settings, are you using a proxy, router or whatever. dns nameserver is correct I assume as you can surf the web but definitely something is wrong in your network (settings?)

195.248.90.23 is the IP for gb.archive.ubuntu.com

---

### Post by xpod on 2006-09-04
> yes it is. its just a frontend for iptables, but i don't know the syntax for iptables at all, so i'd rather deal with the GUI in this case.


I KNOW you realised it mate i just did`nt think the other person  did with his assertion that Ubunto dosent come with a firewall when in fact it does

---

### Post by bluefrog on 2006-09-04
it does yes but not activated if not mistaken, so I guess you may forgive me my not so well phrased assertion.

---

### Post by ComplexNumber on 2006-09-04
yes, it is a bit strange ;). i had a look around the network tools in the menu, and its clearly showing that its connected up to the internet via the router because it gives the address 192.168.1.4

> 
I KNOW you realised it mate i just did`nt think the other person did with his assertion that Ubunto dosent come with a firewall when in fact it does i don't know of any linux distros that don't come with iptables :)


> 
check your network settings, are you using a proxy, router or whatever. dns nameserver is correct I assume as you can surf the web but definitely something is wrong in your network (settings?) everything seems to be ok there. i'm using a router. 
ahh well, if the worst comes to the worst and i don't manage to find a way to add the repos, i'll  slip in the fedora dvd that i've got instead.

---

### Post by Garyu on 2006-09-04
[http://www.ubuntuforums.org/showthread.php?t=249175](http://www.ubuntuforums.org/showthread.php?t=249175)

try this forum. he had the same problem as you. turned out to be a router setting I think.

---

### Post by ComplexNumber on 2006-09-04
> **Garyu said:**
> [http://www.ubuntuforums.org/showthread.php?t=249175](http://www.ubuntuforums.org/showthread.php?t=249175)

try this forum. he had the same problem as you. turned out to be a router setting I think.
ok, cheers. i'm looking through that link now. however, i don't think its a router problem because i have fedora connected up to the same router in the other room at this moment, and that has no problem. theres also a windows machine connected too with no problems.
i guess the solution will turn up eventually.

---

### Post by gils0040 on 2006-09-04
This sounds like a dns problem to me (i had the same exact problem). check and make sure that both of your dns servers are correct.

---

### Post by ComplexNumber on 2006-09-04
> **gils0040 said:**
> This sounds like a dns problem to me (i had the same exact problem). check and make sure that both of your dns servers are correct.
you may well be  correct :). i 'm going to start looking into that possibility  tomorrow.

thanks everyone for your help so far :). i really appreciate it.

---

### Post by bakert on 2006-09-04
I too had this problem and for me it was DNS-related.  Strangely, the act of pinging the repo addresses before running apt-get was enough to make it work (temporarily).  

```
$ ping gb.archive.ubuntun.com
```

Followed by

```
$ sudo apt-get instal blahblahpackage
```

My permanent fix was to make sure my DNS server addresses always appeared in /etc/resolv.conf (which gets overwritten all the time) by using these instructions:

[http://www.greertech.com/nixnotes/dhcpfix.html]("http://www.greertech.com/nixnotes/dhcpfix.html")

---

### Post by ComplexNumber on 2006-09-05
> ping gb.archive.ubuntun.com
trid this, and it pinged fine. then i tried this:
> sudo apt-get install firestarter
sudo apt-get instal frozen-bubble
sudo apt-get install xboard
same as before - all failed.




i checked resolve.conf. it showed "nameserver 192.168.1.1", which is the address of the router. all is well there. i also checked /etc/hosts (this showed 127.0.0.1. this is correct), plus a few others in /etc/apt. nothing appeared to give away any clues.
anyway, the uptake of this is that i gave up on ubuntu and installed fedora instead. he can now browse the web and access the repos. so he now has a good working introduction to linux :)

---

### Post by ComplexNumber on 2006-09-05
> ping gb.archive.ubuntun.com tried this, and it pinged fine. then i tried this:
> sudo apt-get install firestarter
sudo apt-get instal frozen-bubble
sudo apt-get install xboard same as before - all failed.




i checked resolve.conf. it showed "nameserver 192.168.1.1", which is the address of the router. all is well there. i also checked /etc/hosts (this showed 127.0.0.1. this is correct), plus a few others in /etc/apt. nothing appeared to give away any clues.
anyway, the uptake of this is that i gave up on ubuntu and installed fedora(i had a choice of this, suse 10.0 and simplymepis dvd's that i still have) instead. the first thing i did was check the repos....and i downloaded the various packages such as Smart and Smart-gui just to check. he can now browse the web and access the repos. so he now has a good working introduction to linux :)
i haven't yet given up on getting a fully working ubuntu installation, though, and i will try again....maybe efty will work out of the box and be supplied on dvd instead of 1 cd. third time lucky, i guess.

---

### Post by gils0040 on 2006-09-07
Try changing the your dns servers. Instead of using your router as the dns server, try using the dns servers that are provided to you by your isp.

---

### Post by yoghurt on 2006-09-10
This is the right way to approach this problem; however if you're using dhcp to get the IP address, please note that whatever you enter as your DNS will get overwritten by the dhcp with the next Ubuntu start.

I've seen a fix for that somewhere (basically a script that runs each startup and changes the DNS address from your modem's (typically 192.168.1.1) to ISP's one.

---

### Post by ComplexNumber on 2006-09-13
i tried that as well in /etc/resolv.conf, and it didn't work. i've just this minute installed simplymepis that was on the cover of the latest Linux Format. exactly the same problem as ubuntu. next: suse, then knoppix, then i might try to see if i can get ubuntu to play nice. i want dad to use ubuntu because its gnome and because of the size of the repos.

EDIT: suse failed.

---

### Post by linux major on 2006-09-14
Hi, I have been following the thread as i have had the same problems since i installed ubuntu. Finally got round it with the following fix.
Fixed the ip address for my networked linux pc in the router. then changed the network card setting from dchp to the same fixed ip address. now everything is working fine.
My router is a safecom.
Hope this helps others out there.
Regards
Major

---

### Post by ComplexNumber on 2006-09-14
> **linux major said:**
> Hi, I have been following the thread as i have had the same problems since i installed ubuntu. Finally got round it with the following fix.
Fixed the ip address for my networked linux pc in the router. then changed the network card setting from dchp to the same fixed ip address. now everything is working fine.
My router is a safecom.
Hope this helps others out there.
Regards
Major
i NOW think the problem is something to do with some router setting. hopefully mine and other people experiences can help other people experiencing the same problems, because there seems to be quite a few.

a strange thing happened to me today. i have been using fedora on my own pc for the past month or so, but strangely, for an hour today i had been experiencing EXACTLY the same problems as on my dads pc in the next room - ie i could connect to the internet whilst browsing with firefox, but i couldn't download any packages whatsoever using Smart. that seemed rather strange because i haven't actually changed my system in any way whatsoever since the last time i successfully downloaded packages via Smart. 

luckily, i had a eureka moment. i remember that the only thing that may have caused any effect is that, yesterday, i plugged the internet cable into my dads pc. i then had a brainwave. i went into my dads pc room and unplugged the internet cable from the pc where i had previous installed ubuntu, suse, mandriva, fedora, and simply mepis (i was only able to access the repos with fedora and mandriva). i went to my own pc and tried to download packages via Smart on my own pc, and lo and behold, it worked again. note that my pc and my dads pc are both connected to the same router. 

so why would unplugging the network cable of one pc after another pc on the same LAN? the answer has to lie within the router. but why was i able to access the repos on my dads pc using fedora and mandriva, but not with ubuntu or any of the others? :confused:. i'm wondering if it makes a difference if i install ubuntu on my dads pc whilst my pc is switched off rather than on. i noticed that the internal IP address of my pc was the same as that on my dads pc, but that should be impossible. i wonder if thats a clue.



**linux major**
thanks for the tip :). i may try that in the next few days on my dads pc.

---

### Post by linux major on 2006-09-17
Update, After my last post i once again lost the abilty to access the archives on timeouts. So i re configured the dns settings for my etho card to the static settings that my b/band isp uses, ie: 212.104.x.x
then removed the router dns of 192.168.1.3 saved and tried apt-get update. with 100% sucess.
:-) 
Major

---

### Post by linux major on 2006-09-17
ps, the router dns was 192.168.1.1. linux pc is 192.168.1.3

---

### Post by cptc on 2006-10-20
Hi
I've been following this thread as I have  the same problem exactly.
I did read on another forum that it could be a problem with the router software I have a D-Link DSL-G604T and following advice updated the software but really  to no avail. Sometimes for no reason I can explaim it works.
Did anyone else sort this mess out- Any help very much appreciated.

---

### Post by cptc on 2006-10-20
Hi
This worked for me at the moment

deb [http://195.248.90.23/ubuntu](http://195.248.90.23/ubuntu) dapper main restricted
deb [http://195.248.90.23/ubuntu](http://195.248.90.23/ubuntu) dapper-updates main restricted
deb [http://195.248.90.23/ubuntu](http://195.248.90.23/ubuntu) dapper-security main restricted

deb [http://195.248.90.23/ubuntu](http://195.248.90.23/ubuntu) dapper universe multiverse
deb [http://195.248.90.23/ubuntu](http://195.248.90.23/ubuntu) dapper-updates universe multiverse
deb [http://195.248.90.23/ubuntu](http://195.248.90.23/ubuntu) dapper-security universe multiverse

It seesm to be a translation issue of the Ip address

---

### Post by cptc on 2006-11-05
Hi
So my solution below worked for a while then just stopped again, By changing the IP address to 82.211.81.138 however it works again?
Quite confused.!

---

### Post by cptc on 2006-11-12
Hi
Did you solve this? I've tried lots of different things and sometimes it works sometimes it doesn't it is a real pain. I've had most success by putting the real IP address instead of the alias, but it is very flaky

Terence

---

