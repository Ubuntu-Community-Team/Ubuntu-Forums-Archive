---
title: "beginner needs mad help"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by dckat1 on 2007-01-20
i currently have ubuntu running on a compaq presario laptop and have it connected to the internet wirelessly.  i also have a imac running mac os X connected directly to the wireless router.  this is a home network.  i was wondering how i could connect to the mac using my network and is it possible that i could also print from the laptop with a printer connected to the mac and access files connected to the mac with an external hard drive?  please help!!!

dckat1

---

### Post by poningru on 2007-01-20
> **dckat1 said:**
>  i was wondering how i could connect to the mac using my network
please elaborate how you want to connect and what the purpose of this 'connection' will be.
>  and is it possible that i could also print from the laptop with a printer connected to the mac
Take a look at the paragraph [http://members.cox.net/18james/osx_printer_sharing.html](http://members.cox.net/18james/osx_printer_sharing.html) under 'lpd' starting with 'To share a printer on the Mac across an ethernet network, in System Preferences click Sha'
that tells you how to turn on the mac printer sharing.
now in your laptop go to system->admin->printer
add new printer-> check the network printer-> and choose Unix Printer(lpd) -> just put in the mac's ip address in host. now you should be able to print with this printer.

>  and access files connected to the mac with an external hard drive?  please help!!!

dckat1
first go here: [http://mactechnotes.blogspot.com/2005/09/mac-os-x-as-nfs-server.html](http://mactechnotes.blogspot.com/2005/09/mac-os-x-as-nfs-server.html) to setup a nfs-server on your mac for that external hard drive.
now [https://help.ubuntu.com/community/SettingUpNFSHowTo#head-154936a06049932eb7ec96bc72b8fc2b993603a2](https://help.ubuntu.com/community/SettingUpNFSHowTo#head-154936a06049932eb7ec96bc72b8fc2b993603a2)
to setup mount nfs in ubuntu. let me know if something isnt clear, or you need help.

---

