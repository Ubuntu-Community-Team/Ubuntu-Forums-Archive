---
title: "WiFi Network Help (How to Troubleshoot)"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-10-17
Hi,

I have Ubuntu installed with a D-Link DWL-650+ wifi card (laptop).  This wifi card worked when I first plugged it in.  

However, occassionally, I would come across a network in my travels that I could connect to successfully for a time, and then, maybe after a restart or something, would no longer be able to connect to it EVER again afterward.  [I asked around about this]("http://www.ubuntuforums.org/showthread.php?t=246821"), tried to troubleshoot it myself through every means (which are little) I could come up with, and finally took the recommendation to try using wifi-radar ...

Well, I went and installed it here at home and went ahead to play around it.  Just my luck!  Now the one network that has ALWAYS worked won't work anymore!

Even after a restart and only using the "Network Settings" panel from the System applications I can't get my home network to work anymore.   The only symptom I can describe is that it stalls out ... I think it can't establish a connection or IP address but I am not sure.

It is frustrating because I have been using the same network for months ... and now it won't work!

Help?

---

### Post by thornomad on 2006-10-17
Well -- I managed to get it to work again ... but I had to go into my router and release the IPs / MAC addresses ... seems to be something with Ubuntu not reseting or working with the IP correctly ... not sure what I did to fix it.  

What are the steps I should take in the terminal to:

[LIST=1]
[*]view my wireless settings / connectiono
[*]reset my wireless connection
[*]set the WEP password and whatnot
[/LIST]

Thanks,
Damon

---

### Post by jimrz on 2006-10-17
> **thornomad said:**
> Well -- I managed to get it to work again ... but I had to go into my router and release the IPs / MAC addresses ... seems to be something with Ubuntu not reseting or working with the IP correctly ... not sure what I did to fix it.  

What are the steps I should take in the terminal to:

[LIST=1]
[*]view my wireless settings / connectiono
[*]reset my wireless connection
[*]set the WEP password and whatnot
[/LIST]

Thanks,
Damon

are you using Gnome? 

if so,try installing network-manager and network-manager-gnome (gui frontend for network-manager) from Synaptic. if you elect to try this, after install you will need to go to Ternial and do: 
```
sudo cp /etc/network/interfaces /etc/network/interfaces-original
```
always backup critical files
then:
```
sudo gedit /etc/network/interfaces
```

comment out all of the references to your wireless and wired devices, leaving only "auto lo" uncommented. this will allow network-manager to see your devices. restart your comp and you should see the network-manager icon in your panel (you may also see your original icon, showing only lo, which you can remove from panel after confirming that nm is working). click on the network-manager icon and it will open up and you can enter your info to connect to your ap.

---

### Post by thornomad on 2006-10-18
Hi - thanks for that!  Where I am now, though, I can't get on the internet on the Linux side (windows works) so I can't download the new software.  I did look at my /etc/network/interfaces and played around with "reseting" it (commenting everything out) and rebooting, but with no luck.

On windows side, I simply "Configured" network by typing in Network name "RLB" ... that is all.  There is no WEP security, DHCP is automatic ... now: this worked, once, in Ubuntu, but I can't get it to work again.

What should my wlan0 setting look like in this case ?  Any way to troubleshoot why it times out when looking for an IP address on the Ubuntu side but no problem on Windows ?

D

---

### Post by jimrz on 2006-10-18
> **thornomad said:**
> Hi - thanks for that!  Where I am now, though, I can't get on the internet on the Linux side (windows works) so I can't download the new software.  I did look at my /etc/network/interfaces and played around with "reseting" it (commenting everything out) and rebooting, but with no luck.

On windows side, I simply "Configured" network by typing in Network name "RLB" ... that is all.  There is no WEP security, DHCP is automatic ... now: this worked, once, in Ubuntu, but I can't get it to work again.

What should my wlan0 setting look like in this case ?  Any way to troubleshoot why it times out when looking for an IP address on the Ubuntu side but no problem on Windows ?

D

if you have the "alternate" install cd, network manager and it's gui or on it and can be installed via Synaptic using the cd -OR- if not, you could go to [[COLOR="Sienna"]**_this_**[/COLOR]]("http://packages.ubuntu.com/dapper/net/") site using windows and d/l the .deb's for both network-manager + network-manager-gnome, transfer them to your ubuntu desktop and install by double clicking (do network-manager 1st the the gui).

the first method would be preferable. it is possible the second could leave you with a dependency issue but, if so, it would likely be easily resolved.

---

### Post by thornomad on 2006-10-19
**[I posted this question in a new topic since it is off-topic here]("http://www.ubuntuforums.org/showthread.php?p=1635792#post1635792")**

Hey Jimrz,

So I got the internet to work on the original connection and installed "network-manager" and "network-manager-gnome".  Then I commented out the /etc/network/interfaces file leaving only the auto lo instructions.

Now: where do I find network-manager GUI after the restart ?  Am looking for it but don't see it anywhere on my desktop.

Am I being silly?

D

---

### Post by jimrz on 2006-10-19
> **thornomad said:**
> **[I posted this question in a new topic since it is off-topic here]("http://www.ubuntuforums.org/showthread.php?p=1635792#post1635792")**

Hey Jimrz,

So I got the internet to work on the original connection and installed "network-manager" and "network-manager-gnome".  Then I commented out the /etc/network/interfaces file leaving only the auto lo instructions.

Now: where do I find network-manager GUI after the restart ?  Am looking for it but don't see it anywhere on my desktop.

Am I being silly?

D

the gui is called nm-applet and should have been added to your startup menu on install. the icon is either the standard 2 liitle terminals for either wired or no connection (lo) or bars (like signal strength on your cell phone) for wireless or 2 dots w/ circling arrows when searching for wireless connect. this should be on yor top panel on the left near the clock and volume icons. if not there, go to System > Preferences > Sessions > the Startup programs tab and check to make sure it is listed. if not, add it. mine looks like this ```
nm-applet --sm-disable
```
after you get it on the panel, just click it and enter what you need (essid/key/whatever)

---

### Post by Dual Cortex on 2006-10-19
Warning: This is a noobish asnwer

I was having problems connecting to my home network, encrypted using a weak 64 bit key :P
Anyway I was able to fix the problem by deleting the list of DNS Servers when you go to System>ADministration>Networking>DNS.
I assumed this list automatically changed itself when connecting to a network and automatically obtaining an IP Address (DHCP) but I noticed that it seemed to be using an IP of another router from a different unsecured network I had used before.

Finally, after many hours of despair I was able to get it work and I'm now happily browsing and downloading crap at comcastic speeds.

---

### Post by thornomad on 2006-10-20
> **jimrz said:**
> the gui is called nm-applet and should have been added to your startup menu on install. the icon is either the standard 2 liitle terminals for either wired or no connection (lo) or bars (like signal strength on your cell phone) for wireless or 2 dots w/ circling arrows when searching for wireless connect. this should be on yor top panel on the left near the clock and volume icons. if not there, go to System > Preferences > Sessions > the Startup programs tab and check to make sure it is listed.

I am including a screen shot because I do have the start Programs listed correctly (it seems to be) but I do not see any icon.  If I go to the panel, select: Add To Panel, and then browse around, the closest I can find is "Network Monitor" ... but its configuration only takes me to the System/Administration/Networking and network-manager, I think, should be something different.

Take a look at the screen shot and see what you think.

> **Dual Cortex said:**
> I was having problems connecting to my home network, encrypted using a weak 64 bit key :P
Anyway I was able to fix the problem by deleting the list of DNS Servers when you go to System>ADministration>Networking>DNS.
I assumed this list automatically changed itself when connecting to a network and automatically obtaining an IP Address (DHCP) but I noticed that it seemed to be using an IP of another router from a different unsecured network I had used before.

I had tried erasing those in the past -- I noticed they hung around as well.  I also completely trashed the /etc/networks/interfaces/ and started from scratch (as jimrz recommended) ... still no luck.

Where is my network manager!?  Smile.  Thanks!

---

