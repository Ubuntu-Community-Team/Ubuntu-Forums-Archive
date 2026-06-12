---
title: "INTERNET on xubuntu"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by ninguem_vj on 2006-06-21
...hi there...I´m pretty new to linux...first one I instaled and tried was xubuntu...earliers today...but I had a problem with the internet connection...

...basically, I coudn´t find a place to add a new connection...I guess I´m all spoiled by windows XP...but I really need help...

...how do I configure an INTERNET DSL connection on xubuntu?

...I had to skip that step on the instalation...cause my card wasn´t found by the system...and on the tutorial I was following, it said I could leave it for later...but there where no explanation for later...

...well...I hope I´ve made myself clear enough...

...I´m runnin' a P3-700mhz-128mb RAM-16mb video...for pourpouses of testing and puttin' it on my regular using computer...

...so...please...help...and more than that...thanx allready...

ninguem

---

### Post by Brunellus on 2006-06-21
Post the hardware you use to connect to the internet.  Make and model of A) Your DSL modem and B) (if applicable) the router.

---

### Post by nalmeth on 2006-06-21
Just using direct connection?
try this command to restart DHCP

sudo /etc/init.d/networking restart

For some wired troubleshooting:
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

---

### Post by ninguem_vj on 2006-06-22
[QUOTE=Brunellus]Post the hardware you use to connect to the internet.  Make and model of A) Your DSL modem and B) (if applicable) the router.[/QUOTE]


...sorry for the delay...I was trying a bit more with the connection...but had no succes...

...I use a 10-100 T eth adapter (CNET 200 pro)...goes straight to the internet modem...(SpeedTouch 510)...no router...

...ok...I´m goin´ back to the battle and expect to hear from you soon...

...thanxx again...

---

### Post by ninguem_vj on 2006-06-22
[QUOTE=nalmeth]Just using direct connection?
try this command to restart DHCP

sudo /etc/init.d/networking restart

For some wired troubleshooting:
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)[/QUOTE]


...hi there...I tryed the command...and the answer I got was:

"(...)
No DHCPOFFERS recived
No working leases in persistent database - sleeping."

---

### Post by Brunellus on 2006-06-22
have a look in this thread and see if it doesn't also address your problem:

[http://www.ubuntuforums.org/showthread.php?t=201674](http://www.ubuntuforums.org/showthread.php?t=201674)

---

### Post by underdog on 2006-06-22
When you configured your internet connection on your xp computer, did you have to ever type in your IP address (a group of numbers xxx.xxx.xxx.xxx)? DHCP is what assigns this number to your computer, if your ISP doesn't assign you one through DHCP you need to manually specify it.

---

### Post by ninguem_vj on 2006-06-22
...I never had to type any IP...on windows...I guess my isp uses dynamic IP...or something like that...

...those linx seem to be of good help...every little thing explained...the files and all...only thing now is that I discovered that my floppy is not properlly configured, so I can´t take the files from my working computer to the LINUX one...but I´m working on it...and I tryed by CD-rom, but XUBUNTO didn´t read the CD I recorded on windows...guess I´m being stupid here...but...how do I record something on windows to be seein´ on LINUX?

...well...questions questions and more questions...hope I get somewhere...

...thanx ya´ll...

ninguem.

---

### Post by MaximB on 2006-06-22
if you use adsl as I did in winxp - you had to type your username and password to log to the net 
if so we covered this question from top to buttom but I will help you
go to the console/terminal (I hope you know were it is by now)
enter the command :
sudo pppoeconf 
hit return
provide your first ubuntu user password (super user)
then you will be asked for your username and password that your ISP gave you and other simple things
after that you will be aoutomaticly connected. (if you chose to)

if you'll have other problems then search for them on the forum - most of them were already answered by somone.

---

### Post by ninguem_vj on 2006-06-22
[QUOTE=MAXDDARK]if you use adsl as I did in winxp - you had to type your username and password to log to the net 
if so we covered this question from top to buttom but I will help you
go to the console/terminal (I hope you know were it is by now)
enter the command :
sudo pppoeconf 
hit return
provide your first ubuntu user password (super user)
then you will be asked for your username and password that your ISP gave you and other simple things
after that you will be aoutomaticly connected. (if you chose to)

if you'll have other problems then search for them on the forum - most of them were already answered by somone.[/QUOTE]

...thanxx maxddark, for real, but my problems start exactly there...when I hit the pppoe command, the program finds the card, but does not find any connection to the modem...

...I guess I´ll have to go through the steps provided by our colleague up here, for the modem config...

...my problem now is knowing some really basic thing, witch is: can I burn a DATA CD on windows and open it on the xubuntu?...or how to do that...cause I got the necessary files, but I can´t put them on the computer where linux is...

...I´ll keep struggling...

ninguem.

---

### Post by ninguem_vj on 2006-06-22
I really don´t wanna choke on my first cup of ubuntu...

---

