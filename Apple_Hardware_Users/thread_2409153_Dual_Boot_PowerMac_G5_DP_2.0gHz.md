---
title: "Dual Boot PowerMac G5 DP 2.0gHz"
date: 2018-12-28
forum: Apple Hardware Users
---

### Post by alexaxl12 on 2018-12-28
[COLOR=#333333][FONT=&quot]So,i ve got this PowerMac G5 A1047 1969C model with a DP 2.0 gHz,8GB RAM and a nVidia FX 5200 card[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]So,when i got it,it was running Ubuntu Mate 16.04 LTS and i changed that to Lubuntu 16.04 LTS(this is on a 160GB WD HDD)[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Now,i ve installed a fresh OS X 10.5.8(120 GB Kingston SSD V300) but i kinda have some issues selecting this one[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]For the most part,the system goes straight to Lubuntu,but if i give it a restart,and press the space bar a lot,it goes to Mac OS X 10.5.8[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]And now,is this how i should choose between Lubuntu and OS X,or do i need to do something else?[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Please be pacient,because i don't have experience with OS X,Lubuntu/Ubuntu/Linux or Mac's/Apple[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Thank you for you're time[/FONT][/COLOR]

---

### Post by gsahli on 2018-12-29
Lubuntu  is using yaboot as its boot manager. You should read about that online. To have yaboot find mac os 10, while booted  into  lubuntu, open a terminal and run the command: sudo ybin -v. (2 spaces) it asks for your admin password and doesn't  show it when typing.
reboot and yaboot will give you a simple start menu.
Another method:
Use the Mac's  boot manager by holding the option key after the gong (startup) sound.

---

