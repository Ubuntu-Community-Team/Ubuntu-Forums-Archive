---
title: "ndiswrapper"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by voranado on 2008-02-03
I installed ndiswrapper and can get to it through a sudo command via the terminal.  However, it does not show up as "windows drivers" under system-administration.  In fact, the list under system-adminstration starts with keying manager: nothing before the letter k.

I am having trouble installing the driver using the sudo command and would like to try the graphical manager.  Any help appreciated.

Steve

---

### Post by jan quark on 2008-02-03
first what are your network device?

pls post the result of the following terminal commands

```
lspci
```

```
lshw -C network
```

---

### Post by spiderbatdad on 2008-02-03
checkout ndisgtk ( a graphical frontend for ndiswrapper in synaptic).

---

### Post by voranado on 2008-02-03
First, Ubuntu recognizes a linksis USB wireless device, but not a Belkin card.

Synaptic shows both ndswrapper common and ndswrapper utils 1.9 but not ndisgtk.

Thanks

---

### Post by spiderbatdad on 2008-02-03
what version are you using? if not 7.10 you need to enable repositories. If 7.10 you need to update your sources. ndisgtk is definitely there. I like to use the search tool in synaptic. It makes  it a lot easier to find things. Hint: click on the picture again after it opens to enlarge it further...a lot of people don't know that...they think it's a blurry picture.

---

### Post by anewguy on 2008-02-03
Well, I can tell you what I've done each time to make ndiswrapper work.  

(1) Clean out any known ndiswrapper drivers:

sudo ndiswrapper -l  <= lower case "L", stands for "List"

for each item, if any, returned above, do the following:

sudo ndiswrapper -r xxxx <= where xxxx is the name of a driver returned via the list command

Once all of that is back to a clean slate, then copy the Windows files needed for your driver (the .inf and .sys files) to your desktop.  Once there, do the following:

cd ~/Desktop

sudo ndiswrapper -i xxxx.inf <= where xxxx is the .inf file name

then:

sudo ndiswrapper -l  <= lower case "L" again - be sure your device/driver is listed

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m


At this point I would just reboot to make things easy.  After reboot:

sudo ndiswrapper -l <= lower case "L" again - to be sure ndiswrapper started at startup


Next, single left click on the network icon on the top tray (assuming Ubuntu and not kubuntu).  Select your wireless network, then if prompted enter in the network type, key, etc.

Any problems, just post back.:)

---

### Post by voranado on 2008-02-04
Thanks to all of you.  I am using version 7.10.  When I search for ndisgtk, it shows up under All in the left hand panel but not under packages on the right side.  I have not updated via the web after installation and assume that I need to do so.  

I still do not understand why only programs starting with the letter "k" and later show up under system-administration.

Steve

---

### Post by Partyboi2 on 2008-02-04
Have you got all the repo's enabled like spiderbatdad said?
to find out go to Software Sources (System>Admin>Software Sources) on the first tab tick all of them except source code then on the 3rd tab (updates) tick the boxes as well. then close. then open synaptic and try again. Another way after you have check Software Sources is to open a terminal (Applications>Accessories>Terminal) and type
```
sudo apt-get install ndisgtk
```

---

### Post by voranado on 2008-02-04
When I checked all the boxes, but got a pop-up that said could not find the packages.  WHen I ran the apt-get, the answer was that ndisgt could not be found.  I suspect I need to get on the web and do an update.  Thanks again to all.

---

### Post by emarkd on 2008-02-04
After you enabled all the extra repositories, did you reload their content?  Your computer keeps a local list of everything in the repositories and that's what it searches.  If you didn't, just click the Reload button the left and then try your search again.

And yes, you'll have to be online for any of this to work.

---

### Post by voranado on 2008-02-04
[QUOTE=emarkd;4266777]After you enabled all the extra repositories, did you reload their content?  Your computer keeps a local list of everything in the repositories and that's what it searches.  \

I did.  I will have to go online and try again.  Thanks.

---

### Post by dstew on 2008-02-04
> I suspect I need to get on the web and do an update.Yes, to update repositories and to use synaptic or apt-get, you need to be on the internet.

---

