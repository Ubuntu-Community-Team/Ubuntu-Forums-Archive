---
title: "Total linux newb here..."
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by outdoenyou on 2007-02-11
Hey guys my names Brandon, i just installed the ubuntu desktop. Im a total newb when it comes to Linux. I just wanted to ask where a good place would be to start reading/learning how to use this OS? Id like to figure out how to install my WUSB54G driver. I cannot believe how much of an amateur i feel like when i use Linux, haha, i guess thats what happens when you've been using PC's loaded with microsoft since day one.


Thanks for the time, info, and help.

-Brandon

---

### Post by oilchangeguy on 2007-02-11
if you're wanting a book on ubuntu, try barnes and nobles, or borders website and search for ubuntu. and of course there's alot to be learned just by reading the forum. if you go the book route, i suggest ubuntu unleashed.

---

### Post by meng on 2007-02-11
Your question can be divided into 2:
1. Where to get general advice?
2. How to get your wireless set up?

Let's focus on #2 for the sake of expediency. [http://www.ubuntuforums.org/showthread.php?t=352163&highlight=wusb54g](http://www.ubuntuforums.org/showthread.php?t=352163&highlight=wusb54g)
and let us know how you go.

---

### Post by nickoli_02 on 2007-02-11
The only way to learn linux is to use linux :)
On the way you'll be forced to ask for help and read up on things and figure stuff out. That's what these forums are here for :) If you're serious about learning linux, try to resist the urge of going back to windows when something doesn't go quite right.

---

### Post by outdoenyou on 2007-02-11
awesome thanks guys, your pretty quick with the reply's, thats a good thing to know. 

1. Ill look into that book asap, thanks

2. [http://www.ubuntuforums.org/showthread.php?t=192588&highlight=wusb54g](http://www.ubuntuforums.org/showthread.php?t=192588&highlight=wusb54g)

should i follow those guidelines?

just keep in mind, i have not one clue what im doing with this OS, lol


:confused:

---

### Post by meng on 2007-02-11
At least start off by opening a terminal and typing
sudo iwconfig
and telling us what the response is.

---

### Post by outdoenyou on 2007-02-11
...how would one open a new terminal...

appoligies for my ignorance, please bare with me here....

---

### Post by Skidpad on 2007-02-11
Welcome aboard!  Here's one of many good reference sites for the beginners (like me!):

[http://www.ubuntuforums.org/showthread.php?t=142716]("http://www.ubuntuforums.org/showthread.php?t=142716")

---

### Post by meng on 2007-02-11
applications > accessories > terminal

---

### Post by Skidpad on 2007-02-11
> **outdoenyou said:**
> ...how would one open a new terminal...
appoligies for my ignorance, please bare with me here....
Applications>Accessories>Terminal

You can also add it to your "panel" at the top of the display, or to the desktop by right-clicking on it in the menu and selecting the appropriate option.  I have it on my panel - makes it a one-click affair to open the terminal.  :)

---

### Post by outdoenyou on 2007-02-11
brandon@brandon-desktop:~$
brandon@brandon-desktop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:""
          Mode:Managed  Frequency=2.412 GHz
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

brandon@brandon-desktop:~$

---

### Post by outdoenyou on 2007-02-11
is there a way to save text files in ubuntu so they open correctly in win xp?

(im running to computers on a network, the one im on now is windows xp pro - rj45, the other with ubuntu - wireless) 


so im running back and forth with a floppy (flash drive broke) trying to relay messages haha...

---

### Post by meng on 2007-02-11
sudo iwconfig rausb0 essid [insert your ESSID] key restricted [insert your WEP key in hexadecimal]

if you WEP key is alphanumeric, you need to type
sudo iwconfig rausb0 essid [insert your ESSID] key restricted s:[alphanumeric WEP key]
instead

then
sudo dhclient rausb0

that should get your wireless internet going

---

### Post by outdoenyou on 2007-02-12
do i type the  "[ ]" brackets or are the brackets not needed?

---

### Post by nickoli_02 on 2007-02-12
Nope, don't type the brackets in.

---

### Post by P235 on 2007-02-12
[http://www.linux.org/lessons/beginner/toc.html]("http://www.linux.org/lessons/beginner/toc.html")
[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")
[http://ubuntuforums.org/showthread.php?t=315404]("http://ubuntuforums.org/showthread.php?t=315404")

---

### Post by outdoenyou on 2007-02-13
great thanks guys.... it didnt work though.... i was reading this thread... 

[http://www.linuxquestions.org/hcl/showproduct.php?product=2590&cat=144](http://www.linuxquestions.org/hcl/showproduct.php?product=2590&cat=144)

think that will solve my problem, by downloading ndiswrapper?

---

