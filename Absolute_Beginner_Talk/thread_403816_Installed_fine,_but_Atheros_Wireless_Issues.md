---
title: "Installed fine, but Atheros Wireless Issues"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by garius on 2007-04-07
I've resisted posting this as long as possible, as i don't like to waste people's time if a solution exists elsewhere on the Net (or on this forum) but i have to admit that i'm stuck.

Basically the hard-drive died on my laptop the other day so i figured (after buying a replacement) that this was a good time to risk dual-booting again.

I've set up a new partition, and installed Ubuntu. All seems to have gone fine and most things i've been able to configure (still got to attack the graphics drivers but we'll cross that bridge when it comes to it :) ) **but** (There's always a but) the one which i just can't, for the life of me, get to work is...

...my wireless card.

The card itself is AR5211 Atheros (a+b) and just doesn't seem to quite work. Now on reading here and elsewhere i've come across other references to Atheros cards and possible solutions but none seemed to work.

Currently the situation is this:

I've used ndiswrapper to use the windows drivers and that seems to work fine - i get the appropriate message that the driver is installed and the hardware is there, and after installing wifiradar i can even see that its picking up the card and is using it to look for networks. I can even see my network (which i've disabled WEP on, is broadcasting on b+g, channel 11), yet every time i try and connect it reports that its unable to acquire an ip. I've even tried to manually allocate one but had no luck.

Finally, i've also tried to configure it all through the terminal following the instructions here and elsewhere, yet whenever i try to manually set mode, key, etc. via wsconfig i receive a:

"SET failed n device ath0 ; operation not permitted."

or equivalent error.

So i bow to you, the experts. Any ideas people? Am happy to post further info/actions as required because, as i say, frankly its got me beat and if i can't resolve this, then there's little point me carrying on with putting Ubuntu on here - something i'd be very disappointed about because i'm keen to sample its features. etc.

- G

---

### Post by xenblend on 2007-04-07
you seem to have the correct module being loaded.  Did you remove any ath_* modules that may have been automatically loaded?  ath_pci, etc.  Type 'lspci | sort' to get a list of modules.  Remove them all, there are 3 or 4 of them usually.  Obviously it sounds like you're getting ndiswrapper loaded or else you wouldn't be able to scan networks.

then type 'iwconfig [interface] essid [SSID] key [Open/Restricted] [WEP KEY]'

for example: 'iwconfig eth1 essid MySSID key open abcdef1234'

a couple hints: ifconfig -a will give you the correct interface name, 'restricted' means the same as 'shared' is most often used to describe the security protocols.

Now, if you use a DHCP server, you should be able to type 'dhclient [interface]' ie dhclient eth1 and get connected.  If you use a manual configuration, I recommend using KControl's 'network settings' tab as it has most often worked for me in the past.

Good luck with it, I've got the same exact card and it got up and running for me with very little trouble.

xb

---

### Post by LaurelLynn on 2007-04-07
Dear garius,

If your able to search for and find wireless networks the cards drivers are probably fine.

It sounds to me like a configuration problem with the wireless router.  These days most routers actually  run Linux servers with Firewalls and DCHP servers for addresses.  The firewall can drop you completely if set improperly.  The DCHP server might not accept a static IP address that falls within its address range.

I would check your routers documentation for instructions on how to check its configuration (usually only allowed by a direct cable connection through your web browser).  You can have both the cable and the wireless controllers connect to the router at the same time. The router usually has a ping option somewhere to test the connection.

Laurel Lynn

---

### Post by psycosmyth on 2007-04-07
I take it you had no problems with this with the last install?
Are you using Fiesty? Some folks are having issues with Atheros cards that did'nt before, including myself, I went back to Edgy. You may have to install Madwifi from scratch. Just use the Debian method, it works pretty well.

---

### Post by garius on 2007-04-07
> I take it you had no problems with this with the last install?
Are you using Fiesty? Some folks are having issues with Atheros cards that did'nt before, including myself, I went back to Edgy. You may have to install Madwifi from scratch. Just use the Debian method, it works pretty well.

I believe i'm using "edgy" - 6.10. I figured it was best to go with the release advertised on the main ubuntu page in order to avoid potential nastiness. I haven't so much as glanced at any Linux at all since Red Hat 6, and even then only briefly, so i wanted to play safe and go full-on "newbie."

> you seem to have the correct module being loaded. Did you remove any ath_* modules that may have been automatically loaded? ath_pci, etc. Type 'lspci | sort' to get a list of modules. Remove them all, there are 3 or 4 of them usually. Obviously it sounds like you're getting ndiswrapper loaded or else you wouldn't be able to scan networks.

To be frank i'm not sure what i should be looking for (i.e. what should be springing alarm bells and what shouldn't) - i get a bunch of controllers for firewire, my graphics card, normal ethernet card, usb and one reference for the Atheros card. Is that correct?

> then type 'iwconfig [interface] essid [SSID] key [Open/Restricted] [WEP KEY]'

This always results in:

Error for wireless request "Set ESSID" (8BIA) : 
SET failed on device ath0 ; Operation not permitted.

> If your able to search for and find wireless networks the cards drivers are probably fine.

See this was what the little grey cells were telling me too, but i've disabled wep, manually set a channel (so i can be sure the linux laptop is using the same one) and checked its doing nothing funky with firewall inbound/outbound rules and it isn't (at least as far as i can tell). I've also checked the activity monitor to make sure that the Linux lappy isn't being allocated an IP but just not realising it, and it isn't.

Currently it looks like half the south coast of england is connected to my router. just not me :D

(Ii've currently got the missus' laptop logged into the router admin and sitting next to mine. Handy for me, but its getting me some evil looks as its interrupting her solitaire session).

---

### Post by garius on 2007-04-07
Oh, my router is a Netgear DG834G if that helps.

---

### Post by garius on 2007-04-08
right, i'm going to do a completely clean install this morning to see if that helps any, but if not its not looking good for ubuntu :(

---

### Post by Famicommie on 2007-04-08
First: does wifiradar detect any other networks in your area? I had a nasty problem setting up my wireless card simply because my router was on the same channel as my neighbor's! So, as a possible troubleshooting step, I recommend changing the channel that the router is using.

Secondly, I had a lot of problems using programs like wifiradar and the gnome-network-applet. They simply wouldn't allow me to properly connect. Uninstall those programs and try getting everything set up from the terminal.

Finally, whenever you get a "permission denied" error from the terminal, hit the 'up' key on the directional pad, move the cursor to the beginning of the command, and insert the word sudo. Sudo allows you to perform commands as though you were the root user.

Hope that helps.

---

### Post by r00tintheb0x on 2007-04-08
garius

You can NDISWrapper it or rip the code from the windows drivers.

---

### Post by garius on 2007-04-08
> First: does wifiradar detect any other networks in your area? I had a nasty problem setting up my wireless card simply because my router was on the same channel as my neighbor's! So, as a possible troubleshooting step, I recommend changing the channel that the router is using.

It does indeed - i've not had any problems with the windows box, but thas not to say i won't here. As soon as this has all reinstalled i'll give that a go

> Secondly, I had a lot of problems using programs like wifiradar and the gnome-network-applet. They simply wouldn't allow me to properly connect. Uninstall those programs and try getting everything set up from the terminal.

Cool - will do. Will feed back with results

> Finally, whenever you get a "permission denied" error from the terminal, hit the 'up' key on the directional pad, move the cursor to the beginning of the command, and insert the word sudo. Sudo allows you to perform commands as though you were the root user.

Brilliant - thanks, didn't know that, again i'll give it a go on this fresh install.

> You can NDISWrapper it or rip the code from the windows drivers.

This is what i was doing and it seemed to be working fine apart from the teensy-weensy flaw that is the inability to actually connect to anything :D

---

### Post by Famicommie on 2007-04-08
Another important thing to keep in mind is that Ubuntu comes with drivers for a lot of wifi devices, and if you don't disable those drivers then they might conflict with ndiswrapper and prevent it from working. The quick and easy way if I remember properly is:

```
echo 'blacklist ath_pci' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist ath_hal' | sudo tee -a /etc/modprobe.d/blacklist
```

You will have to restart the computer before those changes take effect, though.

---

### Post by garius on 2007-04-08
okay, i've formatted and installed 7.04.

this is the order of events so far

1) GOOD NEWS: I now have no wrappers on there, nuttin' - just using the drivers that Ubuntu picked up on install. "Atheros Hardware Access Layer" is listed as a "restricted driver" but seems to work anyway.

2) These seem to work, and now, looking in iwconfig i get ath0 as the only wireless device. using **famicommie's** sudo method it will now let me configure the settings via the terminal - but i am checking in the NM applet first to see if its actually picking up anything

3) Looking in the NetworkManager Applet 0.6.4 at the top right, i can see that it is detecting the presence of my network - so i know the card is working.

4) sudo iwconfig ath0 essid [networkname] works.

5) the connection type has changed from IEEE 802.11a to b which is correct.

6) sudo iwconfig ath0 channel 11 seems to work. This is the new channel i have set the router to.

7) frequency now reads "2.442 GHz" and "Link Quality=0/94" that last bit seems ominous...

8) BAD NEWS. As expected - still no internet connection.

9) changing to channel 02 on router and laptop just in case. Still no link quality, frequency doesn't seem to change.

10) pinging both router and google via IP results in "network is unreachable"

Any idea what i'm missing? :(

---

### Post by Famicommie on 2007-04-08
Okay, you're almost there!

Open a terminal and enter the command "iwconfig". It should display everything related to your network connection. What we want to see is if the signal has a higher number than the noise level (remember that they are measured in the negatives, so the signal must have a smaller number attached to the negative sign than the noise level). If you have too much noise, try to position yourself closer to the router and run iwconfig again. If that seems fine, input the command "sudo dhclient". Hopefully, it will work once you've run dhclient.

---

### Post by garius on 2007-04-08
> Open a terminal and enter the command "iwconfig". It should display everything related to your network connection. What we want to see is if the signal has a higher number than the noise level (remember that they are measured in the negatives, so the signal must have a smaller number attached to the negative sign than the noise level). If you have too much noise, try to position yourself closer to the router and run iwconfig again.

all good so far:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:"brightonhouse"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:31 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/94  Signal level=-55 dBm  Noise level=-98 dBm
          Rx invalid nwid:1  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

but sudo dhclient gets me:

```
There is already a pid file /var/run/dhclient.pid with pid 5506
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/ath0/00:01:24:70:1d:08
Sending on   LPF/ath0/00:01:24:70:1d:08
Listening on LPF/eth0/00:90:f5:1e:63:46
Sending on   LPF/eth0/00:90:f5:1e:63:46
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

So presumably this is a DHCP issue?

I've got the wired network running fine btw - its just this wireless issue thats causing me grief now - that and my inability to get a resolution above 1024x768 with my Mobility Radeon 9000 - but i'm saving that for another thread :D

---

### Post by garius on 2007-04-08
wey! got my resolution issues sorted, so this is the last big issue to sort (at least for now).

I've been googling for DHCP suggestions but haven't met with much luck. Anyone have any ideas?

---

### Post by xenblend on 2007-04-08
I'm not finding any new responses so I hope that means you've gotten it working.  Let me know if the linux drivers work for you, as I'm using ndiswrapper (windows drivers) and I wonder if the linux ones would be more tweakable.  Just hit 'lsmod | sort' and tell me which modules start with ath*.

Oh yea and if you want to change it so that instead of "ath0" your wifi card shows up as "wlan0" or "eth1" etc. you can edit the "/etc/iftabs" file.  Thats what I did.

---

### Post by garius on 2007-04-08
nope - still an issue.

the linux ones are the ones i'm definitely using now as you're right - if they're there, then they should really be used.

---

### Post by Famicommie on 2007-04-08
You still aren't connected to your router. See where it says "Access Point: Not-Assiociated"?

First thing you should do is verify your ESSID. Make certain that you have capitalizations/spelling all correct. If that doesn't work, then you have a number of options.

If you go to the manufacturer's website, they may have downloadable linux driver sources available. Using the company's official drivers might help a lot, but it'll force you to learn how to compile and fetch dependencies. In short, it's a pain. In long, you'll have to download the tar.gz file, open up a terminal/navigate to the directory where the tar.gz file is saved, enter "tar xvf <driver>.tar.gz", naviate into the <driver> directory that's made, run the command "./configure" and download package from synaptic based on errors given from "./configure", and when "./configure" finally runs properly, run the commands "sudo make" and "sudo make install". It's easier than it sounds, but getting the required dependencies from synaptic is not my idea of a well-spent Easter sunday.

Another option would be to google and see if older versions of madwifi work properly with your card. For that you will have to uninstall the madwifi drivers from synaptic, grab a snapshot of the old madwifi source code, and compile it by going through the procedure outlined above.

Now, my atheros card isn't supported by any release of madwifi, nor would ndiswrapper from the repositories work with it, so I had to uninstall ndiswrapper and compile it from source. [There is an excellent guide on how to do that featured from steps 11-14 here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). Unfortunately, every time there is a kernel update, I have to recompile ndiswrapper as the updates break my wireless.

I sincerely hope that you can get the card working by simply changing the ESSID or running the drivers from the installed version of ndiswrapper. But if you can't, well, be prepared to learn a lot about how things work in linux :D

---

### Post by garius on 2007-04-08
okay, well i've double-checked that the essid is correct so no issue there. Looking around, all driver references on the manufacturer site point to madwifi (the card is the AR5211 for reference).

There are some references [here]("http://madwifi.org/wiki/UserDocs/MiniPCI") to a "radio issue" preventing access point association with some cards that can possibility be fixed by putting:

```
modprobe ath_pci rfkill=0
```

somewhere relevant but i'm not sure whether they apply here.

I suppose a good starting point would be to try using ndiswrapper again now that its a clean install. I can do that, but i'm not sure how i go about ensuring that the *current* drivers are deactivated properly. Any guidance there would be appreciated.

Once that has either succeeded or failed i suppose i'll need to think about the other options you suggested. As they say, life is just one big long learning experience...

---

### Post by LaurelLynn on 2007-04-08
Dear garius,

The signal is stronger than the noise, but might still be a bit weak for a stable connection.   If you haven´t done so yet and if  possible, try to connect with the Access Point within arms length of the computer.  That then rules out all signal strength problems.  When I´m sure it works at that range, then I move them apart and deal with any problems that occur at a distance.

Laurel Lynn

---

### Post by garius on 2007-04-08
okay, i've just done the following:

```
echo 'blacklist ath_pci' | sudo tee -a /etc/modprobe.d/blacklist
Password:
blacklist ath_pci
echo 'blacklist ath_hal' | sudo tee -a /etc/modprobe.d/blacklist
blacklist ath_hal
sudo ndiswrapper -i ~/Desktop/em9ab.inf
installing em9ab ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
ndiswrapper -l
em9ab : driver installed
        device (168C:0012) present (alternate driver: ath_pci)
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

```

still no luck - iwconfig looks exactly the same and its still gets the same dhcp issue.

Assuming you don't think i've done anything wrong above, then i guess i need to be thinking about trying this the hard way...

---

### Post by garius on 2007-04-08
> The signal is stronger than the noise, but might still be a bit weak for a stable connection. If you haven´t done so yet and if possible, try to connect with the Access Point within arms length of the computer. That then rules out all signal strength problems. When I´m sure it works at that range, then I move them apart and deal with any problems that occur at a distance.

Yeah - all this is taking place within two feet of the router - which means i should be getting stupid-strength. I certainly did when this was a windows machine.

Anyway, bed time for me over here in dear old blighty - the missus is summoning me to bed to help her with *Phoenix Wright* (and who says romance is dead...)

Its a four day weekend here though, so any advice on how to go about things the hard way would be appreciated as i'll be looking to have a go tomorrow.

---

### Post by Famicommie on 2007-04-08
I still haven't picked up Phoenix Wright, though I hear a lot of good things about it. Probably because even a year later I still play Trauma Center like crazy, and my PSP keeps me occupied and prevents me from buying DS games. Portable Metal Gear Solid: you can't go wrong XD

Compiling programs isn't *too* hard, and the knowledge is invaluable as you start becoming more competent with Linux and develop esoteric needs not covered by repositories. Just repeat the mantra:

tar xvf <package_name.tar.gz>
cd <directory_created_by_untarring>
./configure
*<step_where_you_download_packages_from_the_repository_when_./configure_can't_find_them>
sudo make
sudo make install

*note: sometimes ./configure will still report missing dependencies even after you've installed them. That's because it's looking for the dev files. When you do the synaptic search for <package_name> ensure that you installed the <package_name-dev> files, too.

That ndiswrapper URL I pointed you to earlier is rad at explaining the whole process necessary for compiling the latest version.

---

### Post by zekus on 2007-04-10
I'm sorry to say that your problem is the Netgear DG834G. I cannot associate with 2 of that pieces of s*+t. 
No problems with other Access Points ( ex. linksys )

bye

---

### Post by stchman on 2007-04-10
> **garius said:**
> I've resisted posting this as long as possible, as i don't like to waste people's time if a solution exists elsewhere on the Net (or on this forum) but i have to admit that i'm stuck.

Basically the hard-drive died on my laptop the other day so i figured (after buying a replacement) that this was a good time to risk dual-booting again.

I've set up a new partition, and installed Ubuntu. All seems to have gone fine and most things i've been able to configure (still got to attack the graphics drivers but we'll cross that bridge when it comes to it :) ) **but** (There's always a but) the one which i just can't, for the life of me, get to work is...

...my wireless card.

The card itself is AR5211 Atheros (a+b) and just doesn't seem to quite work. Now on reading here and elsewhere i've come across other references to Atheros cards and possible solutions but none seemed to work.

Currently the situation is this:

I've used ndiswrapper to use the windows drivers and that seems to work fine - i get the appropriate message that the driver is installed and the hardware is there, and after installing wifiradar i can even see that its picking up the card and is using it to look for networks. I can even see my network (which i've disabled WEP on, is broadcasting on b+g, channel 11), yet every time i try and connect it reports that its unable to acquire an ip. I've even tried to manually allocate one but had no luck.

Finally, i've also tried to configure it all through the terminal following the instructions here and elsewhere, yet whenever i try to manually set mode, key, etc. via wsconfig i receive a:

"SET failed n device ath0 ; operation not permitted."

or equivalent error.

So i bow to you, the experts. Any ideas people? Am happy to post further info/actions as required because, as i say, frankly its got me beat and if i can't resolve this, then there's little point me carrying on with putting Ubuntu on here - something i'd be very disappointed about because i'm keen to sample its features. etc.

- G

You don't need no stinking ndiswrapper.  Use the madwifi drivers.

You need to do two things:

1. Install a kernel that is compatible with madwifi. Go to synaptic and type Atheros. Install a kernel that supports madwifi. You will then reboot.

2. I have a procedure to install madwifi drivers. [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html). 

This will install the madwifi drivers and network manager.

Reboot and your card will be sniffing for wireless networks.

It worked like a charm on my laptop with an Atheros wireless card.

---

