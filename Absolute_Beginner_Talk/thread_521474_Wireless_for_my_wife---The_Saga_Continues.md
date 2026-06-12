---
title: "Wireless for my wife---The Saga Continues"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by yogo on 2007-08-09
BTW thanks to all those for the marriage counseling yesterday:)

I have a fresh install of Ubuntu and it seems like it will work out fine, the biggest hurdle is getting the wireless going.

I have been reading thru a tutorial about getting the ralink drivers going.

I have an Edimax EW 7128g, I believe that is the right #, it is the pci one with the cable antenna.

My Ubuntu sees the router which is a Buffalo WHR HP G-54 but will not connect

The tutorial I have been reading is [here]("http://ubuntuforums.org/showthread.php?t=400236&page=2")

I am stuck on step 4, I have put the download file onto the Ubuntu of my wife from my pc via a memory card.
[I]
Step 4 If you have no internet access on the Linux install already, you will need to download this file from another PC (or from Windows) and then copy it to /usr/src. Just copy the file to a flash disk or something, boot your Linux install and copy the file to your home directory. Then do the following in a terminal:
Code:

sudo cp ~/rt73-cvs-daily.tar.gz /usr/src[/I]


However I am having troubles with getting it into the /usr/scr folder. I can not copy or make a folder there and when I run the command I get an invalid cp option.

Two things at this point, number one I am not sure that this package is what I need as it appears to be for someone that has a wireless USB adapter and I have a pci card. Therefore point me to the right place for the correct pci drivers PLEASE and number two, why am I not getting this into the /usr/src directory?

All help is appreciated, even the marriage counseling!

---

### Post by splintercellguy on 2007-08-09
Can you post the output of lspci so I can determine your chipset? If the Linux native driver cannot handle your wireless, then take a peek at this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by nikef on 2007-08-09
> **yogo said:**
> BTW thanks to all those for the marriage counseling yesterday:)

I have a fresh install of Ubuntu and it seems like it will work out fine, the biggest hurdle is getting the wireless going.

I have been reading thru a tutorial about getting the ralink drivers going.

I have an Edimax EW 7128g, I believe that is the right #, it is the pci one with the cable antenna.

My Ubuntu sees the router which is a Buffalo WHR HP G-54 but will not connect

The tutorial I have been reading is [here]("http://ubuntuforums.org/showthread.php?t=400236&page=2")

I am stuck on step 4, I have put the download file onto the Ubuntu of my wife from my pc via a memory card.
[I]
Step 4 If you have no internet access on the Linux install already, you will need to download this file from another PC (or from Windows) and then copy it to /usr/src. Just copy the file to a flash disk or something, boot your Linux install and copy the file to your home directory. Then do the following in a terminal:
Code:

sudo cp ~/rt73-cvs-daily.tar.gz /usr/src[/I]


However I am having troubles with getting it into the /usr/scr folder. I can not copy or make a folder there and when I run the command I get an invalid cp option.

Two things at this point, number one I am not sure that this package is what I need as it appears to be for someone that has a wireless USB adapter and I have a pci card. Therefore point me to the right place for the correct pci drivers PLEASE and number two, why am I not getting this into the /usr/src directory?

All help is appreciated, even the marriage counseling!


hi,i am having the same problem,except i am using a belkin adaptor

spent 2 days  trying to do step 4 ,but no joy :confused:

---

### Post by splintercellguy on 2007-08-09
Can you create a new thread with the output of lspci?

---

### Post by yogo on 2007-08-09
01:88.0 Network Controller: Ralink RT2561/RT61 802.11g PCI

I also found this[ link]("http://www.cyberciti.biz/tips/linux-install-and-configure-dlink-dwl-g-520-wireless-lan-pci-card.html"), seems like a good place to start but is for wrong card

@Splintercellguy, Found this from your above link but the driver file is missing and there is no download

#
Card: Edimax EW-7128g

    *
      Chipset: RaLink RT2500
    *
      pciid: 1814:0201 (rev 1)
    *
      Driver: Ndiswrapper 0.11; .inf and .sys for Win2K from [ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip](ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip)
    *
      Other: Slackware 10.0. Hint: modify /etc/rc.d/rc.inet1 and replace instances of &#8220;eth&#8221; with &#8220;wlan&#8221;; also modify /etc/rc.d/rc.modules to load ndiswrapper. Running flawlessly for one day so far. Using WEP.

---

### Post by Hospadar on 2007-08-09
Hellos!

Well first off, I suspect for your cp issue that one of two things is the problem either: /usr/src doesn't exist (probably not the case) or your drivers arn't located where you think they are.  for that command to work, your drivers would need to be in your home folder (/home/your_username)

If you don't know, ~ is a shortcut for your home folder, for example for me, "cd ~" and "cd /home/luke" do the same thing.  So first save make sure the driver file is saved to your home folder.  If it's on your desktop, go to Places->Home Folder and then drag it into there.

Second, let's make sure your /usr/src exists do ```
cd /usr
ls
```if you don't see the src folder, create it with ```
sudo mkdir src
```Also, I think you may be using the wrong drivers (although the guide you are looking at may yet be useful, they are probably pretty similar instructions)

have a look [here]("http://ubuntuforums.org/showthread.php?t=156075") It looks a little old, so you may have to substitute some of the version numbers in the directions.

Also, you are going to need the build-essential package which has the tools needed to build software.  you'll have to download this manually if you can't get an internet connection.  go to [http://packages.ubuntu.com/feisty/devel/build-essential](http://packages.ubuntu.com/feisty/devel/build-essential) and manually download the .deb for your version of ubuntu (i86, x64 etc) then go download all the dependancies manually, save these all to a flash drive or whatever, and then install them manually.  you can just double click them once you get them on the machine (you'll need to install the dependancies first). If it complains about some dependancies you don't have, go back to the package site and grab em.

Alternatively, if you can temporarily plug yourself into an internet connection, this is waaay easier, just do a ```
sudo apt-get install build-essential
``` in the terminal.

---

### Post by yogo on 2007-08-09
Thanks Hospadar, that was very helpful.

Yes my /usr/src directory exists.

Where I am at right now is I have Ndiswrapper and utilities installed with the user interface.

I downloaded the  install which is an exe,(for my pci card) and have not put wine on her pc yet so I am wondering if I just install it on mine and copy the inf file which the NDIS gui will install from?


TIA

---

### Post by yogo on 2007-08-09
I can not install the Ralink configuration on my pc, I assume because the card is not installed there. How can I get the inf file that is needed to run NDISWRAPPER?  > select inf to add the driver.


Also if I did install wine, could I just run the Ralink utility as it worked well on Windows.

Just wanna get connected!

---

### Post by anewguy on 2007-08-09
If the file containing the drivers is an exe, you can try right-clicking on it and then selecting "open with achive manage" and see if it will open it.  Depending on the exe, sometimes this works.  If it does click through the files/folders that show until you find the files you need for your driver installation (usually a minimum of .inf and .sys) and extract only those to your desktop (you can extract a single file at a time).

If that doesn't work, then you will either need to install WINE so you can execute and unpack the exe, or perhaps find a Windows machine and extract there and then copy the files so you can load them to your problem system.

Please post back so we know where to go from here.:)

---

### Post by yogo on 2007-08-09
Thanks anewguy,


I was thinking along those lines to install it on my windows box and pick the files from there. 

I will try the archive manger as I did not know that that sometimes works.

How many files are necessary? is the inf file enough or are there supporting files.

Is wine on the Live CD otherwise I will have to download it and copy it over to the other pc.

Just go back in so I will be updating here.

Thanks

---

### Post by yogo on 2007-08-09
Ok I am on windows and have copied the Ralink application to a memory card to transfer to other pc, do I just run the INF with NDISwrapper? This comes with it's own configuration toll but I assume that ndiswrapper is the way to go on Ubuntu.


I'll post back if I have errors.

TIA

---

### Post by anewguy on 2007-08-09
Sorry to take so long, but I've been off my PC until now.  You will need the .inf and the corresponding .sys file to use in ndiswrapper.

Please post back with the results - I have someone else I'm trying to help get their Ra2500 working.:)

---

### Post by yogo on 2007-08-09
I am not sure but it seems like I am going backwards, I installed the .inf but now the Ubuntu box does not even see the router, before it correctly id'ed it but I just could not connect.

when I use iwconfig, I get     lo no wireless extensions    ?

Thanks

---

### Post by anewguy on 2007-08-09
I forgot one other thing I saw somewhere when I was researching this before.  Someone claims that if you put the ra60.bin in your /etc/drivers folder that it will work that way.  I can't say as I'm just trying to get this working for somebody else.  Also, did you find this website:

[http://ubuntuforums.org/showthread.php?t=519280&highlight=rt2500+how+to]("http://ubuntuforums.org/showthread.php?t=519280&highlight=rt2500+how+to")

:)

---

### Post by yogo on 2007-08-09
Thanks for that link it looks helpful, they have the same drivers

---

### Post by yogo on 2007-08-09
I don't have a drivers folder so I will make one and drop that in it, I am not sure where the network manager is putting the driver?


I can not find the ra60.bin file

PS since restarting I can now see the router again.

---

### Post by yogo on 2007-08-09
Ubuntu thinks I am connected and I have a full five bars and it says connection 100% but I still can not get internet?

This is when I set it to roam.

---

### Post by yogo on 2007-08-09
When I use Network tools, it says unknown ra0 device, it does show that it is connected but yet I am not connected. I can not ping a web site. 

Under Connection Information > Active Connection information it has my driver as rt61 and it has my hardware address, the connection is set to roam and that may be why ip addy and everything elso has zeros by them.

This has got to be something so minot, they can see each other, just not talk!

---

### Post by anewguy on 2007-08-09
I believe there was something in the info on the post I mentioned that says you have to set the sessionid, etc., while not connected and the link is down.  There were some pretty detailed instructions on some of that in there.  Perhaps it might be helpful to revisit that sight and check the things about setting session id, etc..   Please post back to let us know how it is going!:)

---

### Post by yogo on 2007-08-10
> **anewguy said:**
> I believe there was something in the info on the post I mentioned that says you have to set the sessionid, etc., while not connected and the link is down.  There were some pretty detailed instructions on some of that in there.  Perhaps it might be helpful to revisit that sight and check the things about setting session id, etc..   Please post back to let us know how it is going!:)


Can you post the link again as I am not sure which one you mean.


TIA   :)

---

### Post by anewguy on 2007-08-10
It's in the #14 in this message thread.:)

---

### Post by yogo on 2007-08-10
A anewguy,

That is the link I thought you were talking about. what confused me was this what you wrote *while not connected and the link is down.* since it was part of this formum and the link worked I thought you may have meant another one.

---

### Post by anewguy on 2007-08-10
Sorry about that - I was doing a dumb thing and trying to answer more than one post at a time, so I had my mind a little elsewhere at the time.  I should know better at my age!:)

Have you had any luck?  If not, what types of problems are you still having?

---

### Post by yogo on 2007-08-11
anewguy,

Thanks for helping, I did get it going but it is somewhat temperamental, maybe because it is on my wife's computer.

here is a [thread]("http://ubuntuforums.org/showthread.php?t=522386&page=3") that explains it, right now i am on it several rooms away, about 70 feet.

It never drops but getting it to start when I want is much like getting my wife to start.

---

### Post by anewguy on 2007-08-13
You know, I'm not sure if it will help the connection from being tempermental, but I have seen other posts on using these drivers, and most of them mention adding a blacklist entry for the driver supplied by the Ubuntu installation.  Since I don't use that card, I don't know what it is called, but it might be rt2500, RT2500, RA2500 or ra2500.  Maybe a query post on this forum will result in an answer for that.  If you don't know how to blacklist, just post back and we'll walk you through it.:)

---

### Post by yogo on 2007-08-13
> **anewguy said:**
> You know, I'm not sure if it will help the connection from being tempermental, but I have seen other posts on using these drivers, and most of them mention adding a blacklist entry for the driver supplied by the Ubuntu installation.  Since I don't use that card, I don't know what it is called, but it might be rt2500, RT2500, RA2500 or ra2500.  Maybe a query post on this forum will result in an answer for that.  If you don't know how to blacklist, just post back and we'll walk you through it.:)

That is one of the questions I was going to post, I did blacklist the bcm43xx because it is a competing driver, but when I looked at where the rt61 driver is there are about ten other drivers rt2500, RT2500, RA250 etc. What I was thinking was why are these not competing? I guess they are, I have not seen that post but I can look for all these drivers and blacklist them individually.

Right now the wireless has been up to a static ip all weekend long, however my sys tray applet is gone and Network manager is also gone as well as user manager. I nixed these things up, I had trouble with the Gnome Setting Daemon, I think that happened when I removed the Ubuntu desktop but have since reinstalled it, I also tried to reinstall the network manager but got an error so I will have to investigate these things.

BTW, I am running xfce4 desktop and I have no errors like the hang on startup with the Gnome environment.

One last thing, I forgot where the blacklist is located, if you could poit to the location it will make blacklisting easier.


TIA

---

### Post by anewguy on 2007-08-21
Jeez I'm sorry - I've been gone for a while.

(1) The location of the blacklist file is /etc/modprobe.d/, so to edit it you can do the following:
-
- sudo gedit /etc/modprobe.d/blacklist
-
Just go to the end of the file and add the new blacklist item.  I believe you only need to blacklist the rt2500, RT2500 or ra2500 - you could just start with rt2500 and see what happens.

(2) I'm not sure, but I think if you delete the gnome desktop, you delete everything associated with it as well.  So, when you reinstalled the gnome desktop did you also go back through synaptic package manager and reinstall network-manager and network-manager gnome?

---

### Post by anewguy on 2007-08-22
And of course I forgot one other thing for you;

If the network manager or network manager gnome applets aren't showing, open a terminal window and type  "nm-applet"  that should get them going again.

---

