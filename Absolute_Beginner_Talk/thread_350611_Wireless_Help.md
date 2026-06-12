---
title: "Wireless Help"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-01-31
Hi,
   I'm running feisty with gnome. In Dapper (last version i used before feisty) in network tools there was a place to configure the wireless network SSID. In feisty there is no option to do this in network tools. I have looked through all the "network" type options in the gnome "System" and "administration" menus. Where can i configure the SSID in feisty?

(I have just gone back to school and require wireless.)

---

### Post by RomeReactor on 2007-01-31
I'm on Edgy, but this may work on Feisty: On a terminal type

```
sudo gedit /etc/network/interfaces
```

and look for "auto wlan0" (or your card's designation, "eth0", etc.). Provided Gedit didn't open a blank document (in which case the file doesn't exist on Feisty, or is somewhere else) below that type

```
wireless-essid NETGEAR
```

where NETGEAR is the essid of my router; change it accordingly. Save and reboot

---

### Post by ajmorris on 2007-01-31
thanks. I didn't even have my wireless device in that file. I added it and the essid, but still can't find the network.

---

### Post by RomeReactor on 2007-01-31
Did you install your wireless drivers with ndiswrapper? also, please post your interfaces file.

---

### Post by ajmorris on 2007-01-31
No i didn't install the drivers from ndiswrapper because in Dapper this card worked right away. Also the lights flash and the network devices picks up that there's a card in.


/etc/network/interfaces:


auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
inet ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid GGSWN

---

### Post by jimrz on 2007-01-31
> **ajmorris said:**
> No i didn't install the drivers from ndiswrapper because in Dapper this card worked right away. Also the lights flash and the network devices picks up that there's a card in.


/etc/network/interfaces:


auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
inet ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid GGSWN

looks like your card has an Atheros chipset. try putting your ESSID info in the "ath0" section rather than the "wlan" section

better still get network-manager + network-manager-gnome from synaptic, comment out all references except the "auto lo" section in "interfaces". then restart X and in the network manager applet which will appear in the panel choose "open a new network" and enter your ESSID info, then let NM do the rest

---

### Post by ajmorris on 2007-02-01
> **jimrz said:**
> looks like your card has an Atheros chipset. try putting your ESSID info in the "ath0" section rather than the "wlan" section

better still get network-manager + network-manager-gnome from synaptic, comment out all references except the "auto lo" section in "interfaces". then restart X and in the network manager applet which will appear in the panel choose "open a new network" and enter your ESSID info, then let NM do the rest

Thanks i will try the ath0 thing but i wont be able to download those till i get home tonight.

---

### Post by ajmorris on 2007-02-01
I tried the essid under ath0 but it was a no go. When i change the network settings to be ath0 instead of wlan0 it says ath0 is error to say there is nothing there. When wlan0 is selected it says disconnected so wlan0 is the right one. Also when i have network settings configured to use wlan0 then remove the wireless card (it's externel) it says it can't find: SIOCSIFFLAGS. 

Also when i do a sudo dhclient it also says that SIOCSIFFLAGS is missing and that wlan0 is disconnected. I have not managed to download those files from the repos yet as i cant do that till 9:10 when i get home.

---

### Post by bikeboy on 2007-02-01
Do you know what sort of card it is? Perhaps it's not an Atheros chipset but the ath0 is added to /etc/network/interfaces anyway.

I'll fire up my slightly older feisty cd to have a look at how it works.

---

### Post by ajmorris on 2007-02-01
> **bikeboy said:**
> Do you know what sort of card it is? Perhaps it's not an Atheros chipset but the ath0 is added to /etc/network/interfaces anyway.

I'll fire up my slightly older feisty cd to have a look at how it works.

It's is not an ahteros chip. It is a linksys wpc11.

---

### Post by chriscando on 2007-02-01
You might try using the program iwconfig. Its easy to set the essid from there
```
sudo iwconfig wlan0 essid your_essid
```
then just type iwconfig to verify that it was set. You can also set your wep key and channel if needed, then when you want to bring it up
```
sudo ifup wlan0
```
Hope this can help

---

### Post by bikeboy on 2007-02-01
Chriscando is right, iwconfig will let you configure all aspects of the card. If you're still in need of the GUI tool, in my feisty it's in System > Gnome Control Centre > System > Network. Unless they've changed it back to how it used to be between Jan 17 and today, you should be able to find it there. You can put in your WEP key if applicable via that GUI too.

---

### Post by ajmorris on 2007-02-02
> **chriscando said:**
> You might try using the program iwconfig. Its easy to set the essid from there
```
sudo iwconfig wlan0 essid your_essid
```
then just type iwconfig to verify that it was set. You can also set your wep key and channel if needed, then when you want to bring it up
```
sudo ifup wlan0
```
Hope this can help

Thanks for your reply but when i type "sudo iwconfig wlan0 essid GGSWN" it says "Error for wireless request "Set ESSID" (8B1A) SET failed on device wlan0 ; Operation not supported."

Any ideas? Maybe a fault in Feisty?

---

### Post by RomeReactor on 2007-02-02
run

```
iwconfig
```

in a terminal and see wich one of the cards listed has wireless extensions. You said before that "wlan0" wasn't in your file and that you put it in; i suggest deleting it, as i don't think that is your card's designation. Also you said that you ruled out "ath0" as your wireless; when you run iwconfig, look if the wireless extensions are on either "eth1" or "eth2"...

---

### Post by ajmorris on 2007-02-02
> **RomeReactor said:**
> run

```
iwconfig
```

in a terminal and see wich one of the cards listed has wireless extensions. You said before that "wlan0" wasn't in your file and that you put it in; i suggest deleting it, as i don't think that is your card's designation. Also you said that you ruled out "ath0" as your wireless; when you run iwconfig, look if the wireless extensions are on either "eth1" or "eth2"...

"iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions."


and i have now deleted the wlan0 line that i added. I am not at school now so i will have to try all the suggestions with a peer 2 peer network.

---

### Post by ajmorris on 2007-02-05
I have tried everything i can think (counting all the suggestions in these posts here.) And still no wireless.

The only other thing i can think of is ndiswrapper (which someone else suggested). I have it installed but no wireless drivers.  As far as i can tell there are none in the repos. Where can the wireless drivers be downloaded from?

---

### Post by RomeReactor on 2007-02-05
Go to the [NdisWrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page") page and check the list of supported cards; there are links there to the drivers (perhaps you can even use the windows drivers, if you have them).

---

### Post by ajmorris on 2007-02-05
> **RomeReactor said:**
> Go to the [NdisWrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page") page and check the list of supported cards; there are links there to the drivers (perhaps you can even use the windows drivers, if you have them).

Thanks. My linksys is supported. I will download the drivers tonight and see if that works.

( sorry about the slow responses of mine, i don't have much time to respond during the week)

---

### Post by ajmorris on 2007-02-06
> **RomeReactor said:**
> Go to the [NdisWrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page") page and check the list of supported cards; there are links there to the drivers (perhaps you can even use the windows drivers, if you have them).

Does ndiswrapper use .inf files? Because i do have the windowsXP drivers as well.

---

### Post by ajmorris on 2007-02-06
Don't worry everyone. Thanks for all your help. For some reason the wireless is now working, but did not work yesterday. The only thing i did differently is that i did not boot up with the wireless card plugged in. (It was not because the wireless was down as other people could access it when i couldn't)

Once again thankyou so much for all your help. :)

---

### Post by lquidfire on 2007-02-15
Allright, good to see I'm not the only one with this problem.

Please let me describe my problem and maybe then you can give me some help :)

I've a USR5416 card, works nicely in WinXP.
It worked as well under Ubuntu Edgy, and, I might be mistaken, but somehow I have in mind that it worked out of the box (so, w/o nidswrapper) for KUbuntu Edgy.

Now since I did a clean install of Feisty Herd 3, I can't get the network running, nor can I get it configured. Ndiswrapper is installed (newest version, 3.18 or so), configured it with usr11g.inf or so, gives as output driver running, device running. I can't give exact quotes, as I have to reboot into WinXP everytime I want to access the net...

A few remarks about things I've looked for / found already:

* System > Control Panel > Hardware / Devices: here the USR WiFi card is listed with it's correct name (even before installing ndiswrapper).

* System > Control Panel > Network: this GUI thing won't let me configure anything. It is put to something called roaming and won't stay on DHCP when I put it to it. Static address doesn't work, either.

* iwconfig gives a list like "eth0" etc and also "wlan0", but "no wireless extensions".

* dmesg | grep acx gives a couple of lines output, all seems to be OK (to me) but one thing: it says something about the device or driver (don't recall) is 32-bit, and this might conflict since I'm using a 64-bit architecture.

I conclude that somehow, even though recognizing the card, it doesn't talk to it correctly or so... Any suggestions on what to do? If you need some CLI-output posted, please let me know and I'll try and get it for you :) Oh, and thanks in advance!

---

### Post by ajmorris on 2007-02-15
For my problem i have to start with an old wireless card that uses eth1 then switch the cards over and use my card that uses wlan0. But since the old card was already in it uses eth1 for the newer one not wlan0.

---

### Post by lquidfire on 2007-02-16
Hm, thanks for the suggestion, but switching a PCI card isn't done in a sec. And btw, it worked a couple of weeks ago, before I did a clean install of Herd 3..

---

### Post by RomeReactor on 2007-02-16
lquidfire, since you're running Feisty 64-bit, you must use 64-bit drivers for your card as well; if you got the drivers you've used in edgy 32-bit from the cd that came with your card, look there. If not, look in the [NdisWrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page") page for your card's drivers; hopefully there should be at least one.

---

### Post by lquidfire on 2007-02-20
Ahh, thanks a lot, that did solve a problem already!

Now the wcard sees other networks, but I can't log in to my own. In the GUI, the bars aren't filled with a green thing showing the strength of the signal..
In the terminal when I type iwconfig it gives the correct settings I'd say, still it won't connect me to the internet. The GUI thing tries to connect but somewhere fails with a password problem I suppose (although it doesn't give me an error-message).

* How do I reset all the (wireless) network settings?
* It is a managed network, open password, 128-bit ascii WEP key. Don't I enter that like

sudo iwconfig essid essidgoeshere
sudo iwconfig managed
sudo iwconfig key s: passwordgoeshere [without the space s: and the pass, but on this forum that gives a funny smiley and a nasty word :P]
sudo iwconfig key open

Is there a special way to enter the fact that it is a 128bit WEP encryption? And why doesn't it work while in KUbuntu (which in general I don't like so much) it almost worked out of the box? :(

Anyway, thanks for your suggestions and help! :)

---

### Post by RomeReactor on 2007-02-20
You forgot to tell iwconfig which interface to apply those settings to. If your wireless card is **wlan0**, then

```
sudo iwconfig wlan0 essid YOUR_ESSID

sudo iwconfig wlan0 mode Managed

sudo iwconfig wlan0 key YOUR_KEY_HERE
```

Change your card's designation if it's different (ath0, eth1, etc). If issued iwconfig commands don't seem to stick, try editing the interfaces file by hand:

```
gksudo gedit /etc/network/interfaces
```

Look for your card's entry (it should say something like **iface wlan0 inet static** or **iface wlan0 inet dhcp**, if it's wlan0), and see if the following text is below it. It should look something like this:

```
iface wlan0 inet dhcp
wireless-essid YOUR_ESSID
wireless-mode managed
wireless-key YOUR_KEY_HERE
```

If the text is not there, add it, save and reboot.

---

### Post by lquidfire on 2007-02-23
Thanks a lot, I'll try!

Is it possible the radio function isn't working? Downloaded Ubuntu Herd 4 CD, live CD won't connect me to the network, either. Using the GUI (beside the time and date, top of the screen), I click the correct Essid. It asks for key, I click 128-bit WEP, ascii mode, enter the key. Takes some time, but in the end it doesn't connect. When hovering the mouse over the network-icon it says something like "Waiting for key for network ***". Any indication what goes wrong?

With a Feisty KUbuntu live CD environment I enter the key and it works. I don't really feel like installing KUbuntu, deleting KDE etc and installing Gnome.

---

