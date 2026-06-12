---
title: "Wireless (take 2)"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Quickened on 2007-04-26
Well i had originally given up but i am back with some new and different questions. I have done searches and read various documentation yet i still am hoping to find an answer.

I am running NetGear MA111 which isnt picked up by ubuntu. Now there is a document that contained some messing around to do that i was tampering with when i had edgy installed. I have since moved over to Fiesty.

On another forum someone suggested NDISWrapper.

I did a search on it and came up with [this link]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,29/id,list_m-n/")

> #
Card: NETGEAR MA111v1 802.11b Wireless USB2.0 Adapter

    *
      Chipset: Prism2/2.5/3
    *
      usbid: 0846:4110 Distribution: Debian sarge, kernel 2.6.8.1, ndiswrapper 0.12rc3
    *
      Driver: <a href=”ftp://downloads.netgear.com/files/ma111_CD_v2.0.zip“>v2.0</a> from the netgear website. Version: NETGEAR,08/11/2003, 3.0.8
    *
      Other: Works well with my ad-hoc WLAN setup.



Listed as number 7 it sounds like something that is right up my alley. But since i cant connect to the internet via Ubuntu i have no way of getting this on. Can i download it to a disk and then somehow run it from there?


Secondly i have heard of blacklisting on here before. Now i havent done super extensive searching but i did seem to find one person using a NetGearMA311 that used blacklisting somehow to fix their problem which seemed similar to mine. I wrote down the terminal and directions but i thought i would ask so i dont accidently screw something up that will cause problems in the future.

This is what i wrote down

```
gksu gedit /etc/modprobe.d/blacklist
```

which evidently opens up a file where i would go straight to the end and add

```
prism2
prism2_pci
hostap
hostap_pci
```

Its a different netGear but i figured "hey what the heck". I'd do about anything to get this working aside from buying a new card (budget is tight)


I hope this all makes sense because i am having trouble understanding this all as i am a newbie :)

Thanks for all time, patience and consideration and help. It means alot

---

### Post by gilda on 2007-04-26
This article on ubuntuguide may help you

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

Specifically read the section on " How to install Windows Wireless Drivers (Ndiswrapper) "


Cited to be supported on the Ndiswrapper list of supported hardware.

---

### Post by Quickened on 2007-04-27
Ah ok! Thanks for that link :)

I guess my question would lie

> sudo apt-get install ndiswrapper-utils-1.8
**sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf**
sudo ndiswrapper -l
sudo modprobe ndiswrapper

In the bolded part. I am not exactly sure what i would be putting for the location of the driver/mydriver. Is this something that i am installing myself off of the netgear disk? Can i put it anywhere or should there be a specific location?

---

### Post by Quickened on 2007-04-27
Actually nevermind i found a place to download the driver from on a NDISwrapper website. So i do have that. Would i just put the MA111 folder on the desktop to make it the easiest?

---

