---
title: "Internet Help/Questions that don't seem to be answered anywhere else"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by ukjmn on 2007-03-02
ive tried to find threads and docs that refer to my type of situation but my problem is very wierd. i am a beginer hence the reason why i posting here instead of someplace else. 

my problem lies within any program that requires use of the internet. i used ubutu dapper for about a week or 2 when suddenly wen im starting to feel pretty confident moving around it and getting things to work properly when anything requiring interent use can not recieve content. when watching my interent connectivity it will briefly go from idle to sending/recieving but pages and or programs never load or gather the content. oddly enough though ubuntu.com and some forum pages work perfectly fine. i just dont understand this. now i booted from my live cd with hopes of reinstalling dapper, but just to test it i tried to browse the interent from my live cd and this had the same exact problems as w/o the live cd. so idk if anyone can help me it would be greatly appreciated

---

### Post by janz84 on 2007-03-02
Is it the internet in general or downloading and installing software?

If it's the downloading of software part, you may just be using a slow depo.

---

### Post by ukjmn on 2007-03-02
ummm... well basically the interent only works when accessing ubuntu.com

---

### Post by janz84 on 2007-03-02
are you currently posting from your windows setup? 

if yes, does your isp have specific network settings or are you configured via DHCP?

also, is your modem a usb modem or do you have a regular lan hookup?

---

### Post by undertakingyou on 2007-03-02
Sounds like a very likely DNS problem.  You could use OpenDNS (a Google search will show them).  Goto SYSTEM=>ADMINISTRATOR=>NETWORKING and go to the DNS tab.  Place in the IP's gotten from the website (I think they are 208.65.222.222 and 220.220  I'm not sure though) and then try the web.

---

### Post by ukjmn on 2007-03-05
yes!! changing my DNS to OpenDNS works!

only problem now is that for some reason it automatically switches back and takes off the new DNS's and puts the old ones that dont work back in? can i fix this permanetly so i dont have to keep going back and putting the DNS's in?

---

### Post by dosmode on 2007-03-05
Hope this helps... it did for me.
From the console type:
sudo -s  
(You will be asked for your password, then)
gedit /etc/resolv.conf

Enter your DNS numbers, save and exit...

---

### Post by ukjmn on 2007-03-05
yea i had done this from the start but for some reason it keeps changing back??

---

### Post by dosmode on 2007-03-05
I have been using Ubuntu for about the same time as you and have not had that problem... so far... I don't think it should be doing that... and I hope it doesn't  eventually does it on my system...
It seems like a feedback on this is in order from a hardcore Linux/Ubuntu user...
Sorry I could not be of any help...

---

