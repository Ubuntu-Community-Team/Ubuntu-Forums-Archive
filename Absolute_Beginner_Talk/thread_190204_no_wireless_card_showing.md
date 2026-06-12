---
title: "no wireless card showing"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by richieboy on 2006-06-06
i bought a compaq v2610us notebook with windows xp.  it has a wireless card that worked.  i overwrote the entire hard drive with ubuntu 5.10 now my wireless card doesn't show up.

i get this message with lspci | grep Broadcom\ Corporation:

0000:05:02.0 Network controller:  Broadcom Corporation:  Unknown device 4318 (rev 02).

i'm guessing this refers to the wireless card. 

how do i get it up and working???????](*,) 

please help.

rich

---

### Post by nalmeth on 2006-06-06
First, don't panic, your thread is incorrectly titled because the device is showing! :)

Second, is it possible to for you to do a fresh install of the newest release (Dapper Drake 6.06)?

Either way, take a read of the Wireless Help link in my signature, and if it's *way* too much information, post back in this thread with anything you've learned or anymore question's.

Essentially, you'll probably end up installing an app called ndiswrapper to run a window's wireless driver.

Skip through all the noise about getting the card detected, because you've gotten that far already!

---

### Post by richieboy on 2006-06-08
nalmath,  i upgraded to dapper and, woo hoo, now it shows my "wireless connection under network settings.  i went through your help manual and found this info:

running lshw -C network i get:

*-network:1 Disabled
              desc:  wireless iface      (my abbreviations until what i hope is the                                 important stuff)
              product: bcm4318 (air force one 54g) wireless lan cont


              bus info: pci@05:02.0
              serial: 00:14:a5:7f:a4:bf
              clock  33mhz
              config:  bcast=yes driver=bcm43xx driverversion=2.6.15-23-386 link=no muticast=yes wireless=IEEE 802.11b/g resources:  iomemory:c0204000-c0205fff irq=217


iwconfig shows this:

eth1 IEEE 802.11B/G ESSID:OFF/ANY NICKNAME:"BROADCOM4318" MODE:MANAGED ACCESS POINT: INVALID BIT RATE=1 MB/S
RTS THR:OFF FRAMENT THR:OFF
ENC KEY:OFF LINK QUAL:0 SIG LEVEL:0 NOISE LEVEL:0 RX INVALID NWID:0
RX INVALID CRYPT:0 RX INVALID FRAG:0 TX EC\SCESSIVE RETRIES:0 INVALID MISC:0 MISSED BEACON:0


sorry for all the caps.  do the rx s mean prescriptions/recomendations?  does this info help at all or should i download th ndiswrapper thing?

thanks,
rich

---

### Post by nalmeth on 2006-06-08
If activating the device in Network Settings doesn't work, then I would go with ndiswrapper. There is a graphical front-end called ndisgtk. I'm pretty sure you need a .inf file or something, the program should explain that I think. Can you dig up a windows wireless driver?

In the terminal install ndiswrapper and the gui with:
sudo apt-get install ndiswrapper ndisgtk

and run it. You probably need admin priviledges to run it, so apphend sudo to the command

sudo ndisgtk

From this GUI you can browse to the location of the driver and install it.

Hopefully that works for you.

---

### Post by richieboy on 2006-06-08
sorry to be an idiot but i don't know where to look for drivers, in what folder i mean.  where would the inf file be.  also i ran ndiswrapper from the command line.  i did the modprobe alias thing and the -l switch told me no drivers are installed.
i'm trying but i'm very slow.
thanks for the help.
rich

---

### Post by nalmeth on 2006-06-08
Sorry, I'm not very clear today it seems. You'll have to browse the net to find the driver (google will find it), or if you have a CD it might be on there. Can you access the net and get the inf over to ubuntu? Maybe on a floppy or CD?

BTW how *are* you accessing the net? Have a temporary direct link? I totally didn't even think that you might not be able to install through apt-get.

I'm a little off today :\

---

### Post by richieboy on 2006-06-08
you are not off today,  you are helping me very much.  i get online with my desktop and by plugging the ethernet cable into the notebook.  ethernet works just not wireless, yet.
thanks,
rich

---

### Post by nalmeth on 2006-06-08
Great that makes things much easier
Do you have a CD that came with the wireless card? If so you can copy the inf to somewhere of your choice, or use the ndisgtk app to browse to your CD (/media/cdrom) and find it that way.

If not, you'll have to find a driver provided by Broadcom, I tried looking briefly, and it wasn't as easy as I assumed it would be. Other companies like D-Link seem to make it easier to find a driver. 

What's the model name of the card?

---

### Post by nalmeth on 2006-06-09
How did this work out richie?

---

### Post by richieboy on 2006-06-09
i found a driver and a sys file.  i'm going to put them in tonight.  cross your fingers.:???:

---

