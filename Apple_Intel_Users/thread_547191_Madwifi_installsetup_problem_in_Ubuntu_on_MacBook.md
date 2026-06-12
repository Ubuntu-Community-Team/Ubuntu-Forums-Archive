---
title: "Madwifi install/setup problem in Ubuntu on MacBook"
date: 2007-09-09
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-09-09
I set up a new MacBook to multiboot several Linux OSes over the last week or so and most things are going well.
However, wireless is causing headaches.
I used this [guide]("https://help.ubuntu.com/community/MacBook") to get wireless going initially in Ubuntu.
However, for various reasons I cannot connect wireless here any more. And this is despite quite a few attempts (AFAIK identical to the first) to reinstall the MadWifi drivers.
Now, I've just come across (what is to me) an interesting anomaly which may have some bearing on my recent lack of success in this area.
The directory /lib/modules has two subdirectories (2.6.20-15-generic and 2.6.20-16-generic corresponding to the current and last Ubuntu kernels).
While both of these subdirectories have "madwifi" sub-sub-directories, only that associated with 2.6.20-15-generic contains any drivers. That linked to the other kernel is totally empty.
Now I'm using the 2.6.20-16-generic kernel and I'm wondering is this the cause of my inability to get a wireless connection.
If it is, why are the MadWifi modules going in there and not into the directory corresponding to the current kernel?
Any views?

---

### Post by moore.bryan on 2007-09-09
[I]hello, again, paulfxh.

sorry to hear you're still running into problems.  i think you hit the nail on the head with your analysis of the problem.  now, i think you can easily solve it by symlinking the drivers in the 2.6.20-15-generic directory to the 2.6.20-16-generic directory.

if you have no clue what i just wrote, just post.
[/I]

---

### Post by bsantos on 2007-09-09
You need to run make install for the new kernel AFAIK.

---

### Post by PaulFXH on 2007-09-10
Thanks for the replies.
> i think you can easily solve it by symlinking the drivers in the 2.6.20-15-generic directory to the 2.6.20-16-generic directory.
I'm not at all sure as I think that the madwifi drivers are kernel-specific which means you can't successfully transfer transfer divers from one kernel to a different one?
Additionally, the Ubuntu installation on my desktop computer (which has NEVER had a wireless card) has madwifi drivers specific to each of 6 kernels in /lib/modules/<kernel>/madwifi which obviously come with the install.  It seems these are legacy madwifi drivers that do not work on more modern chipsets and indeed must be removed prior to installing the updated drivers.
> You need to run make install for the new kernel AFAIK.
Well, i have but they don't go into the /lib/modules/,kernel./madwifi directory.
It seems the drivers are integrated into the kernel during the make operation.
Indeed, looking at the madwifi driver README,  this is mentioned:
> When
the driver is successfully loaded it creates two devices, named "wifi0"
and "ath0".  The output from iwconfig should look like this:

    lo      no wireless extensions.
    
    wifi0   no wireless extensions.
    
    ath0    IEEE 802.11b  ESSID:""
            Mode:Managed  Channel:0  Access Point: Not-Associated
	    Bit Rate:0 kb/s   Tx-Power:50 dBm   Sensitivity=0/3
	    Retry:off   RTS thr:off   Fragment thr:off
	    Power Management:off
	    Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
	    Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
	    Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When I run "iwconfig" in a terminal I get this
> lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:155404  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


which suggests to me that the driver IS successfully loaded.
So, why won't it work for me?
I would very much welcome comments/advice as my wireless experience up to now is very limited.
Thanks
Paul

---

### Post by cyberdork33 on 2007-09-10
> **PaulFXH said:**
> Thanks for the replies.

I'm not at all sure as I think that the madwifi drivers are kernel-specific which means you can't successfully transfer transfer divers from one kernel to a different one?
Additionally, the Ubuntu installation on my desktop computer (which has NEVER had a wireless card) has madwifi drivers specific to each of 6 kernels in /lib/modules/<kernel>/madwifi which obviously come with the install.  It seems these are legacy madwifi drivers that do not work on more modern chipsets and indeed must be removed prior to installing the updated drivers.

Well, i have but they don't go into the /lib/modules/,kernel./madwifi directory.
It seems the drivers are integrated into the kernel during the make operation.
Indeed, looking at the madwifi driver README,  this is mentioned:


When I run "iwconfig" in a terminal I get this

which suggests to me that the driver IS successfully loaded.
So, why won't it work for me?
I would very much welcome comments/advice as my wireless experience up to now is very limited.
Thanks
Paul

If there are precompiled modules from the repositories on your system, they will interfere with newer user-compiled modules (uvcvideo for isight, fglrx, etc). You have to remove/move or blacklist the modules you do not want to load.
In:
[SIZE=-1]```
/etc/default/linux-restricted-modules-common
``` list the module you want to disable, then it should not load the default module and you can load the custom module without interference.

Also, when you compile/install your own module they are not necessarily placed in the "[/SIZE]2.6.20-16-generic" folder, but in a more generic location.

---

### Post by PaulFXH on 2007-09-10
@cyberdork33
Thanks for the comment.
However, it seems that I DON'T have any "legacy" modules from the repositories associated with the wireless card as the directory /lib/modules /<kernel>/madwifi/ is totally empty for 2.6.20-16-generic which is the kernel I'm using. 
Therefore I can't see that anything needs to go onto the blacklist you mentioned.
Nevertheless, I'm still unable to get a wireless connection even though the driver seems to be successfully loaded.
Any views on what else I might try?
Thanks
Paul

---

### Post by cyberdork33 on 2007-09-10
> **PaulFXH said:**
> @cyberdork33
Thanks for the comment.
However, it seems that I DON'T have any "legacy" modules from the repositories associated with the wireless card as the directory /lib/modules /<kernel>/madwifi/ is totally empty for 2.6.20-16-generic which is the kernel I'm using. 
Therefore I can't see that anything needs to go onto the blacklist you mentioned.
Nevertheless, I'm still unable to get a wireless connection even though the driver seems to be successfully loaded.
Any views on what else I might try?
Thanks
Paul
I believe what is in the directory you are listing would be where the repository versions are stored. If you are compiling your own, they may be elsewhere. Try
```
locate ath_pci.ko
``` and see what results you get.

---

### Post by benanzo on 2007-09-10
User-compiled versions of Madwifi install in **/lib/modules/$(uname -r)/net** not **/lib/modules/$(uname -r)/madwifi**.

If you need to uninstall a version of madwifi that you compiled yourself you should go back to the original madwifi build directory and do:
```
make uninstall
```
It's not always safe to just remove the installed module by hand.

After you've finished, be sure to run:
```
sudo depmod -ae -F /boot/System.map-$(uname -r)
```
To relink all the module dependencies inside the kernel and see if you've got any errors.

---

### Post by PaulFXH on 2007-09-10
Thanks for the replies and advice.
The ath_pci.ko module is indeed where benanzo said it would be (/lib/modules/2.6.20-16-generic/net).
However, my objective here is simply to re-establish the wireless connection I had about a week ago.
As of now, the driver seems loaded and in good shape (based on lsmod indication), therefore I don't need to uninstall it at all.
Additionally, my Atheros wireless card is recognised (based on lshw) and there is no indication that this card is de-activated (again based on lshw).
From what I can see (and I'm following this Ubuntu wifi troubelshooting [guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")), there is no communication between the wireless card and the router (Netopia 3347WG).
And that's where I'm stuck -- I can't see where to go from here.
(Note that this is my first wireless experience).
Any clues?

Thanks
Paul

---

### Post by cyberdork33 on 2007-09-10
I think benanzo may have been implying that you might try uninstalling and rebuilding the modules. Just because the hardware is listed doesn't necessarily mean everything is working...

As for why it is not working now (even though it used to) can be for several reasons. what errors are you getting, if any? are you using network-manager? does it have the option to even use wireless?

---

### Post by PaulFXH on 2007-09-10
> I think benanzo may have been implying that you might try uninstalling and rebuilding the modules
OK, I'll try this later when things are a bit quieter here.
> what errors are you getting, if any?
The only "kind of" error I get is that I can't get any DHCP offers when I run "sudo dhclient ath0".
Actually, I think I was wrong earlier when I said there was no "association" between the Atheros card and the router because running "iwconfig" did, for  while anyway; show a MAC address in the Access Point part of the ath0 output. However, for reasons I don't understand, this has now become "not associated".
[QUOTEare you using network-manager?][/QUOTE]
Yes, I am.
> does it have the option to even use wireless?
Yes, it has three options: Wireless (fully configured and enabled), Wired (similar) and Modem (not configured).

---

### Post by cyberdork33 on 2007-09-10
> **PaulFXH said:**
>  Yes, it has three options: Wireless (fully configured and enabled), Wired (similar) and Modem (not configured).

That sounds like the network config tool in the admin menu. Network-Manager is a different applet in your taskar.

---

### Post by PaulFXH on 2007-09-10
Yes, I have the dual monitor thing.
Right now it does not indicate any Wireless option (only Enable Networking). However, if I Enable Roaming Mode on the wireless connection in System>Administration>Network, then an Enable Wireless option additionally comes up in the Network-Manager.

BTW, I tried benanzo's suggestion to uninstall the madwifi driver and re-install. Unfortunately, no improvment.
However, "iwconfig" now shows an "association" between the router and the wireless card but still I can't get any "dhcpoffers" when I type "sudo dhclient ath0".

---

### Post by cyberdork33 on 2007-09-10
This sounds similar to the issues that were being discussed in the Santa Rosa thread. There were only certain versions of madwifi that were working, others were not.

---

### Post by PaulFXH on 2007-09-10
Oh boy. Looks like I'm going to have to either wait for a updated driver or hunt around for an older one.
Anyway, thanks or your help.

---

### Post by benanzo on 2007-09-10
I think maybe you should disable ifup/ifdown from managing your network and see if NetworkManager can get you connected by itself.  You shouldn't have to do anything with ifconfig iwconfig dhclient etc.  NetworkManager is the preferred interface to administer your connections.

In a terminal do:
```
sudo gedit /etc/network/interfaces
```
and comment out everything except for:
```

auto lo
iface lo inet loopback

```
Then save and close gedit.

Now in a terminal do:
```
sudo /etc/init.d/networking restart
```
That should kill any network connections that ifup/ifdown is trying to make (it wont see any network interfaces anymore.)

Now in a terminal do:
```
sudo killall NetworkManager
```
and then:
```
sudo NetworkManager --no-daemon
```
This will spawn the NetworkManager applet (nm-applet) in your notification area.  Make sure that networking (including wireless) is enabled by right-clicking it and selecting the appropriate options.  You'll notice that the "--no-daemon" option cause NM to live in the terminal and print everything it was doing (or trying to do) so you could read it.

If you're not getting any wireless make sure that the module is loaded.  In another terminal (while NetworkManager is still running) do:
```
sudo modprobe ath_pci
```

After a second or two you can click the applet and hopefully you'll see some networks nearby.  When you close the NetworkManager terminal, NM will die too.  To start it again without requiring the terminal be open just do:
```
sudo NetworkManager
```

---

### Post by PaulFXH on 2007-09-10
OK, I did all that and now in the Network Manager applet (on rt click) I have both Enable Networking and Enable Wireless checked.
The ath_pci driver shows up as being loaded when I type lsmod so that looks good.
However, when I click on Connection Information in Network Manager, it seems to indicate that only the Eth0 (wired) connection is active.
Essentially now both Wired and Wireless connections are in Roaming Mode.
However, it doesn't seem like Wireless is truly (if at all) functioning. For example, if I disconnect the ethernet cable, Network Manager immediately gives me a Disconnection message and I can't ping anything.
So, is there more to this?
BTW, I'll be sleeping fairly soon so if you reply I may not be able to respond until tomorrow.
Very many thanks for ll your suggestions. I'm learning a lot.
Paul

---

### Post by cyberdork33 on 2007-09-10
it will automatically switch when you have the ethernet cable connected or removed. Once you remove it you will have to give it a second to switch over, then you should be able to select a wireless network if everything is working.

---

### Post by PaulFXH on 2007-09-11
Unfortunately, the wireless just doesn't connect at all when the cable is removed even after several minutes.
When I replace the cable, connection is resumed in about two seconds.
Therefore, I am forced to conclude that, as cyberdork33 said, 
> only certain versions of madwifi that were working, others were not.
Time to look for a version that works.

The ath_pci version I was using is 0.9.4.5 (svn r2702). It would be interesting to hear from anybody who has this working in Feisty on a MacBook.

Thanks a lot for your help
Paul

---

### Post by Namtabmai on 2007-09-11
Just finished installing Ubuntu Feisty on my Macbook Pro today and encountered the same problems posted here. All Windows drivers (using ndiswrapper) seemed to cause my keyboard to lock and the trunk checkout of madwifi worked in so much as it created ath0 but I couldn't connect to my router regardless of the security settings.
Finally after fiddling around with various revision checkout of madwifi I decided to go back to the first revision which merged the Macbook Pro wireless code, 2360.

And it worked! I'm now connected to my router using WPA security, it's only been a few hours so we'll see if I get disconnects or other problems down the line.

---

### Post by PaulFXH on 2007-09-11
@Namtabmai
Can you please tell me more precisely which version of the madwifi driver works for you and from where you downloaded it?
I have already tried two older versions but they equally did not work for me.
I know I'm using the MacBook (rather than MBP) but I don't have a lot of options at this stage.
Thanks
Paul

---

### Post by Namtabmai on 2007-09-11
I checked out the code from the madwifi SVN, I choose the first revision which contained the newly working code (2360)

So pretty much follow the information here, [https://wiki.ubuntu.com/MacBookProFeisty#Wireless](https://wiki.ubuntu.com/MacBookProFeisty#Wireless),
But replace the svn checkout line with;
```

svn checkout -r 2360 http://svn.madwifi.org/trunk madwifi

```

---

### Post by PaulFXH on 2007-09-11
Well, I'm afraid that didn't work for me either.
I have now tried a total of seven different "legacy" packages from the madwifi [archive]("http://snapshots.madwifi.org/") and every single one has failed for the same reason which is that attempts to get a IP address assigned to the wireless connection using "sudo dhclient ath0" all result in
```
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1c:b3:b4:9e:98
Sending on   LPF/ath0/00:1c:b3:b4:9e:98
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
Note that I do actually get an "association" between the wireless card and the router but I cannot get an IP address.
I have tried using a static IP and even switching off the router's WEP encryption, but the result is always the same -- no DHCP Offers!
Was I really so fortunate initially in that the first madwifi package I tried actually worked without any problems at all and not a single one since then?
The fact that I haven't been able to repeat this success suggests to my inexperienced mind that this is more than just a mal-functioning driver problem.
The first driver packaged I tried was from here ([http://snapshots.madwifi.org/madwifi...current.tar.gz](http://snapshots.madwifi.org/madwifi...current.tar.gz)) but I have not been able to track down older versions of the "trunk-current" branch of madwifi as only the current version seems to be included in the archive.
I think I downloaded the working version on September 1st. If anybody knows how I can get my hands on this, it would be very interesting to try it out again.

---

### Post by pxwpxw on 2007-09-11
PaulFXH

It may not be a driver problem at all, it is certainly not a madwifi/MacBook C2d problem.
Also note I folowed the howto, but then found I had not installed Linux-headers for the kernel I was using, but I assume you have that covered, not sure if it produces an error.

Using the madwifi drivers here on macbook c2d, I find when changeing from a wired ethernet - router to a wireless router, the only way to get it sorted is using complete shutdown - unplug ethernet - restart. There is something in the startup sequence that defies logic, and does not get done with manual restarting the network afte changes

The network manager here (on xubuntu) chooses its DNS ip setting according to what is available at startup, not what I configure. It needs to be checked to be sure what is happening. It will be different for wired or wireless. If you leave the ethernet cable connected, the Network Manager dns setting may get stuck.

I also have a firewall, using firstarter to control it. This also has to be reconfigured manually to open the wireless (ath0). This can prevent dhclient setting up early in the startup.

There are many possible ways to get the configuration wrong, but the restart-hands-off system seems to sort it out, just by checking DNS setting  and firewall for ath0/eth0, and doing another restart if needed.

I should say I did 16 restarts before I could work out what was going on here.

I am not sure if that fits with your case, there are two many variables, but you might be able to see it.

---

### Post by cyberdork33 on 2007-09-11
Yea I think we are passed it being a driver problem. If network-manager sees SSIDs and you can specify one to connect to and can associate, then it is an issue with something else.

---

### Post by PaulFXH on 2007-09-11
Thanks for those suggestions and comments.
Well, I tried a lot of combinations of things including:
--reboot with ethernet cable disconnected
--wireless on roaming mode or with specific settings
--with encryption enabled and disabled

but, I'm still in the same situation -- no wireless in Ubuntu.

On one occasion, however, the NetworkManager applet, changed from being a dual monitor, to a small bar graph (which I had never seen before although I've heard others refer to it). When this happened, the tool-tip said
> wireless network connection to <essid> 100%
This latter figure reduced to 98% now and again.
So, this looked very promising but unfortunately, I still couldn't ping anything or bring up a page in a browser.

---

### Post by cyberdork33 on 2007-09-11
> **PaulFXH said:**
> Thanks for those suggestions and comments.
Well, I tried a lot of combinations of things including:
--reboot with ethernet cable disconnected
--wireless on roaming mode or with specific settings
--with encryption enabled and disabled

but, I'm still in the same situation -- no wireless in Ubuntu.

On one occasion, however, the NetworkManager applet, changed from being a dual monitor, to a small bar graph (which I had never seen before although I've heard others refer to it). When this happened, the tool-tip said

This latter figure reduced to 98% now and again.
So, this looked very promising but unfortunately, I still couldn't ping anything or bring up a page in a browser.
That means it is connected  ;) The bar graph should adjust with signal strength. Are you sure this is not a router / DHCP server problem?

---

### Post by PaulFXH on 2007-09-11
I honestly know very little about router/dhcp interactions so  can't really answer your question. However, my wired network runs on DHCP through the same router and I have never had a connectivity problem there.
Is there any way I can check whether there is a problem or not?

---

### Post by cyberdork33 on 2007-09-11
> **PaulFXH said:**
> I honestly know very little about router/dhcp interactions so  can't really answer your question. However, my wired network runs on DHCP through the same router and I have never had a connectivity problem there.
Is there any way I can check whether there is a problem or not?
you might just try rebooting the router if you can... just unplug it for about 10 seconds. IDK if that will help now from your other information, but I guess it is worth a try. 

I was initially thinking it was a driver problem because it sort of sounded like you were not successfully switching from a scanning mode to the normal operating mode. If you have the bar icon, then you should be 'connected' (with IP), and it is a swirling looking animated icon while it is trying to get an IP after associating, so if you made it that far, it sounds like it worked (once anyway). After unplugging ethernet, are you (left) clicking on the network manager and selecting a SSID? does it show any SSIDs?

If you couldn't get access to the net when connected previously, then I would blame something with the dns config as suggested, or that your router is not completing NAT correctly.

---

### Post by PaulFXH on 2007-09-11
OK, switched router on/off but, once again, no improvement.
Furthermore, the appearance of Network manager as a small bar graph seems to have been a bit of a flash in the pan as nothing even remotely ressembling this has occurred since then.
> After unplugging ethernet, are you (left) clicking on the network manager and selecting a SSID? does it show any SSIDs?
No, no SSID is shown in Network Manager. However, when the bar graph appeared a while ago, the tooltip referred to the ESSID from my ISP which is what is mentioned in my router webpage. Slightly later this turned to "wireless network connection to unknown 100%" which might be that a stronger signal was reached from some other source here in the neighbourhood where I am. Give that my laptop is right beside my wireless router this would be strange.
In any event, I can't under any circumstance reach anything now.

---

### Post by PaulFXH on 2007-09-11
OK, as a last ditch attempt, I decided to try once more the madwifi package recommended by Namtabmai in post #22 above.
Then I used System>Administration>Network to put the wireless network on roaming mode.
Next I rebooted after unplugging the ethernet cable. 
When Ubuntu had booted there was no internet connection but this time the Network Manager applet (dual monitors) did refer to the ESSID but the radio button was empty.
So, I clicked the radio button, and it came back looking for my WEP key.
After I entered this, it came back again asking me to provide a password for the keyring which I gave.
Then the Network Manager applet changed to the bar graph and I had a CONNECTION=D>
So it wasn't just a flash in the pan after all but boy it sure took some effort.
This time, also, it's a real connection in that I can ping and browse just like with the wired connection.
Not sure how long this is going to last but it looks very steady for the moment.
Many thanks to everybody for guiding me through this.
Paul

---

### Post by bsantos on 2007-09-11
Since the recent n-m and pam updates (I don't know if it is related) my working wifi with madwifi stopped working.

I tried to open my AP and I can associate with the AP manually, attribute an IP and it works. So the driver is OK.

But n-m doesn't connect even without encryption.

With encryption I get the password dialog over and over again, also no keyring password dialog, even after deleting the keyring.


Anyone else on a Core 2 Duo MacBook using madwifi with up to date Gutsy is able to use WPA2, even any kind of cipher through n-m?

*sigh* :frown:

---

### Post by PaulFXH on 2007-09-12
Just to mention that wireless is still working absolutely perfectly in Ubuntu on my MacBook.
I want to now outline some different features that I noticed this time in comparison to the wireless I had in Ubuntu on the same machine just about two weeks ago.

Differences:
1) Now when I boot with the ethernet cable disconnected, I am asked for a password to unlock the NM keyring. This never happened before.
2) Now when the wireless connection is established (within seconds of providing the keyring password), the NM applet changes to a bar graph. Before it was always presented as a dual monitor

Below are what I believe to have been the key elements in the dramatic change from a system that just didn't work to one that works like a charm:
1) I am convinced that some madwifi drivers just did not work on my system. So the right driver has to be chosen. In my case this ( http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz} for sep-11-207 did not work while this (svn checkout -r 2360 [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi) did.
2) The wireless netwrok must be set to roaming mode in System>Administration>Network
3) To get the wireless connection to startup initially and configure itself correctly, the advice of pxwpxw in post #24 above are crucial. So, take out the ethernet cable and reboot.

Now I will also mention that I had, in my desperation, installed some packages from Synaptic simply because their discription seemed to be relevant to wireless use on a laptop -- no stricter criterion than this was used.
Included in these were the following:
aircrack
aircrrack-ng
ifplugd
network-manager-openvpn
network-manager-pptp
network-manager-vpnc
waproamd

It would be interesting to hear from those more knowledgable than me which if any of these packages may have assisted in this success.
Thanks
Paul
weplab

---

### Post by cyberdork33 on 2007-09-12
> **PaulFXH said:**
> Differences:
1) Now when I boot with the ethernet cable disconnected, I am asked for a password to unlock the NM keyring. This never happened before.
2) Now when the wireless connection is established (within seconds of providing the keyring password), the NM applet changes to a bar graph. Before it was always presented as a dual monitor

Mu guess would be that you did not have the network manager applet on the panel, but rather the default gnome network applet. The keyring unlock prompt is normal (at least when using n-m). Since you are using WEP, you could have bypassed the n-m method and used the older ubuntu wifi config tool to setup connection info, and it did not ask for the keyring password. You might be able to bypass this in the keyring manager under the admin menu...

> Now I will also mention that I had, in my desperation, installed some packages from Synaptic simply because their discription seemed to be relevant to wireless use on a laptop -- no stricter criterion than this was used.
Included in these were the following:
aircrack
aircrrack-ng
ifplugd
network-manager-openvpn
network-manager-pptp
network-manager-vpnc
waproamd

It would be interesting to hear from those more knowledgable than me which if any of these packages may have assisted in this success.
Thanks
Paul
weplab

The aircrack and weplab packages are for cracking WEP keys... Don't want to get too much into it as it is a sensitive issue, but I am positive that they are not _needed_ for you to connect to _your own_ network.

The network manager packages you listed are special plugins for connecting to certain types of network connections i.e. VPN

ifplugd is actually a nice little daemon that detects when you plug/unplug a ethernet cable. Shouldn't be needed though as this is done by other packages in Ubuntu already, and to do anything with it, you would have to link or write some scripts to control the network interfaces (This should all be done by n-m using more current methods).

I have never even heard of waproamd but since it is a daemon, it probably needs other scripts, etc to actually do anything useful.

---

### Post by bsantos on 2007-09-12
Is there any way to clean up everything keyring related?

I've reinstalled all the packages, deleted all the keyrings, reinstalled all the pam stuff, gdm, etc, but the keyring dialog never shows up.

Wifi works manually but it doesn't with n-m. :(

Starting with eth disconnected had no effect.

Will I need to reinstall from latest tribe?

---

### Post by cyberdork33 on 2007-09-12
> **bsantos said:**
> Is there any way to clean up everything keyring related?

I've reinstalled all the packages, deleted all the keyrings, reinstalled all the pam stuff, gdm, etc, but the keyring dialog never shows up.

Wifi works manually but it doesn't with n-m. :(

Starting with eth disconnected had no effect.

Will I need to reinstall from latest tribe?

Sorry, I really can't help too much here. I remember on earlier tribes that there were some weird bugs with the keyring that would make you set the keyring password everytime n-m tried to access it... I noticed that the pam updates messed some stuff up the other day, then a newer update was released and fixed a bit of it, so just make sure you are up to date I guess... sorry, i can't help more... maybe look for related bugs?

---

