---
title: "Problem trying to install wireless network card, please help"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by stephen0205 on 2008-01-06
Hi there im not shure how to get my wireless card working. I am running Ubuntu 7.10 gutsy gibbon, in one of my old desktops, it has a belkin f5d700 wireless pci card, i read that it will work with ndiswrapper. The only problem is that i read how to install ndiswrapper and i didnt understand any of it. 

so if someone could give me a walk throught, i have no clue with ubuntu, just hate macs and am fed up with windows crashing. So ill write down what a need in a ist, might help u understand what im stuck with..

1. I have downloaded the ndiswrapper software, used ubuntu to unzipped ,

2. I dont know how to run it, the file gives me the option, display or run in termanal, or something like that. 

3. How would i install this ndiswrapper softwate, and how would i run it to work with my wireless card

If anyone can help please do, and thanks for takin the time to read and help a complete noob, i know its frustarating :)

---

### Post by (((X))) on 2008-01-06
or you can just install ndiswrapper via synaptic package manager

---

### Post by stephen0205 on 2008-01-06
could u tell me step by step how do do this.

thnaks

---

### Post by (((X))) on 2008-01-06
sure..
goto system>administration>synaptic package manager and search for ndiswrapper in there

---

### Post by stephen0205 on 2008-01-06
ok thanks, i have ndis rapper installed, and got my belkin drivers from the website. But i dont know what to do with them. Wont let me run the .exe, im nearly there , help me finish the job please.

---

### Post by Waderider on 2008-01-06
Hello Stephen, I'm only three or four days 'into' Ubuntu and actually did this job yesterday on the machine I'm posting from, with a F5D7000uk card.

I used this page and its links.... 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

......and it told me most of what I needed to know. The only other place I went for help was the Ndiswrapper project site itself.

HOWEVER, there are many different versions of the chip inside the F5D7000uk wireless card. Some work automatically with Gutsy Gibbon. Have you looked in system/administration/network and checked that the wireless connection isn't already available? I made that mistake, and spent ages learning how to install ndiswrapper!

---

### Post by stephen0205 on 2008-01-06
well thats helpful, i have the exaxt card, and it dosent show any netwoks or event he card itsself, i dont understand all this terminal code, could u help me throught it, maybe uninstall the card and make a small video posting on youtube, i know thats alot of hastle but it would really make it easier for me if i seen someone do it .

Thanks again

---

### Post by Waderider on 2008-01-06
Stephen, I think you'll need to start getting used to using terminal! I haven't found it too bad a learning curve (yet); the link to within this forum in my previous post really makes it quite easy. If you've installed Ndiswrapper follow the instructions from point 3.2.1 within the link above.

With regard to selecting what driver to use you'll find help on the Ndiswrapper web site.

---

### Post by stephen0205 on 2008-01-07
ok thanks anyway. I read that guide and now am more firmiluar with the terminal, however i cant get it working. 

In the terminal i type.

" lee@lee-desktop:~$ sudo ndiswrapper -i "

And then it shows this stuff

"install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
lee@lee-desktop:~$ "

So for the next part i typed in " sudo blkwgu.INF "

and i get, bad command.

Any ideas

---

### Post by stephen0205 on 2008-01-07
ok thanks read all that stuff, ised the terminal .

Had to get my original driver disk,

I created a folder in the home folder called drivers, and put all the files off the disk, ran ndiswrapper and installed the .inf file. Checked an installed correctly. 

Now i can see wireless networks but i cant connect to them, i select my speedtouch and insert the wep key, after a few trys to get it workin it keeps asking for the key, and it is correct, i have saved the key in notepad and have used it on all my compters so far.

Any change u can help me solve this small problem 2.

Thanks for the help, i really apreciate it.

---

### Post by Waderider on 2008-01-07
Stephen-

Good to hear you've got the driver working. As I didn't get the problem you're now suffering from I can't really help.

Can you (temporarily!) disable security on your network and then connect? At least that would *prove* that you are at the final step and the only issue is passing network security.

I had a quick look on the ndiswrapper site and saw this:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/)

---

