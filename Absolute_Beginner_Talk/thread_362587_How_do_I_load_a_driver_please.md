---
title: "How do I load a driver please"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Ethelbert2 on 2007-02-15
[COLOR="DarkOliveGreen"][FONT="Georgia"][SIZE="3"]I have tried this question on the wireless forum and on the installation forum but no one will answer:no-one seems to want to help answer the basic questions. I will try here but I am beginning to understand why 95% of the world stays with Windows.

Anyway here goes again:


I have installed Ubuntu 6.10 on a P3 with 500MB RAM. I am experimenting iwth Linux to see how it goes. (Installation was OK except I had to use the text based installation choice as the window one froze).

Now I need help installing a driver, please.

It is for a wireless card. From the network manager it is listed with a Realtek chipset (rtl8185) but does not work. I was going to install NDIS wrapper and find a windows driver but, after ages trawling around, by chance I found an actuall Linux driver (!!) though hidden away on the Taiwan website of Realtek (I can give a link if anyone is interested.)

I had no idea how to do the wrapper anyway and a purpose made Linux driver would be better clearly - it says in the read me file that it runs with Debian 3.1 among other distributions. I assume that is OK for Ubuntu? 

So I used a WinXP computer to download the collection of files. The driver comes with various files including two files of commands, which help the installation, and instructions - but unfortunately I do not know how to use the instructions.

I can quote a bit of the readme file telling what is included:[/SIZE][/FONT][/COLOR]

[SIZE="1"][COLOR="Sienna"]The driver is composed of several parts:
(1)source code
r818x.tar.gz
stack.tar.gz

(2)Script ot build the modules
makedrv

(3)Script to load/unload modules
wlan0up
wlan0down

(4)Script and configuration for DHCP
wlan0dhcp
ifcfg-wlan0

(5)Supplicant source code
wpa_supplicant-0.3.8.tar.gz

(6)Example of supplicant configuration file
wpa1.conf
[/COLOR][/SIZE]
[SIZE="3"][FONT="Georgia"]This is fairly clear I suppose if you know Linux. It goes on to tell you what to do, but presupposes some confidence with Linux - but I am an utter beginner and there are unanswered questions which prevent me getting to first base.

It says:[/FONT][/SIZE]

[COLOR="Sienna"]< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:
[/COLOR]

[COLOR="DarkOliveGreen"][SIZE="3"][FONT="Georgia"]So that means some of it is taken care of. You just have to start the file. The makedrv file contains a sequence of instructions for example which I assume takes care of the proper sequence of commands. 

But the instructions only tell you to do this----[/FONT][/SIZE][/COLOR]

[COLOR="Sienna"](1)Build up the driver from the source code
**./makedrv**[/COLOR]

[FONT="Georgia"][COLOR="DarkOliveGreen"][SIZE="3"]But where and when do I enter this command? (In the command line window obviously but should I put all the files listed above in a particular place first (eg on a floppy)?
If I do, do I have to navigate to that directory (and how do I do that?)
Do I enter that command as it is or do I have to tailor it for my own circumstance (the appropriate directory etc?)

The instructions continue:----[/SIZE][/COLOR][/FONT]

[SIZE="1"][COLOR="Sienna"](2)Load the driver module to kernel and start up nic
**./wlan0up**
(if "insmod: error inserting 'r8180.ko': -File exists." met,
[B]./wlan0rmv
./wlan0down
./wlan0up[/B]
should be OK.
)
[/COLOR][/SIZE]
[COLOR="DarkOliveGreen"][SIZE="3"][FONT="Georgia"]
This seems clear but I am still unsure - again do I just enter **./wlan0rmv** or must I modify it somehow?
The bit in brackets is possibly OK but I am not sure I understand it fully - I guess it is to do with what happens if certain error messages are received).

PLease excuse me labouring the points and demanding what might seem excessive handholding but it is the little missing bits that are important here.

There is more (another three or so sections) but if I can get through these first two bits, the rest might be self-explanatory (though I might have to come back!)

I do appreciate it if anyone takes the trouble to answer. Thank you[/FONT][/SIZE][/COLOR]

---

### Post by tronica on 2007-02-15
i don't have any experience with ndiswrapper, but heres a guide i found searching the forums.


[http://ubuntuforums.org/showthread.php?t=361917&highlight=ndiswrapper]("http://ubuntuforums.org/showthread.php?t=361917&highlight=ndiswrapper")

---

### Post by dcstar on 2007-02-15
> **Ethelbert2 said:**
> 
........
(1)Build up the driver from the source code
**./makedrv**

But where and when do I enter this command? (In the command line window obviously but should I put all the files listed above in a particular place first (eg on a floppy)?
If I do, do I have to navigate to that directory (and how do I do that?)
Do I enter that command as it is or do I have to tailor it for my own circumstance (the appropriate directory etc?)
........

You will have "untar"ed the files provided into a particular directory.

In a terminal you have to **cd** to this directory, and then run the commands listed in the instructions.

---

### Post by Maestro23 on 2007-02-15
Some links to get your feet wet with Ubuntu.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

How to Install Anything: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Linux Commands/File Structure: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

*Also the link to the Ubuntu guide is in my sig.

Good luck.

---

### Post by Ethelbert2 on 2007-02-16
Thanks very much - somereading and experimenting to do.

---

