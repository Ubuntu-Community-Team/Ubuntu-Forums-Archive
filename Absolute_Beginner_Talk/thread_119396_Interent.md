---
title: "Interent"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by acid on 2006-01-19
Note: I am a Linux NEWBIE..I KNOW JACK ABOUT IT..But i really want to get into  it.

..I Just Installed Ubuntu On my 2ndary HD

and it loads fine and everything looks grand. But There are a few things i need to get sorted out first.

1: my interent..: I am usuing a Thompson Speedtouch ASDl modem...But i dont knowhow to set Up my Internet so i can download Stuff for Unbuntu..

could some one PLEASE Walk me thru this..And you need to use like baby lanuage..cos Im Compklety New to Ubuntu..Cheers

---

### Post by Azion on 2006-01-19
Is your modem internal or external?
In the case, or not

---

### Post by acid on 2006-01-19
[QUOTE=Azion]Is your modem internal or external?
In the case, or not[/QUOTE]

ROFL....Its External its a thompson SpeedTouch USB..the ones you get with your ISP In the Uk :P if anyone is from the Uk they will know what Im on about.

hardware I do ..been building my own pC's since i was 11..I just need to find out How to set Up my Modem In Ubuntu ...I saw a way to do this in another thred..But did not understand any of it,

PLEASE HELP ME

---

### Post by Azion on 2006-01-19
Well u didn't indicate.
Ok, how's it connected to ur PC?

---

### Post by mips on 2006-01-19
Whats the model number of the speedtouch ???
USB or Ethernet connection ?

---

### Post by linbetwin on 2006-01-19
Download firmware from the bottom of this page:
[http://www.speedtouch.com/driver_upgrade_lx_3.0.1.2.htm]("http://www.speedtouch.com/driver_upgrade_lx_3.0.1.2.htm")

and then read the instructions here:
[http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html]("http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html")

---

### Post by mips on 2006-01-19
Depending on your model:

[http://www.ubuntuforums.org/showthread.php?t=112094](http://www.ubuntuforums.org/showthread.php?t=112094)
[http://www.ubuntuforums.org/showthread.php?t=95431](http://www.ubuntuforums.org/showthread.php?t=95431)

Or do a search here for "speedtouch xxx" where xxx is your model

---

### Post by acid on 2006-01-19
ITs a Thompson SpeetTouch 330 ..It Connects Via USB..

So could some oNe explain (As easy simple as Possible)...How to get this Thing working so i can go Online

---

### Post by Azion on 2006-01-19
[http://www.ubuntuforums.org/showthread.php?t=102958&highlight=speedtouch+330](http://www.ubuntuforums.org/showthread.php?t=102958&highlight=speedtouch+330)
[https://wiki.ubuntu.com/UKSpeedtouchDSLHowTo](https://wiki.ubuntu.com/UKSpeedtouchDSLHowTo)
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

Pay special attention to the 2nd and 3rd links

---

### Post by linbetwin on 2006-01-19
I too have a Thomson modem connected through USB, but it's a cable modem, not DSL. It works "out of the box" in Ubuntu, I don't have to install or configure anything. My PC is connected to the Internet even before the installation of Ubuntu is completed. In fact, this is one of the reasons I settled on Ubuntu: it's the only distro I've tried that works with my modem.

---

### Post by mips on 2006-01-19
Follow the second link Azion posted, assuming you have Breezy.

---

### Post by acid on 2006-01-19
OK i tried the 2nd Link..and at one point it says..:
--------------
If this looks complex, you can just download and install [WWW] an unofficial firmware package 
--------------
So li clicked the link and downloaded the *.deb File.
I then went to the Terminal and typed:  

dpkg -i speedtouch-firmware_0.3012k.deb

But i get an error saying i need Superuser Privelidges...But i dont understand this cos I am the only User On the system..So arnt i the admin Already ?....

So how do i install this *.deb Package ??

---

### Post by linbetwin on 2006-01-19
sudo dpkg -i speedtouch-firmware_0.3012k.deb

then type your user password

---

### Post by bscbrit on 2006-01-19
Follow linbetwin's advice but, to answer your question, you are not given automatic priviliges even if you are the only user.  This is to protect both you and your system.

Typing 'sudo' before commands give you the priviliges you need.

---

### Post by acid on 2006-01-19
I get an error saying There is "no Such File"

where am i suposed to Put the *.deb File..??

---

### Post by firefly123 on 2006-02-05
Hi 
you will get going on line i got my globespan adsl usb to work and its quicker without all the xp rubbish using up  resources, the forum is a great help and support so dont give up!!!!!!!!!!!!!!!!!!!:p :p :p :p

---

### Post by bartbes on 2006-02-05
It doesn't matter where you place the file, but go to the place the file is before trying to install with dpkg. I think it's useful to put in /tmp or a tmpfs (read my howto to find out how to make one) because then you don't have to lose time deleting them

---

