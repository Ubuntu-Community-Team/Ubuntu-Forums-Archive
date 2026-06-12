---
title: "Starting WiFi in Fluxbox"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by countryparson on 2007-05-30
Hello, 
I was wondering how to start my wifi internet connection while using fluxbox.  I'm able to start wifi in gnome and switch over to fluxbox and the connection is still up.
I want to be able to boot straight into fluxbox and start the connection.
Is there a command line command or something I should add to the fluxbox init file to do this?
Thanks for any help,
-Scott

---

### Post by yabbadabbadont on 2007-05-30
What exactly do you do in gnome to start the connection?

---

### Post by dolphin_oracle on 2007-05-30
it depends a little on your card, but I use iwconfig and ifconfig from the command line.  I'm using a RT61 based card with a native linux driver.

You might also try

$sudo ifup *interface_name*

---

### Post by countryparson on 2007-05-30
wow, thanks for such quick responses
Network manager usually starts the connection automatically.
I tried using wifi radar before and it hadn't worked, I just tried it again and it worked.  
For future reference would the interface name be something like eth0 or eth1?
Thanks for the help.  The support available in the forums is the main reason I've switched to ubuntu!
-Scott

---

### Post by jargoman on 2007-06-07
ya it's probably eth1. It depends on your distro, card driver and other factors. Basicaly eth1 means ethernet card 2. eht0 being 1 of course. It may also be wlan0.

---

### Post by Bachstelze on 2007-06-07
To know for sure :

```
sudo iwconfig
```

---

### Post by kill4killin on 2007-06-07
I'm having the same problem with the network manager fluxbox thing. I usually use Gnome and finally got settled and so I thought, well, I want to get fluxbox back like I used to have on my slackware box (wired connection). So I did all the usual, apt-get install fluxbox and what have you, but, the one thing I am unable to do in fluxbox that I can do in Gnome is use network-manager. I went through all the trouble of upgrading to the network-manager 0.6.5 packages that were put in a thread here not to long ago to fix the issue with dual layer wpa authentication. I would really like to be able to use this in fluxbox but so far have found no means of getting it to work. I thought I could try manually starting it once I booted up but it appears that when I try to type in "network-manager" in terminal it says that it is not a valid command. So is it called something else or is there a way to specify it in ~/.fluxbox/startup?

Any help would be appreciated, thanks.

---

### Post by Pugwash on 2007-06-07
If you have network manager, just stick "nm-applet &" in the startup file (but make sure its before the "exec /usr/local/bin/fluxbox.... " line). It works for me.

---

### Post by kill4killin on 2007-06-08
Thanks a bunch Pugwash! That worked perfectly for me! Now I have to get the front audio keys on my laptop to start working and figure out how to load xscreensaver so that it starts automatically in the background and I'm golden...until I find another problem.

---

### Post by Pugwash on 2007-06-09
> **kill4killin said:**
> Thanks a bunch Pugwash! That worked perfectly for me! Now I have to get the front audio keys on my laptop to start working and figure out how to load xscreensaver so that it starts automatically in the background and I'm golden...until I find another problem.

Don't know about the audio keys, I haven't got that sorted. But you can use wmix, (its in the universe I think). If you want xscreensaver to start  automatically, stick this in your startup file like you did network manager:  xscreensaver -nosplash &

Hope that helps.

---

### Post by quantumcheese on 2007-07-01
> **kill4killin said:**
> Now I have to get the front audio keys on my laptop to start working...

I used a combination of xmodmap and keybindings, in conjunction with alsamixer.
my .xmodmaprc contains
```

! vol up
keycode 176 = XF86AudioRaiseVolume
! vol down 
keycode 174 = XF86AudioLowerVolume
! vol mute
keycode 160 = XF86AudioMute
```
(check the keycodes for your buttons using xev) and then I have 
```

XF86AudioMute             :ExecCommand amixer set Master toggle
XF86AudioLowerVolume      :ExecCommand amixer set Master 5%-
XF86AudioRaiseVolume      :ExecCommand amixer set Master 5%+
```
in .fluxbox/keys.  Hope this helps; check the xmodmap man page for more.

---

### Post by dxmosiris on 2007-07-08
Is there a good CLI tutorial for associating a wireless card with a specific ap? I don't want to use any applets or gui alternatives. This is one of the last features I need to get right so I can start using fluxbox exclusivley.

The best I can come up with is >> iwconfig ethX essid apname channel x rate auto key s:apkey.

That obviously doesn't work but am I at least on the right track? If all else fails what do other fluxbox users do to associate their wireless cards without using the gnome network manager. I haven't yet tried wifi-radar but I will look into it if I have to.

Thanks

---

### Post by dolphin_oracle on 2007-07-08
that's pretty close to what I use, but I've got a rt61 card and it uses a text file to configure its settings.  However, I've used iwconfig to set to a different ESSID.  Once you associate, you need to run dhclient to get a new IP address and such if you are using dhcp.

for instance, I would use:
$ sudo iwconfig ra0 essid xxxxxxx
$ sudo dhclient ra0

That will get you on most public access points, like hotels and such.  The channel and rate info should be defaulting to AUTO (at least mine does).  I don't know about the WEP key, since I use the text file for my secured connections.

also,                iwlist [interface] scanning                will give you a list of available networks.

check out this site for iwconfig commands and syntax

[http://www.wirelessdefence.org/Contents/LinuxWirelessCommands.htm](http://www.wirelessdefence.org/Contents/LinuxWirelessCommands.htm)

---

### Post by dxmosiris on 2007-07-08
great help and great tutorial website. I am running into a little issue. I am running WPA protection and I don't think that is supported by iwconfig. :( I have wpa supplicant but the "key" value is not accepted in ascii form. 

Unfortunately I am cursed with a broadcom chipset in which I am using Ndiswrapper with windows drivers so I can get full 54Mbps support.

I also bought a wg511t so I do have a card capable of running on native linux drivers.

Does iwconfig support ndis? Does it support wpa?

Ubuntu Feisty btw. Thanks for all of the help so far.

---

### Post by duphenix on 2007-08-21
> **Pugwash said:**
> If you have network manager, just stick "nm-applet &" in the startup file (but make sure its before the "exec /usr/local/bin/fluxbox.... " line). It works for me.

I had to add "gnome-keyring-daemon &" along with "nm-applet &" in order to get wifi with WEP to work and not constantly ask for the WEP key to be re-entered.

---

