---
title: "Internet not available on start up"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Vaidya on 2007-06-09
I am using Feisty.

The problem is that when ever I restart my machine, I have to always go to network tools, select the location option (which is always greyed out when I start the machine), select my only available location, which causes the DNS settings to set to those supplied by my ISP, hence giving me access to the internet.

I want to know if this can be done automatically, and if so what do I need to do in order to enable automatic access to the internet when I start up my machine?

Thanks in advance

---

### Post by Vaidya on 2007-06-09
Well, this post has seen a few lookups, but it seems no one has a similar problem or a solution to offer.

Can it be I am the only one in the wide world with this problem?

Heh, in a nerdy way, that almost makes me feel good... (it MY problem, I will not give it away to anyone - go away!):D

But seriously, some please do drop in a solution for me please...

---

### Post by Tux Aubrey on 2007-06-09
Ok, I'll bite.:)  

I have no idea, really, but maybe you could check that network manager is loading in session manager?  Save the session config anyway and see what happens.

Keep bumping if that doesn't work.  Some more Europeans or Americans should be awake soon.  That's the trouble with timezones.  Sometimes there's no one here but a few clueless Australians and Japanese.:)

---

### Post by ghost_ryder35 on 2007-06-09
i have a very similar problem with network manager.  i have figured out that it is due to me not broadcasting my ssid in my wireless router.  so everytime I reboot, i must manually connect.  my solution was downloading that app called "wifi" and adding it to the startup programs under  session settings.  and just have to hit connect to my wireless connection everytime.  it does a much better job than network manager.

---

### Post by pardesi on 2007-06-09
do you have a static IP adress or a DHCP .Post what your computer shows when you write
```
sudo gedit /etc/network/interfaces
```

---

### Post by sirgazil on 2007-06-09
> do you have a static IP adress or a DHCP .Post what your computer shows when you write
Code:

```
sudo gedit /etc/network/interfaces
```

Hey **pardesi**, [[COLOR="Sienna"]_here's a recomendation_[/COLOR]]("https://help.ubuntu.com/community/gedit") from the documentation of Ubuntu:

> ```
gksudo gedit /etc/network/interfaces
```

Note: If you need to run graphical applications as root, use gksudo, as shown above, as it will set up the environment more appropriately. Avoid ever using sudo with gui apps. 

;)

---

### Post by Vaidya on 2007-06-10
Hi Thanks Pardesi.

Here is the output of the command you asked me to run: (incidentally mine is a wired connection, thought I should let you know)

++++++
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




auto eth0

---

### Post by pardesi on 2007-06-10
thanks **sirgazil** 
well vaidya do you use ur net via eth0

---

### Post by Vaidya on 2007-06-10
yes, i do access my net through eth0, I have an adsl modem, on which the pppoeconf does not work (it gives time out error, hence a no go option for me :( ...)

---

### Post by pardesi on 2007-06-10
then 
```
gksudo gedit /etc/network/interfaces
```
now change what you have to 
```
 auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 127.0.0.1
netmask 255.0.0.0

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```
 save and reboot

---

### Post by Vaidya on 2007-06-10
Whew ... this is turning out to be tougher than I thought.

I did what you suggested, it did not work...

Funny thing is that while i diligently changed everything around and rebooted twice, while I was trying to copy paste my new file, I got a message in the Gnome terminal that the file had been changed on the disk, do you want to reload? I did so and it had stripped of the address and mask lines off neatly, as below:




auto lo
iface lo inet loopback

# 2 lines inserted -SV

auto eth0
iface eth0 inet dhcp


# iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




# auto eth0

+++

I am trying to do this yet again, let me see what happens...

:(

---

### Post by pardesi on 2007-06-10
wait wait what did you copy paste

---

### Post by pardesi on 2007-06-10
just  write the first code gksudo...
then you will be directed to a Gedit text file.there just change the things as i had told you then just save the file.close the Gedit.come out reboot and post what  you get and do nothing else

---

### Post by Vaidya on 2007-06-10
Ok. Back again.

This is what i did:

1. ran gksudo as you suggested, ran the command (copy pasted ur input) as root.

2. Copy pasted the lines from your post

3. saved and re booted.

4. here is the output from the interfaces file:
 auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 127.0.0.1
netmask 255.0.0.0

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

AND Right now, there is a yellow warning band on top of terminal stating that the file has changed on disk, do you want to reload?

I have NOT reloaded at the moment, but I'll bet it will strip the addres and netmask lines off ...

---

### Post by Vaidya on 2007-06-10
And yes, the original problem still persists...

---

### Post by pardesi on 2007-06-10
ok just remove those ip address and netmask from the file save it and reboot.write your output of
the previous code .

---

### Post by Vaidya on 2007-06-10
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

This is what i have now, before I reboot...

---

### Post by pardesi on 2007-06-10
ok is it fine if not then 
first go to system<adminstration<network and see if under connection heading DHCP is selected and if not  go to properties and change to DHCP...

---

### Post by Vaidya on 2007-06-10
back yet again... yes, connection heading DHCP is selected...

Man! I guess I will have to live with this it seems

But I really appreciate your efforts and your help.

Thank you very much, you have been prompt and have been at my prob for a long long time !

---

### Post by pardesi on 2007-06-10
i live witha even stupid problem than yours i need to reboot my computer after each time booting before FF opens anything .....:(

---

