---
title: "Apple airport card help..."
date: 2007-04-22
forum: Apple PPC Users
---

### Post by mrbugspray on 2007-04-22
Hey,
can somebody help me with my airport extreme card? I installed ubuntu dapper once, but I couldn't get wireless internet via airport to work. ](*,)  Please help.

Thanks, 



Mr. Bugspray

---

### Post by tgalati4 on 2007-04-22
Try installing 6.06.1 Dapper.  I got it to work with a Powebook G4, 1 GHz.  Wireless worked without configuration.  I believe it used ndiswrapper but I don't remember.  I went back to Tiger because Dapper still had some fit-and-finish problems with the powerbook.

To enjoy Ubuntu goodness, you can install XDarwin, run startx in a terminal, then 
ssh -Y -2 user@yourubuntumachine

Any you can run just about any application from an Ubuntu desktop on your powerbook.  You can also install Fink Commander and directly install many Linux programs.  There is also a growing list of ports of popular packages (like Kismet) to the Cocoa environment.  

I have to admit, Tiger 10.4.8 is a solid operating system.  I get uptimes of several weeks, only rebooting when updates require it.

---

### Post by stmiller on 2007-04-22
Install the fwcutter package. This extracts the broadcom firmware for the driver to work. Ubuntu cannot include this proprietary driver firmware by default.
This is ALL over the ubuntu forums. Please use the search function.

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

### Post by mrbugspray on 2007-04-22
Thanks

---

### Post by ego1 on 2007-04-23
sudo apt-get install bcm43xx-fwcutter

This will install fwcutter and will download the Airport driver too.
It is wonderful, nothing more and you can have airport extreme running with network-manager.
Only I'd seem a bug with wpa, for the password we must put the result of

wpa_passphrase SSID passphase

where SSID is the SSID name of wireless network
           
for example

user@chancleta:~$ wpa_passphrase HomeWireless contraseña
network={
        ssid="HomeWireless"
        #psk="contraseña"
        psk=3feece65d7e374f9c17ea783172e3e22d37150546a89ee629393156f510466ce
}
user@chancleta:~$ 

them copy 3feece65d7e374f9c17ea783172e3e22d37150546a89ee629393156f510466ce
and paste in the password field in network manager.

---

