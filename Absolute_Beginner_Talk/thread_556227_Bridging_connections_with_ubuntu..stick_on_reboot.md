---
title: "Bridging connections with ubuntu..stick on reboot?"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by PreviousN on 2007-09-21
Hello,

I've got a ubuntu server that is "headless". I recently just plugged in a monitor so I could configure bridging. Below I will give what I currently have and then what I want:

== Current: ==
Ubuntu server (gigabit) ==> (gigabit) Windows (100mbit) ==>  (dhcp 100mbit) router ==> cable modem

I've connected my server and windows together w/gigabit because I've got a buch of hard drives on the ubuntu machine and specifically, a raid that I use via a samba share on my windows computer to backup important documents. So, overall, my entire network runs on 100mbit, except for the connection between my windows and ubuntu server (using a crossover cable, of course).

== What I want ==
Windows (gigabit) ==> (gigabit)(eth1) ubuntu server (10/100)(eth0) ==> (dhcp) router ==> cable modem
Third computer      ==> (10/100)(eth2) ubuntu server ----------- ^^^^^

side note: I've followed this guide somewhat: [http://www.virtualbox.org/wiki/Automatic_Bridge_Ubuntu](http://www.virtualbox.org/wiki/Automatic_Bridge_Ubuntu) and have managed to f*ck up my /etc/networking file. Does anyone have a default they can paste in that I can use? I forgot to make a backup...(opps)

So from what I understand I type in 
{{ brctl addbr br0 }}
{{ brctl addif br0 eth1}}
{{ brctl addif br0 eth0}}
{{ brctl addif br0 eth2}}
{{ ifconfig br0 up        }}
And sometimes that works...but I frequently (ok...like once a month) have to reboot my server . Since I administer it via ssh and need to access the samba shares, the fact that bridging doesn't start on boot is a pain. Especially considering that this computer doesn't have a keyboard, mouse, or display plugged in. 

== what I need help with ==
How do I make it run on boot? Do I add these to my /etc/rc.d/local? Guidance?
A pasted in /etc/networks file. If these are "unique" just paste yours and I can probably figure it out myself.

---

### Post by PreviousN on 2007-09-21
36 minutes and no reply? Is briding connections really that difficult? Please help me, this is quite irritating! (bump)

---

### Post by PreviousN on 2007-09-21
Sigh...thanks a TON for the help guys. I've been waiting nearly an hour and only 5 views and no reply. A simple "don't know, here's a link" woudl have helped...sigh.

---

### Post by dmizer on 2007-09-21
bumping after only 30 minutes actually _hurts_ your chances of getting a helpful reply.

there is a support group here, dedicated to answering posts with no answers.  since you bumped your own thread, your thread no longer appears as a zero reply thread and this group is more likely to overlook your thread.

what's more, this forum (unlike many other forums you may be familiar with) is extremely active, and folks like me regularly go through several days worth of posts looking for people who have not gotten a useful reply.  i have at least one thread that went for over a month with no reply before someone gave me the answer i needed.

also keep in mind, i have your answer.  but i'm not available online all day long ... all week long.  everyone here is volunteering their help.  no one is paid to give you your answer.

moral of the story?  just because it drops off the first page does not mean your post is gone forever.

what you need is to set your ubuntu server up with network address translation (not bridging) like so: [https://help.ubuntu.com/community/InternetConnectionSharing?](https://help.ubuntu.com/community/InternetConnectionSharing?)

yes, bridging will also work, but network address translation is easier.

---

### Post by spd106 on 2007-09-21
There's also a help docs page on bridging here [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)
and another one more about routing here [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

In this case bridging would be acceptable and involve less overhead on the Ubuntu PC than NAT would.

If you need help in a short amount of time try IRC.

---

### Post by PreviousN on 2007-09-22
Hey guys,

Thanks so much for getting back to me. I guess I just was too impatient. And thanks for the tip on not bumping. 

I know that no one gets paid for helping others around here, which is exactly why I thought that my post was just overlooked because it seemed that I wasn't like a "new user" that was considering going back to windows or somthing like that. In retrospect, I'm sorry, it wont happen again. I work as a tech support (for windows/mac computers mainly) and have to go through the same thing (users being beligerent if they don't get a reply right away) I should have known. Sorry.

Also, thanks a TON for those links. I haven't looked at them yet but will do. I may have to rereply to this if they don't start on boot though. Thats my main problem.

Thanks for the tip about bridging taking less horsepower than NAT. I'm on a tight budget and my server is a pentium III (600mhz) and only 384 megs of ram...so nat might be too much of a performance hit. 

Thank you very much again!

---

### Post by PreviousN on 2007-09-22
Well...like I thought, the guide didn't have instructions for the bridge to auto up on reboot. Any ideas?

After rebooting I type 
{{ifconfig bridge up}}
and It replys: "bridge: ERROR while getting interface flags: No such device"

So I guess its back to square one...Maybe I wasn't specific enough when I first posted. How do you make these start on boot? Do I just add


ifconfig eth0 0.0.0.0
ifconfig eth1 0.0.0.0
ifconfig eth2 0.0.0.0
brctl addbr bridge
brctl addif bridge eth0
brctl addif bridge eth2
brctl addif bridge eth3
ifconfig bridge up
dhclient bridge

to my "etc/rc.local" file?

---

### Post by dmizer on 2007-09-23
i still think nat is going to be your better option despite the horsepower loss, and here's why.

with bridging, your windows machine gets its ip address from your 100mb router (via your ubuntu server).  so, when your windows machine talks to your ubuntu server, you only get 100mb because all the traffic is carried through the 100mb router.

if you set up nat, your windows machine will pull its ip address directly from the ubuntu server in a separate 1000mb subnet.  so when your windows machine talks to your ubuntu server, you get gigabit throughput.

also:
> **PreviousN said:**
> How do you make these start on boot? Do I just add

[snip]

to my "etc/rc.local" file?
why not try it?  it's not going to hurt anything if it doesn't work, and it does seem like a possible solution (perhaps not the best solution ... but we're graded on results, no?)

---

### Post by PreviousN on 2007-09-23
Hmm. Seems you were right about the performance hit. I used to get 20mB/s when windows was doing ICS but now I hardly get over 14mB/s between the two. I'll try routing with NAT to see if its faster, if not, I dunno what I'll do. 5-6mB/s is a lot of bandwidth loss.

Thanks for following up. I tried adding it to rc.local, and it works well enough, if not very elegantly. I keep thinking it won't be as reliable as if I had done it separatly. Isn't there like a 

brctl saveconfig bridge

then add to inet.conf "bridge = dhcp = yes?"

Oh well. We indeed are graded on results.

---

