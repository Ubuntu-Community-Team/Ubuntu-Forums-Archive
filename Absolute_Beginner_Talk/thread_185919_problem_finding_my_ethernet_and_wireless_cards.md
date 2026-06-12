---
title: "problem finding my ethernet and wireless cards"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2006-06-01
I have a HP Pavillion zv5000 laptop and just installed Dapper Drake.  
Previously, I had Breezy installed and I was able to connect to the internet without having to do any modifications to the OS.

Now that I have dapper drake, I figured that I wouldn't have some of the network problems I encountered with breezy but when I type in ifconfig in the terminal, I don't even see the eth or ath.  All I see is lo and it's values.

My wireless card is: BroadCom
Ethernet network card is: Realtek

I also went to system->Adminstration->Networking and enabled both of the cards individually to see if I could obtain an internet connection.  I am trying to connect to the internet using a Westell VersaLink 327W DSL modem.

Can anyone help me???

---

### Post by damianubuntu on 2006-06-01
Have you tiried
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide) ?

I know its for wireless but its a pretty comprehensive diagnostic imho.

Do/did you have both the eth and ath active at the same time?  On my system if I overlap the two, the whole of dapper freezes and I have to reboot.  For me I had to deactivate eth, close the networking gui, then re-open it and activate the ath (actually rausb in my case).

Hope this helps...

---

### Post by vanlue on 2007-02-15
Hey, racermike, did that troubleshooting guide end up fixing your problem?

I'm having a similar issue (I just did a clean install of Edgy) and was hoping to know that there is a good chance the guide worked before I power through it.

Thanks!

---

### Post by vanlue on 2007-02-22
Well, the guide worked for me!

It's an awesome guide.

---

### Post by Sunflower1970 on 2007-02-22
I'm glad I found this thread with that link. After two (pretty) smooth installs of Ubuntu on my desktops, I'm having a heck of a time with my laptop. Gonna have to look at that guide tonight. :) Just hopes it works with Feisty too...

---

### Post by vanlue on 2007-02-22
I'm no expert and I haven't looked into Fiesty much, but my guess would be that it would work.

It's a fairly general guide that is less copy/paste code and more step-by-step directions on how to find a solution to a broad range of problems.

---

