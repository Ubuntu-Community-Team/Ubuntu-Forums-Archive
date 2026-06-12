---
title: "eMac and iMac File Sharing with Ethernet Cable and Other Cable"
date: 2010-10-12
forum: Apple Hardware Users
---

### Post by corrytonapple on 2010-10-12
Hello All!
I was wondering how I could file share, or make the whole Hard Drive  (HDD) accessible to another computer. The two other computers I have are  a Toshiba Laptop with Ethernet and USB, and a iMac Intel with Firewire,  USB, and Ethernet. Putting these to use along with:

[LIST]
[*] Three Ethernet Cables
[/LIST]

[LIST]
[*] Two Printer Peripheral USB Cables
[/LIST]

[LIST]
[*] The Two Computers
[/LIST]

[LIST]
[*]A 2GB Flash Drive
[/LIST]
 That is all I can think of right now. I do not want to use CDs. In a way, I would like to do a network boot. So, how do I get the whole HDD visible to the others computers  (either/both) and be able to write to it? I want to put Xubuntu on it,  and earse the rest of the Hard Drive. The computers getting this are the  iMac G3s and the eMac G4. The eMac has 256MB RAM, 40GB HDD, and a 700MHz processor. Two iMacs have 128MB RAM, 40GB HDD, and a 600MHz Processor. The other iMac is the same as the rest but has a 500MHz processor. Thank you for the help.

---

### Post by jjex22 on 2010-10-12
sorry I got a bit confused, are you;
a)trying to use one or more of the computers as an external HDD
b) trying upgrade the old macs to xubuntu but keep the data on them
c) trying to set up a network between the three machines?

---

### Post by corrytonapple on 2010-10-12
I am trying to A) To use one or more of the computers as an external HDD. I want to take the HDDs in them, wipe them, and put Xubuntu on the eMac and Debian on the iMacs. They will probally have to be external to do that (or mounted on the OS X 10.05 or Ubuntu 10.04's desktop.

---

### Post by jjex22 on 2010-10-12
If you want to create an external Hdd from one or more of the Imacs,  external really is the only way to go with the emac. I am using one  myself and can confirm that changing the HDD is an absolute pain (and a  little frighting as you have to dive deep into things you didn't really  want to take apart.) and most importantly there isn't room for two 3.5  ide drives in there.

You can externalize your drive by purchasing  an inexpensive kit (10-20 bucks) to make the drive external. Judging by  your processor, your emac uses usb 1.x, so connecting the drive to  firewire is the best solution.

 - firewire is nearly as fast at data  transfers as usb2 and won't impede on the CPU unlike usb, and lets face  it with such old systems every little helps!  The downside to firewire  is that an ide firewire connector is harder to come by, so may cost 20%  more. Firewire also has associated security risks- if you connect 2  computers via firewire you have instant ram access - though on a home  unit this shouldn't be a problem, at work or public areas it is  always best to disable firewire ports. it would be up to you to weigh up  the options -remember usb2 enclosures will work with your emac, but  only at usb 1.x speeds. 

Also remember that open firmware on the  emac will boot from firewire and from your 2gb pen drive, but will not  boot from a usb hdd - so you would have to put your OS's on the internal  emac drive and use the external as a shared data drive if you get a usb  hdd enclosure.

The next option is to turn one of the imacs into a  server using a server edition of an OS, probably ubuntu as it's quick  and easy and you can use the same mini.iso to set up xubuntu and the  ubuntu server from your pen drive. this would enable you to use the imac  as a hdd for any computer on the network, create network accounts,  configure access for users, etc. 

 The big advantage to this is  you don't have to spend any money if you have network cables, (and it  seems you do), you don't have to open up the equally frightening imac,  and you still have the imac for the future. the downside is that if you  do not already use ftp, you will have to enable this, which is an  additional open port on your system (though not a major risk) and the  imac is not well suited to server life as the crt monitor is always  connected and on - really not a good energy saver!. you would also  probably want to keep an eye on ebay for cheap second hand ram floating  about (I spent only 5usd on ebay last month for 2 512mb's for my emac -  one to upgrade to 1gb ram and the other to keep as a spare!).

I  would recommend doing a mixture of the both - grabbing a cheap as dirt  second hand desktop of ebay, wacking in your i mac drive(s) as well as  the hdd that comes with it and running that as a server for your home  network. (to give you a price guide I spent $18.50 on a firewire  enclosure last year, and about 6 months ago I spent $25 on an old pc  with better processor, ram and hdd than an imac G3 -it even came with a  eybouard mouse, speakers and a 15" monitor that spends 2% of it's time  connected to the server, and 98% of it's time as a second monitor for my  emac). If you wanted to keep things in the mac family, you could look  into a cube or early mini mac (and firewire the other drive) or an old powermac, though these aren't as cheap!. Just remember that when buying an old comp to use as a server for  home  you don't need many resources and you definatetly won't be  needing gigs of ram and graphics cards etc, meaning you can get a real  bargin!

whichever you choose I'm glad there's someone else  keeping these old macs running along on linux (I also have tiger on my  emac, pretty much for itunes nowadays and its always a little depressing  booting back in!) I cannot recommend enough using the mini.iso - follow  directions from linuxopjemac:

[http://art.ubuntuforums.org/showthread.php?t=1454430](http://art.ubuntuforums.org/showthread.php?t=1454430)

it  takes almost the same time as a live cd install but you can choose  exaclty what you want on there as you go through and no need for cd's!  (i had to use
 boot usb0/disk@1:2,\\yaboot 
when i did it, and don't connect the usb stick to the usb on the keyboard - it has to be one of the usbs on the emac.

I  have also used this iso for my tangerine orange G3, I don't run the full  Xubuntu on these basic conputers - i do a basic install, add no extras  when you get to the list (ubuntu server, edubuntu, xubuntu etc) and  install the xfce4 desktop once in the base system.

If you have any further questions about running ubuntu on an emac just ask!

Quick imac/emac tips

when Ubuntu asks to gues your keymap, say no, then choose your region followed by macintosh  at the next screen.

once in XFCE4, right click with control+mouse click on the desktop and set a keyboard shortcut with the command

eject -T /dev/cdrom

and  when asked for the key command just press the eject button on the  desktop and voila! your cd eject button works again (well as it should  rather than shooting out and back in again)

---

### Post by corrytonapple on 2010-10-12
> **jjex22 said:**
> If you want to create an external Hdd from one or more of the Imacs,  external really is the only way to go with the emac. I am using one  myself and can confirm that changing the HDD is an absolute pain (and a  little frighting as you have to dive deep into things you didn't really  want to take apart.) and most importantly there isn't room for two 3.5  ide drives in there.

You can externalize your drive by purchasing  an inexpensive kit (10-20 bucks) to make the drive external. Judging by  your processor, your emac uses usb 1.x, so connecting the drive to  firewire is the best solution.
I do not have the money to get anything. These are computers I am either selling, and if I can't, they will be donated. Could I hook up the HDDs and have them accessible via ethernet?
> **jjex22 said:**
> The next option is to turn one of the imacs into a  server using a server edition of an OS, probably ubuntu as it's quick  and easy and you can use the same mini.iso to set up xubuntu and the  ubuntu server from your pen drive. this would enable you to use the imac  as a hdd for any computer on the network, create network accounts,  configure access for users, etc. 

So the mini ISO lets me choose which version of Ubuntu I want? If so, I am getting it! I will check out that link. Thank you for the help so far.

---

### Post by jjex22 on 2010-10-12
do you have a firewire cable?

If you do, connect it between the emac and the imac you want to use as a hdd. Then turn on your macs. When you turn on the imac to use as a hdd, hold down the 'T' button. this will tell the firmware in that mac that you want to use it as a slave drive and it will not load any OS, the symbol for firewire should appear like a screen saver and the other mac should detect it as a firewire drive (provided firewire is turned on - I think ubuntu does this by default, though i can't remember). note you will have to do this each time you turn it on and cannot connect it to your laptop unless your laptop has a 1394 port (pc for firewire) but it does keep the ethernet free for non dial up users.

---

### Post by corrytonapple on 2010-10-12
No firewire. Could I mount the HDD using ethernet by connecting the two computers via an ethernet cord in the ethernet ports and then going to **Places>Connect to Server?**

---

### Post by jjex22 on 2010-10-12
yes,

to do that we have to go back to my second post and use the target imac as a server.

firstly emacs and imacs have only one Ethernet card, so connecting them together without a router will mean you can only connect to the internet via dial up or airport. if this is how you will connect or they don't need to, then just plug a cable between them and begin setting up the server. If you plan to use ubuntu, the guide for server ed. is here
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

If you plan to connect via ethernet, then you need to use a router. connect the router to the internet as usual and connect both computers to the router via ethernet cables then set up your server as in the guides.

I havn't done it, but it should be possible to use the router to connect all three together with one imac as the dominant server to manage the network and one as a simple file server so that you can use both imac's drives. I can foresee this being a pain but once done you would be able to save on both imacs and access them from all three computers and wirelessly through your laptop if it is a wireless router?

---

### Post by jjex22 on 2010-10-13
Just thought I'd add if your planning on upping to 10.10 on these machines, best wait a month, got meerkat on there last night n as usual initial ppc release seems a little buggy..

---

