---
title: "Will wpa work in dapper with a dell 1370 integrated wireless card on a dell 6000?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by solarwind on 2006-05-30
Hello,
I am not a beginner but could not find a proper place for this question.

Will wpa encryption work in dapper with a dell 1370 integrated wireless card on a dell 6000? Is wpa encryption wireless-card-specific or if I want to install support for it, is the package the same for any card?

---

### Post by solarwind on 2006-05-30
Can someone please answer me? Thanks!

---

### Post by jgoguen on 2006-05-30
Install WPA Supplicant and the GUI tool
```
sudo apt-get install wpasupplicant wpagui
``` 
That should let you use WPA in all it's varieties.  You'll need to edit three files:

/etc/default/wpasupplicant:
> ENABLED=1
OPTIONS="-w -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf" Replace madwifi with your driver (madwifi, ndiswrapper, etc.), ath0 with your interface name.

/etc/wpa_supplicant.conf:
> ctrl_interface=/var/run/wpa_supplicant      # Leave this as is
ctrl_interface_group=112     # The GID of the group allowed to use the GUI tool
update_config=1     # This file is only updated if wpa_supplicant is started 
                                # with this set to 1 and the user is in the 
                                # ctrl_interface_group

# Define a network using WPA-PSK or WPA2-PSK
network={
        ssid="secure_ssid"  # Enter the SSID of the network here
        scan_ssid=1
        psk="mysupersecretkey"     # Enter the network key here
        proto=RSN     # Leave this as is for WPA2-PSK, remove for WPA1
        key_mgmt=WPA-PSK     # Tell wpa_supplicant to use WPA-PSK or WPA2-PSK
        pairwise=CCMP     # Use TKIP+AES (change to TKIP for only TKIP or for WPA1)
}

# Define a network with no encryption (no WPA, no WEP, etc)
network={
        ssid="open_ssid"     # The SSID
        scan_ssid=1
        key_mgmt=NONE     # Tell wpa_supplicant not to authenticate to this network
} 
If you aren't sure what setting you're using (WPA1, WPA2, TKIP+AES or just TKIP) check the access point configuration.  Otherwise ask your network administrator and explain you need the settings so you can use wireless with your Linux laptop.

/etc/network/interfaces:
Find the section started by "auto <if_name>" where if_name is the name of your wireless interface (mine is ath0) and add these lines:
> auto ath0
iface ath0 inet dhcp
pre-up /sbin/wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant If "iface ath0..." is elsewhere, comment it out with a pound sign (#) at the start of the line.  
If wpa_supplicant isn't in /sbin/ you need to change /sbin/wpa_supplicant to be the full path to wpa_supplicant (maybe /usr/sbin/wpa_supplicant or /usr/local/sbin/wpa_supplicant).  You can find this with the command
```
which wpa_supplicant
``` which will give you the full path to the wpa_supplicant binary.  

This should get you basically up and running.  You can tweak these settings with the GUI tool (run wpa_gui from the command line), just remember to restart wpa_supplicant (I restarted networking: /etc/init.d/networking restart) before launching the GUI.

---

### Post by solarwind on 2006-05-31
Thanks! This is really helpful. I haven't done it yet but it looks like it'll work fine. But using this configuration, will my dell 1370 card automatically acquire an IP address using my router's DHCP? This thread should be stickied!

---

### Post by jgoguen on 2006-05-31
The " iface ath0 inet dhcp" line tells the interface to ask DHCP for its information.  It works just fine on mine, this is actually a copy-and-paste of my configuration with my PSK and SSIDs removed :)

---

### Post by solarwind on 2006-06-06
root@vg-laptop:/etc/default# ls | grep wpa
--as we can see, there is no file called /etc/default/wpasupplicant-- what's going on?

also, none of the three files you mentionned existed.



also, when I run wpa_gui, I keep getting this to stdout:

root@vg-laptop:/etc/network# wpa_gui
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Failed to open control connection to wpa_supplicant.
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect

---

### Post by jgoguen on 2006-06-06
Sorry, I forgot to mention that.  Just create the files.  It's strange that /etc/network/interfaces isn't there though, that file is fairly important.  I have no idea what package would provide it either, it was just there on my default installation.  Try creating the two WPA Supplicant files and double check that /etc/network/interfaces isn't there.

---

### Post by solarwind on 2006-06-06
Sorry, my bad, thanks for your reply. /etc/network/interfaces is there. I forgot about that. I should know. I've been using Linux for years. 

But... why do I get those errors when trying to use wpa_gui?

---

### Post by jgoguen on 2006-06-06
If you haven't rebooted, restart networking after plugging in your wireless card (or turning it on if it's internal):
```
sudo /etc/init.d/networking restart
```
and the changes you made will cause this init script to load wpa_supplicant when the wireless interface is brought up.  Once that's done, wpa_gui should work fine.

---

### Post by uzi09 on 2006-06-06
i'm a bit of a newbie and probably in no postition to really give any advice, but you might want to check this out:

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

and its wiki....
[https://wiki.ubuntu.com/NetworkManager?highlight=%28NetworkManager%29](https://wiki.ubuntu.com/NetworkManager?highlight=%28NetworkManager%29)

---

### Post by solarwind on 2006-06-06
Thanks, all, I got it working. Turns out that I have a dell 1370 card and the bcm43xx firmware does not work with it well (even though it's a right chipset and it's supposed to work, it does not). I completely removed the bcm43xx drivers and such and installed ndiswrapper and friends. I used my windows driver for this card (bcmwl5.inf and bemwl5.sys) I installed networkmanager and gnome applet netowrk manager (thanks uzi09) I then reinstalled wpasupplicant. Everything was automatic from there (damn broadcom and their stupid firmware!!) 

Thanks everyone! My problem was solved. Maybe I should make a how-to... or is there one already for a dell 1370 card (which is a common card)?

---

### Post by jgoguen on 2006-06-06
Take a look around...if you can't find a How-To, it'd be a good one to have.

---

