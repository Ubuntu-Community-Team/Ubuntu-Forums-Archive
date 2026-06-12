---
title: "BT Voyager 1055 in 7.04"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Raziel.ie on 2007-05-04
Hello guys.

Could someone please help me set up my BT Voyager 1055 to work in Ubuntu 7.04?

I followed this thread's tutorial on doing, but no dice 
[http://ubuntuforums.org/showthread.php?t=367448&highlight=BT+Voyager+1055](http://ubuntuforums.org/showthread.php?t=367448&highlight=BT+Voyager+1055) (Post Number 6)

A Step by Step guide would be nice.

Thanks for any help.

---

### Post by tyres on 2007-05-05
Hi,

Hopefully attached are the driver files you requested, plus my 99-custom.rules script.

They are in a gzip tar archive.

---

### Post by lordsword_8 on 2007-05-10
Ive followed both of these posts, but am having no headway. The ndiswrapper is reporting both hardware and driver as present, but i cant get online. How do i confirm its working and configure it with such stuff as my wep key?

Thanks, Mike

---

### Post by tyres on 2007-05-10
What's the output of the 'ifconfig' command?

The light on your adapter won't necessarily come on until you get your network configuration right, and it can associate with your router. 'ifconfig' may give some pointers towards that.

---

### Post by tyres on 2007-05-10
By the way, you might want to take a look at this post on how to set up the network with
WPA, which is much more secure than WEP, which can be broken trivially.

[http://ubuntuforums.org/showthread.php?t=202834&highlight=WPA+HowTo](http://ubuntuforums.org/showthread.php?t=202834&highlight=WPA+HowTo)

---

### Post by tyres on 2007-05-10
It's been a while since I used WEP, but looking back now you should be able to use the  
System/Administration/Network tool to configure your wireless connection with your network SSID and WEP key.

---

### Post by lordsword_8 on 2007-05-16
Sorry for the long delay, but its exam time for me. :mad: 

Ice still had no luck. iwconfig reports no wireless devices are installed and ifconfig only lists the loopbak device. I cant get you the exact output as im to much of a novice to be able to save a text file thats readable in windows!:) 

Thanks for the help, Miike

---

### Post by tyres on 2007-05-20
Sounds like maybe the devce (the BT1055 adapter) isn't being recognised as yet.

You say you followed the posts on this page to set up the BT1055 with ndiswrapper.

Did you set up the 99-custom.rules script in the /etc/udev/rules.d directory? If so, what values did you use in the script? You should use the values shown in the output of the 'lsusb' command (run in a terminal screen). Should show you something like '1690:0715'. That script (99-custom.rules) is necessary to get the BT1055 working, and needs the correct values from 'lsusb'. You could just use the 99-custome.rules script I posted in my message to Raziel.ie (a few messages back). 

If things are set up correctly, 'ifconfig' should show a 'wlan0' device, which is your BT1055 adapter.

---

### Post by tyres on 2007-05-20
By the way, to save the output of a command run in the terminal use the redirection arrow, like this;

'iwconfig > iwconfig.txt' (call the output file anything you want, of course). That will save the output of the 'iwconfig' command to a text file.

---

