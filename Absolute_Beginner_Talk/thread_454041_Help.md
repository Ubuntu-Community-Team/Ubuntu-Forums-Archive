---
title: "Help"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by shadowsword232 on 2007-05-25
I have gotten Ubuntu up and running but I cannot get it to recognize my wireless card. If I can get it to recognize that then I can go from there on the rest of the drivers.  Intel Wireless WiFi Link 4965AGN is the card. I saw the hardware information page but I could not make heads or tales of it. If I have to run a command prompt please explain how to pull one up.

---

### Post by Kobalt on 2007-05-25
Go to Applications > Accessories > Terminal in order to access the command line. From there you just need to enter the commands as is... [Here]("https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty") is how to install your card.

---

### Post by DerArzt on 2007-05-25
Ok. You're card is a bit tricky but apparently is doable. First of all, there is not currently a native linux driver, but a number of other users from the forum got it working using the windows driver and a program called ndiswrapper. post 8 on 
[http://ubuntuforums.org/showthread.php?t=396204&highlight=4965AGN](http://ubuntuforums.org/showthread.php?t=396204&highlight=4965AGN)
is where im getting this all from.

First of all, you will need to open a terminal (go to applications--->accessories--->Terminal
once there type 

```
sudo apt-get install ndiswrapper-utils-1.9
```
you will be asked to enter your password. you wont see letters as you type, and that is normal

chances are that the ndiswrapper-utils-1.9 package will already be installed and it will tell you that if you read the output. if that is the case, thats fine


now open firefox and go to 
[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2753&OSFullName=Windows*+XP+Professional&lang=eng&strOSs=44&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2753&OSFullName=Windows*+XP+Professional&lang=eng&strOSs=44&submit=Go%21)

download the second driver you see (its called V11.1.0.0_XP_DRIVERS.ZIP)

now go to your desktop and extract the zip file (right click-->extract here)

ok, now go back to the terminal, or open a new one if you closed the first and change to the directory of the unzipped driver

do this by typing 

```
cd /home/$USER/Desktop/Drivers
``` 

now, in the same terminal type 
```
ndiswrapper -i NETw4x32.INF
```

next type
```
ndiswrapper -m
```

then
```
ndiswrapper -l
```
just check that the driver for your card is listed

lastly, type 

```
modprobe ndiswrapper
```


This next part i write is straight from post 8 on the before mentioned thread:

make sure that wireless is turned off when you exit/ enter ubuntu (fn + f2). If it remains on (wireless) then ubuntu can fail to boot or shutdown.

once in ubuntu, and having switched wireless the light should flash periodically (perhaps once every 5 seconds, this is normal behaiour).

after wireless has been turned on go to the network manager (nm-applet) and deselect then reselect enable networking to restart it (right-click). it should no become aware of the available wireless connections.

if your network manager shows no connections, check if any are available with the command;
sudo iwlist scan

Hope this works  Best of luck

---

### Post by DerArzt on 2007-05-25
lol, would have saved me some time to find that link above...oh well. it says the same stuff :)

---

### Post by shadowsword232 on 2007-05-27
I have been trying the method in the link, and everything goes ok until the sudo make command. When I get there it sends up a longs stream of errors. It does it again at make install and nothing after that works. Any advice?

---

