---
title: "How do I connect Ubuntu to the Net?"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Nilanjan on 2006-10-13
Do you know how to connect to the internet using Ubuntu - thru both dial up and cable broadband?:-k

---

### Post by Sef on 2006-10-13
Broadband should just be picked up.  If not, go to System > Administration > Networking.  Use that for dial up also.

---

### Post by unisol on 2006-10-13
for dialup if your using dapper right-click on the panel and select add to panel when the add to panel box opens choose modem monitor then click add when the applet appears right-click and select properties and fill in your dialup info. this may not work with edgy as the modem applet is broke ommy edgy cd

---

### Post by Nilanjan on 2006-10-14
Not being able to configure the dial up modem.It is not autodetecting and not configuring thru system>administration>networking.

---

### Post by unisol on 2006-10-14
are you using dapper or edgy? what is your isp

---

### Post by Nilanjan on 2006-10-14
> **unisol said:**
> are you using dapper or edgy? what is your isp

What is dapper and what is edgy? My isp is 10.129.120.1 Why? are you going to hack it??

:KS

---

### Post by xyz on 2006-10-14
Edgy is the latest Ubuntu; Dapper the preceeding one!!

---

### Post by unisol on 2006-10-14
of course not! dapper is the current stable release of ubuntu and edgy is the beta release. the reason i asked your isp is because with certain isps eg: msn you type msn/username in the dialup info for it to work if you would need help, the forum would gladly help you. try to add the modem monitor to your panel and see if that works

---

### Post by Beggar Su on 2006-10-14
> **Nilanjan said:**
> What is dapper and what is edgy? My isp is 10.129.120.1 Why? are you going to hack it??

:KS

Hi He was asking for your Internet Service Provider i.e aol, roadrunner etc not your IP address.

---

### Post by unisol on 2006-10-14
hey Beggar Su i was only trying to helpthe guy out no harm intended what i told him worked for me

---

### Post by Nilanjan on 2006-10-14
> **Beggar Su said:**
> Hi He was asking for your Internet Service Provider i.e aol, roadrunner etc not your IP address.

:rolleyes: Lol. Ok. Its sify broadband.Is that ok?

---

### Post by Nilanjan on 2006-10-15
Well the network connections is autodetecting my broadband cable connection (eth0) but it wont work till I download the broadband installer program. Any ideas on how I can do this without being connected to the net first??

Also the dialup modem connection is not activating. I dont know why. Ive typed in the phone nos. buth theres still some problem somewhere.

---

### Post by junglepeanut on 2006-10-15
I have setup dial up on a few computer (not my own) this is not fun, but straightforward if your hardware(or should I say software) is supported.

Basically it all boils down to on dial up if you have a real modem or a winmodem (fake software type of modem) If you got to 

[http://linmodems.org/](http://linmodems.org/)

and follow everything you should be able to set it up if yours is detected and if the detected version is supported. 

I believe somebody may have a how to on here as well.

As for broadband if the networking thing is not working you can use the terminal.

you may have to read the man pages to get a clear understanding of what needs to be done. 

ifconfig

iwconfig

ifup ifdown

I suspect it will be the ifup and ifdown commands you need to use most, but run ifconfig first to see who is up and doing what.

---

### Post by Nilanjan on 2006-10-16
> **junglepeanut said:**
> I have setup dial up on a few computer (not my own) this is not fun, but straightforward if your hardware(or should I say software) is supported.

Basically it all boils down to on dial up if you have a real modem or a winmodem (fake software type of modem) If you got to 

[http://linmodems.org/](http://linmodems.org/)

and follow everything you should be able to set it up if yours is detected and if the detected version is supported. 

I believe somebody may have a how to on here as well.

As for broadband if the networking thing is not working you can use the terminal.

you may have to read the man pages to get a clear understanding of what needs to be done. 

ifconfig

iwconfig

ifup ifdown

I suspect it will be the ifup and ifdown commands you need to use most, but run ifconfig first to see who is up and doing what.

I have a real modem (for the dialup) and it is not activating.

---

### Post by junglepeanut on 2006-10-16
What was the output from scanModem as to the relevant information (i.e. don't post anything that may be sensitive)

I think if it was a real modem some of the information will be in ModemData.txt and the other will be yourmodem.txt (capitalization may be different). Just incase it was softmodem you may want to see what it says in softmodem.txt.

---

### Post by junglepeanut on 2006-10-16
Also I am unsure what the broadband installer program is, but I just realized maybe you have not even done the Linmodems stuff yet. And are just assuming it is real, I could be wrong here though, since you have no Internet connection on the ubuntu box. So if you haven't already you can for the scanModem script put it on a cd or usb with whatever you are able to connect to the Internet with and then use that to put on your desktop. Again I don't know what the broadband installer is but I suspect the same option should work for that as well.

---

### Post by Nilanjan on 2006-10-20
> **junglepeanut said:**
> Also I am unsure what the broadband installer program is, but I just realized maybe you have not even done the Linmodems stuff yet. And are just assuming it is real, I could be wrong here though, since you have no Internet connection on the ubuntu box. So if you haven't already you can for the scanModem script put it on a cd or usb with whatever you are able to connect to the Internet with and then use that to put on your desktop. Again I don't know what the broadband installer is but I suspect the same option should work for that as well.

The broadband intaller is a program downloaded from the net for subscribers of my isp- sifybroadband.com You download it to install the client program on yr computer thru which subscribers login to their paid broadband subscription. It installs the login program for you. Without it you cant login, even if linux/Ub. detects yr active network connection (eth0). 
The client download url [http://202.144.65.70:8090/](http://202.144.65.70:8090/)  is not opening in firefox.

---

### Post by Nilanjan on 2006-10-22
Still havent been able to connect to the net, using either the cable network or dialup.

---

### Post by Nilanjan on 2006-10-22
Still havent been able to connect to the net, using either the cable network or dialup.:KS

---

### Post by Nilanjan on 2006-10-23
Any help/advice anyone?

---

### Post by Nilanjan on 2006-10-25
Finally connected to the net using the broadband cable connection- but its so slow & the broadband client installer program which i downloaded is not extracting/opening/installing.
Anyway, I FINALLY connnected to the NET!HURRAY!

The firefox is really slow and its taking ages to open any site. Also it doesnt respond to any of the commands to close tabs, minimize, maximize etc. easily. Difficult to use.

Does anyone know how to ping in Ubuntu?? Is there a RUN command?

---

### Post by KoRnholio on 2006-10-25
Go to Applications -> Accessories -> Terminal and you'll have the ping command.

ping [www.yahoo.com](www.yahoo.com) 

for example.

run command is simply typing the name of the program into the Terminal.

---

