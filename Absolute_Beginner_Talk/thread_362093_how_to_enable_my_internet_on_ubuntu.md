---
title: "how to enable my internet on ubuntu?"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by d_maniger06 on 2007-02-15
hi everyone!

first of all i wanted to thank those people who helped me out on how to get an ubuntu installer that is not a live cd..i have done what you guys told me and i have now ubuntu on my pc..

since i am a newbie in a linux platform, i really dont know how to start using it..i would like to connect to the internet using my ubuntu but i cant..i tried to insert the driver cd for my router but it would just open the cd..can anyone give me instructions on how to set my ubuntu up so that i can connect to the internet and do some stuffs in ubuntu..

another problem which i have encountered is that my ubuntu doesnt produce some sounds..i dont know why..so can you help me out on this too?..

thanx for always!...

God bless!..

---

### Post by austin on 2007-02-15
is your router a DHCP server as well (that gives you an automatic IP address)? In this case you have to do nothing at all but plug in a cable.

what happens when you start firefox?

what happens if you start a terminal and type ifconfig?

what do you see in "Network Settings" in the menu under System -> Administration?

---

### Post by d_maniger06 on 2007-02-15
yes, my router is in dhcp..i havent tried typing ipconfig in the terminal and those other stuffs..im using my windows xp os now..that's why i can connect to the internet..does the ipconfig in the terminal of ubuntu will yield the same as i type ipconfig here in the terminal in windows?..if yes, then i would just give u the details here in my windows so that i wont be restarting my computer..but if i really need to restart, its fine with me..so what should i do?..

---

### Post by jingo811 on 2007-02-15
First things first what Ubuntu version are you using?
How do you connect to your router cable or wireless?

If you use cable
are you using an external NIC (Network Interface Card)?
or are you using the built-in NIC on your MOBO (motherboard)?

If NIC is built-in on MOBO can you check your specifications if it says Dual Internet/Network interface or something like that?

By the way!
Windows use= ipconfig
Ubuntu use= ifconfig

---

### Post by Obor on 2007-02-15
you can try ifup eth0 or sudo ifup eth0
to connect

---

### Post by austin on 2007-02-15
> **d_maniger06 said:**
> ..but if i really need to restart, its fine with me..so what should i do?..

you have to restart indeed. well i suggest you plug in the cable, boot into ubuntu and see if firefox works what might well be the case. if not reboot into windows and come back here

---

### Post by d_maniger06 on 2007-02-15
i have restarted my computer..ive open firefox but it would just open a starter page for ubuntu which is just a file in the computer..ive tried connecting to google but no page to be displayed..

---

### Post by austin on 2007-02-15
you could print this out:

[http://www.lesbell.com.au/Home.nsf/0/ac6983ac71a95aebca256f3800170b4f?OpenDocument](http://www.lesbell.com.au/Home.nsf/0/ac6983ac71a95aebca256f3800170b4f?OpenDocument)

and start the troubleshooting in ubuntu again

if ifconfig shows you eth0 with information about HWaddr you do not need the next section "Networking Not Configured During Installation"

Note that for most commands you have to put "sudo" before the actual command

---

