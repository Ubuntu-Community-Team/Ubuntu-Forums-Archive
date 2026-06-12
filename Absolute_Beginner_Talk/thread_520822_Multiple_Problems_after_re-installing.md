---
title: "Multiple Problems after re-installing"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by reslider on 2007-08-08
The two problems I am Having are 
[LIST=1]
[*]When I login in gnome (ubunty edgy) it takes several minutes.
Then it shows a error on not loading gnome-settings-deamon.

"There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GNOME will still try to restart the Settings Daemon next time you log in."

This happend in 7.04, then I re-installed everything because I messed up my X configuration trying install my graphics card.
After re-installing 7.04 it still came up, but I decided to go back to 6.10 because I also could not get my wireless to work in 7.04

After doing a complete install to edgy I still get the pop up when I log into Ubuntu?

 

[*]I cant count how many time ive reinstalled Ubuntu but The last two installs Ive done the whole system seems really slow.

When I had 7.04 it seemed really fast and I really enjoyed it, then I did the reinstall because I messed up the x-configuration and after that it seemed really slow. (Opening windows and other programs) I thought if I switched to 6.06 It would fix it, but no luck still very slow.

Im just confused why it would be fast on one install and very slow on another install?

If anyone has any ideas that would be great,
                                    
Thanks Tyler

[/LIST]

---

### Post by overdrank on 2007-08-08
HI I did a quick search on that error and it appears to related to the network interface 
[http://ubuntuforums.org/showthread.php?t=520575&highlight=GNOME+Settings+Daemon](http://ubuntuforums.org/showthread.php?t=520575&highlight=GNOME+Settings+Daemon)
I have heard that ubuntu can be sluggish with a network issue. SO you might need to search that bug and see if you can find a solution. Good luck! :popcorn:

---

### Post by reslider on 2007-08-08
sorry im at work so this is not my exact interface, but I used one of the threads to help set it up so I know it is what mine looks like

> 
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 1
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key> [IMPORTANT: See "WPA-PSK key generation"] 

So I have the auto lo in there, I will try commenting out the IPv6 addresses in /etc/hosts when I get home.

Just curious why this problem would follow me from reinstalling 7.04 then going back to 6.10 which obviously would be a fresh install? When I do the re-install  I make sure that all the partitions get reformated, could it be somthing on my hda1 ( ubuntu is installed on hdb) that does not get erased when I would do a fresh install?

---

### Post by overdrank on 2007-08-08
> **reslider said:**
> sorry im at work so this is not my exact interface, but I used one of the threads to help set it up so I know it is what mine looks like



So I have the auto lo in there, I will try commenting out the IPv6 addresses in /etc/hosts when I get home.

Just curious why this problem would follow me from reinstalling 7.04 then going back to 6.10 which obviously would be a fresh install? When I do the re-install  I make sure that all the partitions get reformated, could it be somthing on my hda1 ( ubuntu is installed on hdb) that does not get erased when I would do a fresh install?

The only thing I can think of ( and I am no network person myself) is that the nic card you are using has issue in linux because of the drivers. :(

---

### Post by reslider on 2007-08-08
> **overdrank said:**
> The only thing I can think of ( and I am no network person myself) is that the nic card you are using has issue in linux because of the drivers. :(

Well I've been trying diffrent versions for a while so Ive done a lot of instalations of the three versions, 
    Started with 7.04  but the boot up took way too long, 
    so I went to 6.06 ( but I found out 6.10 used Firefox 2.0) 
    so I went to 6.10 but I was having having downloads fail when trying to install applications, so I wanted to give 7.04 a try again, still couldn't get wireless to work, also tried to install my graphics card and thats when I messed up my X configuration, so I reinstalled 7.04 *** and this is when I started having the problem with daemon. So I figured since I couldn't get wireless to work I would just go back to 6.10 and I would get rid of the Daemon Problem, well the first Time I loaded 6.10 it was still having problems.

But up untill  the point where I put the *** I did not have the problem and I had my wireless working on both 6.06 and 6.10. 

I did notice however, that right after grub loads it says something about PCI, but it goes way too fast for me to read anything, I'm assuming its my graphics card (I'm still trying to get that to work). It doesn't say anything about it when I type lspci so it is not noticing it's there, could this have anything to do with the slowness maybe? Or Daemon?

---

### Post by bobtom on 2007-08-08
I had that same problem when I installed Ubuntu(fiestyfawn) on my old Dell laptop (pIII @1gig).

After I tried installing Ubuntu several times(each time seemed different), I tried logging out and logging back in when I got that error message about the GNOME settings daemon to see if it could fix itself. (After all, it did say that when I logged back in later it would try to fix itself) Well guess what, it did fix itself! :) bt

---

### Post by reslider on 2007-08-09
So I erased XP off my main hardrive, and installed ubuntu 6.10 to it, and it is just as fast as it could be. and no more error, so I don't know if it was the re-install or the Hardrive that solved it, but It's really fast and I enjoy that. Thanks for the help, Tyler

---

### Post by overdrank on 2007-08-09
> **reslider said:**
> So I erased XP off my main hardrive, and installed ubuntu 6.10 to it, and it is just as fast as it could be. and no more error, so I don't know if it was the re-install or the Hardrive that solved it, but It's really fast and I enjoy that. Thanks for the help, Tyler

Glad to hear and good luck and enjoy! :popcorn:

---

