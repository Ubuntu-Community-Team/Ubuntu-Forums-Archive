---
title: "Just did Ubuntu Updates, now logging in takes 10 mins"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Ice Dragon on 2007-07-02
So I just installed all the Ubuntu updates and then restarted the computer as it asked me to do. Now whenever I log in with my user name and password the screen freezes for like 10 mins or so before it finally plays the ubuntu music and logs me in.

When I finally get in I see an error message, something about the Setting Daemon not being loaded right and GNOME would try to load it again next time. I do get my settings to come up (desktop wallpaper, theme color, etc..) so im not sure what it means.

Why does this happen from an update? I havent installed anything that doesnt come on the latest ubuntu CD and the official updates?

Thanks for help in advance.

---

### Post by ndefontenay on 2007-07-03
Maybe you can check your logs in /var directory.

You might have some good indications on what's going on.

Feel free to post them here.

You are not having much answer because there's no way for anyone to get a clue about what's going on so far.

Getting your hand on logs and post them here would help us solve your problem and you would have more input.

---

### Post by ndefontenay on 2007-07-03
Hi.

Maybe your update has screw up some configuration settings.

Can you try this:

```
dpkg-reconfigure xorg-server
```

---

### Post by Ocxic on 2007-07-03
I've acctually had this happen to me, not for such a long period of time, but it has happend, never really did figure out why, and it's not common for me.. I'm gonna keep an eye on this thread, to see if there may be any corrilation.

---

### Post by Ice Dragon on 2007-07-03
root@archmage-laptop:/# dpkg-reconfigure xorg-server
Package `xorg-server' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xorg-server is not installed

thats what it said when i typed in the command you listed below, i dont think that fixed anything.

> **ndefontenay said:**
> Hi.

Maybe your update has screw up some configuration settings.

Can you try this:

```
dpkg-reconfigure xorg-server
```

---

### Post by NeoLithium on 2007-07-03
I think it would be best to try to get a hold of your logs, as well, check out your /home/USERNAME/.xsession-errors to see if anything is there.  Reconfiguring the xserver should be a more last resort. (It's  sudo dpkg-reconfigure xserver-xorg  though) if you want to try.

---

### Post by Ice Dragon on 2007-07-03
> **ndefontenay said:**
> Maybe you can check your logs in /var directory.

You might have some good indications on what's going on.

Feel free to post them here.

You are not having much answer because there's no way for anyone to get a clue about what's going on so far.

Getting your hand on logs and post them here would help us solve your problem and you would have more input.

Im not really sure what logs in var to post, but this one seemed relivant, its from var/daemon.log

root@archmage-laptop:/var/log# cat daemon.log
Jul  2 17:01:27 archmage-laptop init: tty4 main process (4326) killed by TERM signal
Jul  2 17:01:27 archmage-laptop init: tty5 main process (4327) killed by TERM signal
Jul  2 17:01:27 archmage-laptop init: tty3 main process (4332) killed by TERM signal
Jul  2 17:01:27 archmage-laptop init: tty1 main process (4333) killed by TERM signal
Jul  2 17:01:27 archmage-laptop init: tty6 main process (4334) killed by TERM signal
Jul  2 17:01:27 archmage-laptop init: tty2 main process (4329) killed by TERM signal
Jul  2 17:02:44 archmage-laptop NetworkManager: <information>^Istarting... 
Jul  2 17:02:44 archmage-laptop firmware_helper[4874]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:00.0' with driver '(unknown)'
Jul  2 17:02:44 archmage-laptop avahi-daemon[4880]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Jul  2 17:02:44 archmage-laptop avahi-daemon[4880]: Successfully dropped root privileges.
Jul  2 17:02:44 archmage-laptop avahi-daemon[4880]: avahi-daemon 0.6.17 starting up.
Jul  2 17:02:44 archmage-laptop avahi-daemon[4880]: Successfully called chroot().
Jul  2 17:02:44 archmage-laptop avahi-daemon[4880]: Successfully dropped remaining capabilities.
Jul  2 17:02:44 archmage-laptop avahi-daemon[4880]: No service found in /etc/avahi/services.
Jul  2 17:02:44 archmage-laptop avahi-daemon[4880]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.64.
Jul  2 17:02:44 archmage-laptop avahi-daemon[4880]: New relevant interface eth0.IPv4 for mDNS.
Jul  2 17:02:44 archmage-laptop avahi-daemon[4880]: Network interface enumeration completed.
Jul  2 17:02:44 archmage-laptop avahi-daemon[4880]: Registering new address record for fe80::216:d4ff:fed3:eb99 on eth0.*.
Jul  2 17:02:44 archmage-laptop avahi-daemon[4880]: Registering new address record for 192.168.1.64 on eth0.IPv4.
Jul  2 17:02:44 archmage-laptop avahi-daemon[4880]: Registering HINFO record with values 'I686'/'LINUX'.
Jul  2 17:02:45 archmage-laptop avahi-daemon[4880]: Server startup complete. Host name is archmage-laptop.local. Local service cookie is 1625979490.
Jul  2 17:03:07 archmage-laptop hcid[5136]: Bluetooth HCI daemon
Jul  2 17:03:07 archmage-laptop hcid[5136]: Starting SDP server
Jul  2 17:03:07 archmage-laptop NetworkManager: <debug info>^I[1183410187.873634] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jul  2 17:07:59 archmage-laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jul  2 17:07:59 archmage-laptop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jul  2 18:11:27 archmage-laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jul  2 18:11:27 archmage-laptop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jul  2 21:03:59 archmage-laptop NetworkManager: <information>^Istarting... 
Jul  2 21:03:59 archmage-laptop firmware_helper[5009]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:00.0' with driver '(unknown)'
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: Successfully dropped root privileges.
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: avahi-daemon 0.6.17 starting up.
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: Successfully called chroot().
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: Successfully dropped remaining capabilities.
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: No service found in /etc/avahi/services.
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.64.
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: New relevant interface eth0.IPv4 for mDNS.
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: Network interface enumeration completed.
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: Registering new address record for fe80::216:d4ff:fed3:eb99 on eth0.*.
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: Registering new address record for 192.168.1.64 on eth0.IPv4.
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: Registering HINFO record with values 'I686'/'LINUX'.
Jul  2 21:03:59 archmage-laptop avahi-daemon[5015]: Server startup complete. Host name is archmage-laptop.local. Local service cookie is 3190978228.
Jul  2 21:04:22 archmage-laptop hcid[5328]: Bluetooth HCI daemon
Jul  2 21:04:22 archmage-laptop hcid[5328]: Starting SDP server
Jul  2 21:04:22 archmage-laptop NetworkManager: <debug info>^I[1183424662.687137] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jul  2 21:08:33 archmage-laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jul  2 21:08:33 archmage-laptop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jul  2 21:29:22 archmage-laptop gdm[5078]: Root login disallowed on display ':0'
Jul  2 21:29:39 archmage-laptop gdm[5078]: Root login disallowed on display ':0'
Jul  2 21:34:40 archmage-laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jul  2 21:34:40 archmage-laptop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jul  2 22:51:37 archmage-laptop gdm[8137]: Couldn't authenticate user
root@archmage-laptop:/var/log#

---

### Post by sweetthdevil on 2007-07-27
Did you manage to find a solution? I am having exactly the same issue!!

---

### Post by bravemosquito on 2007-07-28
I've got this problem again today after updates (approx. 175MB of size, the box wasn't updated a known period of time)... It dissapeared a months ago but now it's back again :confused:

---

### Post by dasunst3r on 2007-07-28
I remembered this happening to me during my Edgy -> Feisty upgrade.  I had to back up my home directory, delete all the dot files (the files that started with a '.'), and reconfigure everything that had to do with GNOME.  I speculate that the user preferences were broken.

By the way: if you do this procedure, you can restore .pidgin, .mozilla, and other stuff like that once you're finished.

---

