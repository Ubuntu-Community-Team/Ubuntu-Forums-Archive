---
title: "Palm Centro sync with Gutsy"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by mmtowns on 2008-04-09
I recently bought a Palm Centro and wanted to sync my calendar and contacts with Evolution.  I've had some success, so I thought I'd share it with the forum.

First, I started out by using this [link]("https://help.ubuntu.com/community/PortableDevices/PalmOS").  
From this website, I gathered that I needed to go to System - Preferences - PalmOS Devices.

It ran me through a wizard.  I changed the "type" to USB and then the device to "usb:"  It then said it was going to send my information and ID to the device, so at this time I plugged my Centro in to the USB cable and I was happy to see that Gutsy and my Centro were "talking."  

Next, I opened Evolution.  I went to Edit - Synchronization Options.  I then clicked on "conduits" and enabled the ones I wanted to sync.  I chose "address" thinking it would sync my contacts with Evolution.  I did a hotsync and it said on my Centro that I was "synching address." Sure enough, my contacts are now backed up on Evolution.

I have not done much with the calendar on my Centro, but assume that it will sync nicely with Evolution, too.

Good luck and I hope this helps other people who might be trying to setup their Centros with Evolution using Gutsy.

---

### Post by vgrisham on 2008-04-22
mmtowns,

Thanks for this post. I just got my Centro today, and it's pretty cool. So far, what have you been able to get to sync with Ubuntu? 

Thanks,
Vaughn

---

### Post by bsmith1051 on 2008-04-30
Any more updates, guys?  I'm thinking about upgrading my old phone to a Centro, too.

---

### Post by vgrisham on 2008-04-30
Hi bsmith1051. I've had my Centro for a little over a week now. A couple of observations. First, make sure you get a good sized micro SDHC card with a card reader specifically made for SDHC. You're going to need it in order to interface with Ubuntu as far as digital photos, videos, music and files. Second, jPilot does not yet work with the Centro, so make sure you go through gnome-pilot so that you can sync your Centro with Evolution. You can configure gnome-pilot through Systerm>Preferences>PalmOS Devices. Make sure to tell it you're connecting via USB and change the port to USB: prior to sync-ing. Also, be sure and configure the PalmOS Devices options on the Conduits tab, matching exactly what you want to sync with Ubuntu.

The nice thing is, most of the Palm software that you'll want for your smartphone can install straight from the Internet, so you won't really need Palm Desktop.

---

### Post by bsmith1051 on 2008-05-01
so you're able to sync Contacts and Calendar over the USB, but you need to pop-out the memory card in order to transfer pictures or music?

---

### Post by vgrisham on 2008-05-01
Yes, that's right. The gnome-pilot daemon's Conduits tab has a ton of options however. There may be a way to sync more than Evolution stuff, but I haven't really tinkered with all of the options yet. For right now though, I can sync am syncing my contacts and calendar and gnome-pilot is backing up my Centro's databases.

One more thing, if you want the hotsync daemon to load, you need to add the applet to gnome panel. You can do so by right clicking on the panel and choosing Add To Panel, and then selecting Pilot Applet.

---

### Post by vgrisham on 2008-05-04
bsmith,

[This]("http://www.softick.com/cardexport2/") softare works well mounting the phone's card in Ubuntu (as well as on my wife's macbook and on my Vista gaming partition).

Vaughn

---

### Post by dkerlee on 2008-05-10
I use home addresses, and work addresses, and birthdays. Some of the information was getting synced via gnome-desktop and Evolution, but but not all of it. And I was getting doubles now and again. I found that jpilot with J-Pilot Preferences:Address:Use Contacts database (Palm OS >= 4.0) and J-Pilot Preferences:Memo:Use Memos database (Palm OS >= 4.0) works much better. JPilot is a very ugly program - but it catches every detail of information from my Centro, and THAT is the most important thing. Now if it would shoot that stuff into Evolution - I'd be set...

Ubuntu 8.04, Hardy Heron

---

### Post by mmtowns on 2008-05-10
> **vgrisham said:**
> mmtowns,

Thanks for this post. I just got my Centro today, and it's pretty cool. So far, what have you been able to get to sync with Ubuntu? 

Thanks,
Vaughn
So far, I've only attempted to sync contacts.  I'll fire it up here in the next few days and see what else I can get to work.

---

### Post by vgrisham on 2008-05-10
> **dkerlee said:**
> I use home addresses, and work addresses, and birthdays. Some of the information was getting synced via gnome-desktop and Evolution, but but not all of it. And I was getting doubles now and again. I found that jpilot with J-Pilot Preferences:Address:Use Contacts database (Palm OS >= 4.0) and J-Pilot Preferences:Memo:Use Memos database (Palm OS >= 4.0) works much better. JPilot is a very ugly program - but it catches every detail of information from my Centro, and THAT is the most important thing. Now if it would shoot that stuff into Evolution - I'd be set...

Ubuntu 8.04, Hardy Heron

So you got J-Pilot to work with your Centro? I had read somewhere that the two weren't playing nice together. I'm having the same duplications when sync-ing with Evolution and I too would like to send info into Evolution.

---

### Post by dkerlee on 2008-05-11
> **vgrisham said:**
> So you got J-Pilot to work with your Centro? I had read somewhere that the two weren't playing nice together. I'm having the same duplications when sync-ing with Evolution and I too would like to send info into Evolution.

Yeah, they just sorta work together. But like I said, jpilot is u.l.g.y. and I wish it was as good looking as Evolution. I don't even care about the email portion much - it's nice to just keep it to webmail. For settings in the connection dialouge I have: 
Serial Port - usb:
Serial Rate - 57600
then where I can, I've selected Palm OS >= 4.0

Good luck

---

### Post by danbodoh on 2008-05-13
> **bsmith1051 said:**
> so you're able to sync Contacts and Calendar over the USB, but you need to pop-out the memory card in order to transfer pictures or music?

I've just finished writing a JPilot plugin to fetch the photos and videos from the Centro (and other late-model Treos (Treo 680, Treo 700p, and Treo 755p).  It's not been tested on Treos yet.

Download the source from [http://sourceforge.net/projects/picsnvideos/](http://sourceforge.net/projects/picsnvideos/)

---

### Post by bcnaat on 2008-05-26
First, thanks for the plug in for pictures **danbodoh**! Awesome.

Second, to get my Centro sync'd with JPilot I couldn't use the the Palm=> 4.0 settings or it stalled. This may be due to the fact that I sync'd my Z22 with JPilot before receiving the Centro and just kept everything the same since I needed the Z22 things on my Centro.

If I used the higher OS setting, it would stall at the first sync of Contacts and then the connection would be broken between the Palm and JPilot. 

Kay

---

### Post by vgrisham on 2008-05-26
danbodoh, thanks very much for the plugin. 

I executed the deb. Do I have to do anything in jpilot? I don't see the pics plugin listed in jpilot's plugins section.

---

### Post by bcnaat on 2008-05-27
vgrisham:

After syncing with the plugin, I now have a file in my home folder labeled Palm Pictures. I'm guessing it adds that folder and yes, all my photos are in there from my Centro.

---

### Post by danbodoh on 2008-05-27
> **vgrisham said:**
> d
I executed the deb. Do I have to do anything in jpilot? I don't see the pics plugin listed in jpilot's plugins section.

The only evidence of it that you will find in JPilot is under the "Help" menu on the right, and under "File..Preferences..Conduits".  JPilot must be restarted after the deb package is installed.

If it's not there, can you post exactly what you did?

Dan

---

### Post by vgrisham on 2008-06-01
Danbodoh, 

Here's my output from within j-pilot: 
Error reading file: ContactsDB-PAdd.pdb
Open failed on plugin [/usr/lib/jpilot/plugins/libpicsnvideos.so]
 error [/usr/lib/jpilot/plugins/libpicsnvideos.so: wrong ELF class: ELFCLASS32]
****************************************
 Syncing on device USB:
 Press the HotSync button now
****************************************
pi_bind error: USB: No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished
Error reading file: ContactsDB-PAdd.pdb

I should've mentioned that I'm running 64-bit Hardy (Gnome).

EDIT: For other 32-bit apps, I've been able to use Cappy's getlibs script to build whatever 32-bit libraries are required. For instance, for Amazon's MP3 Downloader, I've forced the deb and then in a shell coded getlibs amazonmp3. I tried 'getlibs libpicsnvideos.so, but that didn't work.

---

### Post by danbodoh on 2008-06-01
> **vgrisham said:**
> 
Here's my output from within j-pilot: 
Error reading file: ContactsDB-PAdd.pdb
Open failed on plugin [/usr/lib/jpilot/plugins/libpicsnvideos.so]
 error [/usr/lib/jpilot/plugins/libpicsnvideos.so: wrong ELF class: ELFCLASS32]


You can't use getlibs, because the Pics&Videos plugin is a shared library that JPilot loads.  JPilot itself is a 64-bit app, so it must load only 64-bit libs.

I don't have a 64-bit system to build a deb binary package for 64-bit, but you could compile it from the source.

Download picsnvideos-0.2.tar.gz

The do the following
```

tar zxvf picsnvideos-0.2.tar.gz
sudo apt-get install libpisock-dev gdbm-dev
cd picsnvideos-0.2
./configure
make

```
Then you have a choice - to place the plugin in the system-wide JPilot plugins directory, do 'sudo make install'.  If you want to place it in your personal plugins directory, do 'make local_install'

I'd suggest you put it into the system wide directory, because that's were any future 64-bit debian package would put it.  When you install the package, it would overwrite the old version.

You can delete the picsnvideos-0.2 directory after installing; it's no longer needed.

Enjoy!

Dan Bodoh

---

### Post by vgrisham on 2008-06-01
Thanks for the quick reply. What do you mean by system wide folder?

EDIT: And how do I uninstall the 32-bit plugin?

---

### Post by danbodoh on 2008-06-01
> **vgrisham said:**
> 
 What do you mean by system wide folder?

EDIT: And how do I uninstall the 32-bit plugin?

Remove the 32-bit package with
sudo dpkg -r jpilot-picsnvideos

Installing in the system wide folder (/usr/lib/jpilot/plugsin) allows all users on your system to see the plugin.  Installing locally ($HOME/.jpilot/plugins) gives only that user access to the plugin.

Dan Bodoh

---

### Post by themoose on 2008-07-15
I've had my centro for about a month and used evolution with palm for about a year with only minor hitches.  However, just today, although evolution and the palm recognize each other they either
1. won't exchange information (this is happening with the ecalendar)- regardless of the setting on the conduit or
2. just make extra copies of everything, for example I now have 4 of every task - the list was already dauntingly long...

Help!

---

### Post by themoose on 2008-07-15
OK, I've made a bit of progress.  The only thing I had changed since last syncing was I had tried to activate a versamail account.  I deleted that account and now it is trying to sync the calendar, but, I think, timing out and no data is being transferred at all - in either direction.  Something else was funny in that at the beginning of this little odyssey, the id evolution had for my centro was different.

---

### Post by mmtowns on 2008-07-16
> **themoose said:**
> OK, I've made a bit of progress.  The only thing I had changed since last syncing was I had tried to activate a versamail account.  I deleted that account and now it is trying to sync the calendar, but, I think, timing out and no data is being transferred at all - in either direction.  Something else was funny in that at the beginning of this little odyssey, the id evolution had for my centro was different.

I'm having similar issues now, too.  I went from loving my Centro/Evolution sync to wondering what I did wrong.  Looks like I need to spend some serious time reading and playing around.  How are others doing?

---

