---
title: "wireless help"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by jrandolph on 2007-03-05
First I want to say thanks to Taurus for all the help 
I am now having trouble getting my wireless connection to work after install
I am currently hardwired and have a Linksys wireless pci card, but it seems that it is not working

---

### Post by benfindlay on 2007-03-05
If you have your windows drivers for said card I would suggest installing ndiswrapper if you havent already done so. There's a guide at: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Hope this helps!

---

### Post by jrandolph on 2007-03-05
Is this only for a laptop wireless card or for desktop too?

---

### Post by benfindlay on 2007-03-05
It works for both. Ndiswrapper is simply a piece of software designed to get windows wifi drivers to work under linux. I use it with a netgear pcmcia card in my old PII dell latitude laptop!

---

### Post by jrandolph on 2007-03-05
I am really new to this, and I am not sure how to work most of this but I will give it a try.
Thank you for your help

---

### Post by benfindlay on 2007-03-05
Ok, then its probably best if I just post a list of things to type into a terminal for you!

Try the following:

1. Download the windows drivers onto your linux computer. I create a folder on my desktop for them usually

2. Launch Synaptic Package Manager (System>>Admininstration>>Synaptic Package Manager I think, might be System>>Preferences>>Synaptic Package Manager, use kubuntu myself) and search for ndiswrapper. It should display ndiswrapper-source, ndiswrapper-utils and ndisgtk. Install the lot!

3. Launch a terminal and go to the directory you copied your windows drivers to by typing:```
cd /home/[your user name]/Desktop/[name of folder you copied the files to]
```

4. Once of the files in the drivers directory is a .inf file, so you type:```
sudo ndiswrapper -i [filename].inf
``` Remember that ubuntu is case sensitive!!

5. Check its working ok, by typing ```
ndiswrapper -l
```If it is, it should tell you that driver and hardware are both present!

6. Now type ```
sudo ndiswrapper -m
``` this sorts out ndiswrapper for startup

7. Then ```
gksudo gedit /etc/modules
``` and add ```
ndiswrapper
``` to the end of the file!

8. Then```
sudo modprobe ndiswrapper
```this makes ubuntu load the drivers (I think)

Now you should be able to go into your Aplications>>Internet menu and there should be something called Windows Wireless Drivers (if its not there, try looking through your other menus. The ndisgtk package you installed earlier is a GUI interface for config of your wifi stuff.
If this doesn't work, try the following commands one after another:
```
iwconfig
ifconfig
iwconfig wlan0 essid <name of AP>
dhclient wlan0
```

Once this is all set up you need to go into System>>Administration?>>Network (Its either there or in preferences again!) and enable and configure your wireless device (dhcp or manual ip etc). Once its all done and activated you should be good to go (although a reboot may be required at some point first!)

Hope this helps!

---

### Post by benfindlay on 2007-03-05
By the way, for more info, go to [http://ubuntuguide.org/wiki/Dapper]("http://ubuntuguide.org/wiki/Dapper") and search for ndiswrapper!

---

### Post by jrandolph on 2007-03-06
I may be just dumb -- but I can get step 2 to work it tell me no such file or directory

---

### Post by benfindlay on 2007-03-06
Ok, instead of step 2, in terminal type ```
cd
```

This should put you in a directory containing Desktop and Examples and maybe other things. Typing ```
ls
``` will confirm this

In there type ```
cd Desktop
``` with **CAPITAL D!**

Then type ```
ls
``` again to see the directories and stuff on your desktop.

Then type ```
cd
``` followed the name of whatever directory you copied the files to, making sure to pay attention to exactly what is displayed when you typed ls in terminal before (as speces, capital letters etc all have their particular way of being handled by terminal!

Hope this helps

---

### Post by jrandolph on 2007-03-07
When I get to step 5 on the list above it says


Installed drivers:
file    invalid driver!
rt2500  invalid driver!
your_driver     invalid driver!

Can anyone tell me what to do now

---

### Post by benfindlay on 2007-03-07
Click System>>Administration>>Windows Wireless Drivers and remove all the ones that give you conflicts. If your hardware is listed there and is shown as present, tehn keep going, if not, click install new driver and browse for your relevant driver file (the *.inf I mentioned before)

Hope this helps

---

### Post by jrandolph on 2007-03-07
When I go to system and administration there is no option for windows wireless anything

---

### Post by benfindlay on 2007-03-07
did you install the ndisgtk package earlier?

---

### Post by jrandolph on 2007-03-07
I think i have done everything exactly as u have told me to

---

### Post by benfindlay on 2007-03-07
hmm thats very odd, all I can really suggest is that you launch a terminal and type ```
sudo apt-get install ndisgtk
```

When your system said this:

> Installed drivers:
file invalid driver!
rt2500 invalid driver!
your_driver invalid driver!

at least on mine, the invalid ones were due to typos when I first got it set up.

The other thing you could try is to start from scratch, and pay extra care to what you type in. For me I kept making mistakes because I put the files in folders that had spaces in the name and you need to treat them differently to normal folders in terminal, so I would suggest perhaps just copying the files onto your Desktop direct and trying once more!

Hope this helps!

---

### Post by jrandolph on 2007-03-07
ok i typed that into the terminal and now the windows wireless option is there 
so should i try to start over

---

### Post by benfindlay on 2007-03-07
if its there, then you should try adding your wireless drivers through the GUI, will probably be a lot less hassle that way!

---

### Post by jrandolph on 2007-03-07
This thing keeps telling me that the driver is invalid

---

### Post by jrandolph on 2007-03-07
Can anyone tell me why it keeps telling me that the driver is invalid?

---

### Post by benfindlay on 2007-03-08
could well be that the driver is in fact the wrong one for the card under linux. May be worth searching around for a more generic one. The reason I say this is because my wifi card is made by Netgear, its the MA521 pcmcia card, but it runs on the RTL8180 chipset. so I have to use the RTL818- drivers off realtek's website. The MA521 drivers that came with it actually don't work.

If you could post you exact model number, perhaps someone could tell you what driver they used to get it to work!

Hope this helps!

---

### Post by jrandolph on 2007-03-08
The wireless card I have is a Linksys WMP54G V4

---

