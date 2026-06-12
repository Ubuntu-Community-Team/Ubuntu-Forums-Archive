---
title: "Ndiswrapper installed for wireless setup?"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-04
I was told somewhere that ubuntu has ndiswrapper pre installed, is that the case?  At the wiki site for ndiswrapper I found this about my pcmcia card:

# Card: Linksys #[WPC54G v3], 54Mbps -- [link here|List#WPC54G v3]

    * Chipset: Broadcom Corporation BCM4318 802.11/g Wireless LAN
    * pciid: 14e4:4318
    * Driver: ndiswrapper v1.3 with bcmwl5a.inf [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/) (Broadcom, 12/22/2004, v3.100.46.0)
    * Other: linux-2.6.8 kernel, debian, card worked well
    * Other: linux-2.6.14 kernel, debian, ndiswrapper 1.9, wpa_supplicant 0.4.7, driver [ftp://ftp.linksys.com/international/drivers/WPC54G_driver_utility_v3.1.zip](ftp://ftp.linksys.com/international/drivers/WPC54G_driver_utility_v3.1.zip), works with WPA2 

Do I need to find what kind of kernal I have?  Im not quite sure what these instructions/information means...How do I get the drivers into ubuntu without a net connection ect...??

---

### Post by carlosqueso on 2006-04-04
You need to download the windows driver and unzip it.  Save the .inf and .sys files to a folder on a floppy/CD/usbdisk.  You will also need the ndiswrapper-utils package from [http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils](http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils) 

Then you need to copy the windows drivers, and the .deb file with ndiswrapper-utils to a part of your disk that you will be able to find. Navigate to the directory to which you copied the ndiswrapper-utils_1.1-4ubuntu2_i386.deb file and type ```
sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb
``` and it'll install the ndiswrapper package.  Since you found that site, I"m assuming you know how to use ndiswrapper, so I won't go into that unless you want me to.

---

### Post by karthik085 on 2006-04-04
[QUOTE=x5452]I was told somewhere that ubuntu has ndiswrapper pre installed, is that the case?  At the wiki site for ndiswrapper I found this about my pcmcia card:

# Card: Linksys #[WPC54G v3], 54Mbps -- [link here|List#WPC54G v3]

    * Chipset: Broadcom Corporation BCM4318 802.11/g Wireless LAN
    * pciid: 14e4:4318
    * Driver: ndiswrapper v1.3 with bcmwl5a.inf [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/) (Broadcom, 12/22/2004, v3.100.46.0)
    * Other: linux-2.6.8 kernel, debian, card worked well
    * Other: linux-2.6.14 kernel, debian, ndiswrapper 1.9, wpa_supplicant 0.4.7, driver [ftp://ftp.linksys.com/international/drivers/WPC54G_driver_utility_v3.1.zip](ftp://ftp.linksys.com/international/drivers/WPC54G_driver_utility_v3.1.zip), works with WPA2 

Do I need to find what kind of kernal I have?  Im not quite sure what these instructions/information means...How do I get the drivers into ubuntu without a net connection ect...??[/QUOTE]
Summary:
[http://ubuntuforums.org/showpost.php?p=113584&postcount=7](http://ubuntuforums.org/showpost.php?p=113584&postcount=7)

Ndiswrapper Wiki:
[http://ndiswrapper.sourceforge.net/support.html](http://ndiswrapper.sourceforge.net/support.html)

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

There are many discussions and solutions, if you search on ubuntuforums.
Try other ways - ethernet/modem etc. If none of them works for you, copy the drivers and necessary files from a computer with net connection, into a floppy/cd/usb drive etc and transfer it to Ubuntu.

---

### Post by x5452 on 2006-04-04
thanks for your reply and if you wouldnt mind, id be very grateful if youd go into it, I found the site by following link after link trying to find some instructions fit for a moron, (me).  I dont know how to use ndiswrapper, Im following instructions in the wiki how to and it says to download two packages, which I did, Im also downloading the two drivers from that other site, (im not sure which one I need..) the wiki says once i download the packages, to 
Copy the appropriate files over to a directory on your ubuntu machine (a good location is /home/(user_name)/drivers) and install them in this order: 

sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb

sudo dpkg -i ndisgtk_0.5-1ubuntu1_all.deb

Ok I see that, but how do you do this?  Do i burn the files to a cd from this laptop and pop the cd into the other laptop( with ubuntu)?  And only copy certain files to where?  I cant find anything like windows explorer or something, so I dont know how to get to where I can copy files. So If you woldnt mind throwing me a quick idiots walkthrough, thanks!  :-)

---

### Post by shyopstv on 2006-04-04
I am far from an expert and I am also in XP so can't remeber exactly what you do but the Windows explorer type thing is on Go To --> Filesystem but tbh I find it easier to go to "home" when i am deciding where to put files

---

### Post by x5452 on 2006-04-04
yeah i have read a lot of places to put things in /home... but where is home?  I thought it was like a 'tree type directory' but i cant find it

---

### Post by carlosqueso on 2006-04-04
[QUOTE=x5452]
Ok I see that, but how do you do this?  Do i burn the files to a cd from this laptop and pop the cd into the other laptop( with ubuntu)?  And only copy certain files to where?  I cant find anything like windows explorer or something, so I dont know how to get to where I can copy files. So If you woldnt mind throwing me a quick idiots walkthrough, thanks!  :-)[/QUOTE]

Yes, just burn the files onto a CD.  Download the ndiswrapper file from the link I gave you and the 802.11g driver from the [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/) website.  Copy those to cd from your win box, and pop it into your Ubuntu box.  You should then copy them from the cd to your desktop. Double-click the .zip file that the windows drivers are in and you should be able to extract them to your hard drive.  Just straight-up copy the .deb file to the desktop

Then, fire up a terminal and change to the Desktop directory with ```
cd Desktop
``` and install the ndiswrapper deb with ```
sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb
``` 
If you extracted the drivers to another folder, you'll need to cd into it.  Then you can install the driver with ```
sudo ndiswrapper -i <INF file>
sudo modprobe ndiswrapper
``` where <INF file> is the name of your driver's .inf file.  You should then be able to bring up your wireless card with ```
sudo ifup wlan0
```

If you run into problems, check two things before posting.  First, make sure that you are in the directory with your driver.  Second, remember that, unlike windows, linux is CaSe SeNsItIvE and won't work if you use the wrong case.  After you check those, post back and we'll be happy to help to the best of our abilities.

---

### Post by karthik085 on 2006-04-04
If you do not like command line, you can use nautilus - file manager for copying, opening....files, directories...etc.

---

### Post by carlosqueso on 2006-04-04
[QUOTE=x5452]yeah i have read a lot of places to put things in /home... but where is home?  I thought it was like a 'tree type directory' but i cant find it[/QUOTE]

you actually don't want to put things in /home, but in /home/<your username>.  Since that's a royal pain, linux makes it easy for you.  You can get there by selecting Places->Home from gnome.  Terminals also open in the /home/<username> directory, identified by it's symbol ~. (it's like prince, represented by an unpronouncable symbol).  If you ever get lost and need to go back home, just type ```
cd
``` and you'll magicly teleport there.

---

### Post by x5452 on 2006-04-04
Hopeless Im stuck already...
I now have three files I copied to my ubuntu desktop, 80211g.zip, ndiswrapper-utils_1.1-4ubuntu2_i386.deb
and
ndisgtk_0.5-1ubuntu1_all.deb
Hope those are the right ones, but when i moved them to desktop they all got little gold colored lock icons on top of them??  what is that?  and when i double click the zip folder to extract, (extract in folder home) it says, extraction not performed, you dont have the right permissions to extract archives in the folder "/home"
There is a password box in the extract folder, i tried putting in the pass i made up when installing and nothing. 
I know you said not to put files in home, but in home/<my name> but when i clicked choose other, and went through home and clicked my name, it just says extract in home, doesnt say my name though so i guess its right.
But how do i unlock this stuff??

---

### Post by carlosqueso on 2006-04-04
You need to unlock it by going to where you put it in a terminal, and typing ```
sudo chmod 777 <name>
``` and your user password.  That should fix your permissions problems.

---

### Post by x5452 on 2006-04-04
first off , is there a way to abolish the passwords?  It unlocked when i did what you said, but then I moved the folder, it was the 80211g zip one, into a folder i made in home/name/drivers and now there is a lock on all the individual files inside?  

second heres what ive done, yes all case sensitive were adhered to :-) 
in my home directory i made a file drivers, i open terminal and type cd Drivers and it goes to scott@ubuntu:~/Drivers$ I then type sudo su ndiswrapper -i linksys.inf  (i renamed the file)  it then says, installing linksys, then says cp: cannot stat 'linksys.inf' : no such file or directory  i then retyped it, with just -i linksys, no .inf and it says linksys is already installed.  Use -e to remove it

so then I tried the sudo modprobe and it said command not found.  so i cd back to ~ and sudo modprobe and it said FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): operation not permitted
then i typed, from ~directory still, sudo ifup wlan0 and got 
ignoring unknown interface wlan0=wlan0.
and then i said bad words, had a cigarette, and came cryin to yall!  what did i mess up?

---

### Post by x5452 on 2006-04-04
alright I found another how to here and tried that but to no avail, 

0. Before you start, clear out any mess from existing failed attempts to use ndiswrapper. Note that you shouldn't use a root terminal to execute the code in this how-to; use a normal terminal session instead.
Code:

sudo modprobe -r bcmwl5 sudo rmmod ndiswrapper sudo apt-get remove ndiswrapper-utils sudo rm -r /etc/ndiswrapper/ sudo rm -r /etc/modprobe.d/ndiswrapper

Some of these steps may report errors; just ignore them.

1. Copy the bcmwl5.inf and bcmwl5.sys files to your desktop

2. Follow the advice given here under How to add extra repositories

3. Open a terminal session and enter this code. Note that you need an active network connection for this to work; I've assumed that if you have access to a wireless LAN, you also have access to a wired network as a fallback.
Code:

sudo apt-get install ndiswrapper-utils sudo ndiswrapper -i ~/Desktop/bcmwl5.inf sudo ndiswrapper -m for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile done

4. Reboot your PC. On restarting, the light on your wireless card should come on. If not, try entering

once i get to the for conffile part i start getting error, like syntax error near unknown sudo...  is there a better way than this?

---

### Post by x5452 on 2006-04-04
ok yippee, I finally got wireless up and going, thanks for all your help!!
a couple little questions left, first, is it going to configure automatically and be internet ready when shut down and booted up?  I entered in
sudo ndiswrapper -m and it told me modprobe config aready contains alias directive
second, is there a way to get an internet 'icon' for the sys tray so you can tell when it goes online and off?  not the io network icon up top, but an lan connection icon?
three, the files i have on my desktop, ndiswrapper.deb, ndisgtk.deb, 80211g zip, bcmwl4.inf and bcmwl5.sys, can i delete them from my desktop now, or do i have to save them?

and finally, wheres the best place to download the cool looking themes and desktops!!!  this brown background is killin me!!

Thanks again for all you help gettin me online, beers are on me  :mrgreen:

---

### Post by carlosqueso on 2006-04-04
sorry it took me so long to get back, I was at work last time I talked to you, and had stuff to do before I could get back.  I don't know about the lan connection icon, I don't use GNOME (the default ubuntu environment), but you could try right-clicking on the panel and choosing "add to panel".  There may be something useful in there (there is in XFCE, I checked).  

As for the files, the ndiswrapper and ndisgtk debs can go, as can the zip file, but if you used the inf and sys files on the desktop, those have to stay.

I like [http://art.gnome.org](http://art.gnome.org) for gnome themes if you don't like any of the ones in ubuntu.  Somewhere under the Actions->system menu is a theme thing, just drag your art.gnome.org themes/desktops/etc in there and you'll be all prettified.

If you need more help, just post up here, that's what us ubuntuites are for.  Welcome!

---

### Post by x5452 on 2006-04-04
the way i finally got it was by typing into the terminal 
 sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb
 sudo dpkg -i ndisgtk_0.5-1ubuntu1_all.deb
then i had a system>admin>windows wireless button i could click, followed through there and got it going.
I not sure if i ever used the other stuff lol. guess ill just hide the icons.
I did get the tray icon by right click> add to panel> add network monitor so thats cool. Trying to figure out how to install the latest firefox now, 
thanks for all your help!!

---

