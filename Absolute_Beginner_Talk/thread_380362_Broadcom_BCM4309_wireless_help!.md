---
title: "Broadcom BCM4309 wireless help!"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Ozor Mox on 2007-03-09
Help! I've been trying to get wireless to work with my Broadcom wireless card for a while now and have still had no success.

I know I have the BCM4309 chipset from running the hardware list from the terminal, and according to the ndiswrapper page that means I have a Dell Wireless 1450 (802.11a/b/g) Dual-Band WLAN miniPCI Card, although my chipset applies to two other cards as well which I don't think are mine.

I have found the inf file (bcmwl5a.inf) from biginoz.free.fr/linux/ and downloaded it to my desktop and attempted to put it in to ndiswrapper using ndisgtk, but I get the following error:

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
modprobe config already contains alias directive

```

And in the interface it tells me:

bcmwl5a
Hardware present: No

Can anyone tell me what I'm doing wrong please?

---

### Post by Ek0nomik on 2007-03-09
[http://www.ubuntuforums.org/showthread.php?p=2268117&highlight=4309#post2268117](http://www.ubuntuforums.org/showthread.php?p=2268117&highlight=4309#post2268117)

Did you follow this How To?

---

### Post by Ozor Mox on 2007-03-09
Yes I have blacklisted my drivers and I am using the same file as the other poster, I must be missing another step that they took.

Thanks for the reply though.

---

### Post by Ek0nomik on 2007-03-09
What does ```
sudo ndiswrapper -l
``` display?

It says that your hardware isn't present?  Make sure you download the correct driver.  A lot of the drivers are called the same thing.  So just because you are using bcml5, doesn't mean you are actually using the CORRECT one.

---

### Post by lamalex on 2007-03-09
have you tried using the native driver? Ive got a 4311, Del 1470 which works well with the bcm43xx.

---

### Post by Ozor Mox on 2007-03-09
Ek0nomik:

sudo ndiswrapper -l displays:

```
Installed ndis drivers:
bcmwl5a invalid driver!

```

The ndiswrapper page tells me that bcmwl5a.inf is the correct driver for my chipset, but if there's another driver with the same name I'm not sure where to find it. The one I downloaded was the only one I could find on a search on the internet. Maybe someone has the correct inf file for this card?

lamalex:

As far as I could tell the default driver did not work. It listed the wireless device in the networking interface but I could not activate it and the hardware list listed it as "DISABLED".

---

### Post by Ozor Mox on 2007-03-09
Just for an update, I found the .sys file to go with the .inf file (bcmwl5 not bcmwl5a, I haven't found that one yet) and now it adds to ndiswrapper and sudo ndiswrapper -l tells me that the driver and hardware are both present, but I still get no wireless connection in the networking interface and basically can't do anything with my card.

Argh! :mad:

---

### Post by Ozor Mox on 2007-03-12
Ok I found that the problem was on the command sudo modprobe ndiswrapper, where the error "Invalid argument" was appearing. After trying every combination of unzipped EXE, INF and SYS files I could possibly find and getting no result, I searched for some answers and did apt-get on ndiswrapper-utils-1.18 (I think it was) and then the modprobe command worked! I now have valid drivers and hardware and ndiswrapper is active! Yahoo! So I check the networking interface and wireless network has reappeared! I click on it, enter information, and enable and...

Nothing. If I unplug the ethernet cable and check the networks by clicking on the two computers icon, a choice of ethernet or the feedback loop one. Maybe a reboot...

Nothing. ARGH! I'm back to where I started with the native Broadcom driver! Ubuntu knows I have a wireless network card but can't use it!

Is the BCM4309 chip a lost cause, must I return to the dark side? My laptop loses a lot of its usefulness without the wireless card functioning.

---

### Post by clooch on 2007-03-13
I hope this thread helps, it is the only thing that plays well with my broadcom 4306.

[http://ubuntuforums.org/showpost.php?p=1189151&postcount=332](http://ubuntuforums.org/showpost.php?p=1189151&postcount=332)

I realize the cards are different but it is worth a shot.

cheers

---

### Post by Ozor Mox on 2007-03-13
Thanks for the link clooch. I have two more ndiswrapper related things to try, first using bcmwl5.inf instead of bcmwl5a.inf, and second following [these  instructions](http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606) which some people seem to have had success with. If neither of these solutions will work then I will try your link using bcm43xx-fwcutter, which will be my last attempt, after that I'm out of ideas, other than possibly upgrading to the less stable Feisty Fawn before release.

I'm really disappointed about this as I'm loving Ubuntu and would very much like to keep it as my desktop, and I don't blame Linux at all, I blame Broadcom. I will report back on my results. If anyone has any further suggestions please don't hesitate to post them.

---

### Post by Ozor Mox on 2007-03-14
Wow! I just got wireless to work! I'll try to provide some useful information in case anyone else has some trouble with the Broadcom BCM4309.

Basically, it seems I was barking up the wrong tree with ndiswrapper. I tried everything with that module and could not get it to work with any combination of files or commands. Then I went back to the native driver bcm43xx by un-blacklisting it and basically following the instructions on [this page](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy). Although the important thing for me was that running the script:

```
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```

that finds and downloads the correct driver did not work. It did some stuff in the terminal but I still had no wireless available. Then I followed this:

```
sudo bcm43xx-fwcutter -w /lib/firmware/2.6.17-11-386 bcmwl5.sys
```

using the driver file I had downloaded for ndiswrapper, rebooted, and it worked perfectly! eth1 appeared in my networks list and I entered my SSID and was connected! I still have to get WPA to work though, hopefully this won't be too hard.

Also I downloaded network-manager-gnome and it currently only displays my wired network, is there a reason why this isn't displaying my wireless network too?

Anyway my thanks to those who replied in this thread and I hope this helps anyone else with my annoying Broadcom BCM4309 chipset or a Dell Latitude D600 laptop.

---

