---
title: "Noob: Trouble following directions for WPA Networking"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by bowkerhouse on 2007-03-17
Hello!  I've just installed Ubuntu on my Dell Latitude and so far I'm very impressed.  I've got the wired network card working fine, and I was able to get the wireless card working if I turn WPA off on the router.  But I really want to use WPA...

I've found some directions for enabling it, but I must be misunderstanding a step or something, because what I'm seeing doesn't seem to follow the guide.  Am I missing an obvious Linux/Ubuntu step that I'm just not familiar with?

The directions I'm trying to follow are here:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy/Networking#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager](http://ubuntuguide.org/wiki/Ubuntu:Edgy/Networking#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager)

So I did this:
sudo apt-get install network-manager-gnome

and that appeared to finish correctly.  Then I rebooted.

When I look in the system tray (in the upper right) I see a little icon of two computer screens that identifies itself in the about windows as NetworkManager Applet 0.6.3.  (Is this the right version?)

Then the directions say this:
>>
Once Network-Manager is installed, click on the NM icon in the notification area (default is at the top right of Ubuntu/Gnome). Choose your network, then enter your passphrase. Type a password for the keyring, and you're set.

If you don't see your network, click "Create New Wireless Network...", type your essid/networkname, then choose "WPA Personal" for wireless security. 
<<

When I click on the NetworkManager icon I only see an option for "Wired Network" and there is no option for creating a new wireless network.  Hmm..

When I go into the Networking control panel I can adjust the properties of the wireless networking, but there are no options for WPA; I can only select a password type, either "Plain" of "Hexadecimal".

The directions seem to simple, but I feel like I must have the wrong version of the Network Manager aplet installed.  The wireless networking works fine if I turn security off (which is not a good solution for me).

Can anyone see where I've gone astray?

Thanks!
-Brian

---

### Post by eljalill on 2007-03-17
You could make sure, you have the wpasupplicant installed. If you open synaptic and search for it, you can check. 

But I don't know for the "create wireless network".

---

### Post by bowkerhouse on 2007-03-17
Thanks for the reply!

I opened Synaptic and found that I have WPASupplicant 0.5.4-5 installed.  Do I need to turn it on, or enable it or something?

-Brian

---

### Post by Ozor Mox on 2007-03-17
You need to edit the etc/network/interfaces file and comment out all of the lines except the loopback interface ('auto lo' and 'iface lo inet loopback' lines). Remember to make a backup; I didn't and caused Ubuntu to stop booting!

Apparently the easier way is to go to System > Administration > Networking and disable all the networks there by selecting them, clicking properties, and unchecking the enable box. This will allow network manager to manage these networks for you and you'll see them in a drop down if you select the icon.

---

### Post by bowkerhouse on 2007-03-18
Thanks for the reply, but I'm afraid I'm still stuck.

I tried the "easier way" first and disabled each of the network connections, but the wired network (the one I'm currently using while I try to figure out WPA for the wireless) doesn't turn off.  When I go back into the Networking control panel it's enabled again.

So I found the interfaces file - it was just where you said - but it will only let me open it as read only.  I went into the properties of the file and it says it's owned by "root" and won't let me change it.

I have a few other questions - I copied the file to the desktop to make a backup, but if Ubuntu stops booting I don't know how to get in to replace it.  Would I boot from the Live CD?

Also, it looks like you put a # in front of each line you want to comment out, is that correct?  (Assuming I figure out how to open the file to edit it...)

I'm sorry I'm not catching on very quickly - I've been a Windows user/admin since the beginning and am feeling pretty lost with Linux right now.  But I truly want to understand and appreciate any help you can give me!

Thanks,
-Brian

---

### Post by bowkerhouse on 2007-03-18
New development!  But still not quite working...

After my last session I put my laptop to sleep.  When I woke it up and it reestablished networking it behaved differently; Now when I click on the NetworkManager icon I DO get a list of wireless networks, including mine!  And when I select mine it does ask me for security settings!

But it only gives me three flavors of WEP as options; no WPA. :( 

Apparently dissabling all the network interfaces in the networking control panel did work, but the networking system needed to be rebooted or something.

So I'm closer!  But I still can't seem to find WPA.  Anyone else have any clues for me to follow?

-Brian

---

### Post by bowkerhouse on 2007-03-19
I've done a little more looking around, but still can't seem to get WPA options to show up in my wireless configuration.  Any help would be very appreciated!

-Brian

---

### Post by Ozor Mox on 2007-03-19
To answer your original question about how to modify the interfaces file, open it with root privileges, that's:

```
sudo gedit interfaces
```

when you're in the etc/network folder. Or you can open up the file browser with root privileges using:

```
gksudo nautilus
```

and browse to the correct folder and open the file. You will now be able to save your changes.

And yes, # is used to comment out the line. Good for reversing changes as I learnt!

As for WPA, I'm not entirely sure about this yet. I did get it to work once using [these instructions](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy) (the part that says "Configuration of WPA"), however modifying my interfaces file as it instructed completely borked the entire OS and I couldn't boot into it anymore, and I stupidly forgot to backup the original file. Now that I've reinstalled Ubuntu, I will be trying to connect to a WPA network tonight so I'll let you know how I get on!

---

### Post by cwmaxson on 2007-03-19
I think this connection manager deals with WPA better:

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

Cheers

---

### Post by toddhd on 2007-03-19
I just got WPA-PSK working on my Dell XPS 180. Took a lot of time to understand, and I never was able to get it working from a GUI like Network Manager or Wifi Radar. Post your /etc/network/interfaces file here and I'll see if I can help.

---

### Post by Ozor Mox on 2007-03-19
Well I clicked on the Network Manager icon with a WPA network as opposed to a WEP network in range, the latter of which worked perfectly. Network Manager detects that it's a WPA enabled network and asks me for a WPA key instead of giving me the various WEP encryption options, and offers to store my password in Gnome Keyring Manager.

And that's it, it works! I have no idea why yours would not detect that it's a WPA network, is it definitely enabled as one, or is this just a problem with Network Manager and certain cards? If the latter, I would suggest using a different network manager and see if that works.

---

### Post by bowkerhouse on 2007-03-20
Ozor Mox: I am jealous of your success!  I do have other networks in the surrounding area that show up in my Network Manager.  It could be that one or more of them are WEP - Maybe that's messing up the options for my network...?  But if I go to create a custom connection it still only gives me the WEP options.  Hmm...

Toddhd: I will gladly post my interfaces file with hopes of help!  I am not afraid to completely reinstall Ubuntu if necessary - I haven't really done anything with it yet.

I don't know if you will need this info of not, but just in case:
I'm using a Dell Latitude Cpx Model: PPX
My wireless card is a Linksys WPC54G ver.2
My SSID is 701NState

I think I got the file attached, but I had to add a .txt on the end for the upload tool to accept it.  Originally the file had no extension.

THANKS!
-Brian

---

### Post by cwmaxson on 2007-03-20
Try using WICD wireless manager, I had the same problems, then used it to get wireless working and it worked "out of the box".  It was written for Dapper and Edgy and is great.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

Cheers

---

### Post by Ozor Mox on 2007-03-20
Bowkerhouse, try doing:

```
sudo apt-get install wpasupplicant
```

just to make sure the WPA package is definitely installed. It was installed by default for me on Edgy, but it may be worth checking.

If not, I'd definitely try WICD. Cwmaxon, is it a better option than Network Manager? I was going to try it as it may help my connection timing out when I leave it idle for a while.

---

### Post by Fitzcarraldo on 2007-03-20
I recently configured my ubuntu 6.06 Dapper Drake installation for WPA-PSK ("WPA-Personal") and described the procedure in detail in the following thread, which may be of some help:

[http://ubuntuforums.org/showthread.php?t=378179](http://ubuntuforums.org/showthread.php?t=378179)

---

### Post by toddhd on 2007-03-20
Thanks for posting your interfaces file, that helped a lot. Please try the following - it is working for me on a similar Dell machine.

First, open up a terminal, and enter the following:

```
wpa_passphrase 'your_essid' 'your_ascii_key' 
```

That will spit back a result that looks something like this:

```
network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
} 
```

That long encoded string after psk= is what we need, so keep it around somewhere that you can copy/paste it in a moment.

Next, open up your interfaces file:

```
sudo gedit /etc/network/interfaces
```

Delete everything (if you want to, back it up first), and replace it with this:
```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-driver madwifi
wpa-conf managed
wpa-ssid Test
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
```

Replace the wpa-ssid line with your own SSID (the name of your router) and replace the wpa-psk with that long encoded string we just generated above.

Ok, you are done the hard part! Now cross your fingers, and try one last command:

```
sudo /etc/init.d/networking restart
```

Let that run for a few seconds until it completes. When it is done, try your internet connection.

Hope this helped!

PS - I typically have to run that last "restart" command every time I reboot. I'm still working on that...

PS - If for some reason this is still not working, try setting "wpa-driver madwifi" to "wpa-driver wext" and then restart the network service.

---

### Post by cwmaxson on 2007-03-20
WICD works great, it was written by compwiz and does everything network manager is supposed to.

Cheers.

---

