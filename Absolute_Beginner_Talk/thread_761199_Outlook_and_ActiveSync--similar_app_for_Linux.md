---
title: "Outlook and ActiveSync--similar app for Linux?"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by mypetduck on 2008-04-21
I've seen old posts about this topic, but wanted a fresh perspective. I'm trying to move away from Windows and other MS products in moving to Xubuntu, but one thing I would have a hard time not having is my Windows Mobile 6.0 Samsung BlackJack II with Outlook, for I rely heavily upon syncing Outlook btw my laptop and phone.

Does any Linux app (PIM and sync software) do what ActiveSync does?

---

### Post by trwrt on 2008-04-21
Evolution can supposedly sync with Palm devices, but I don't know of anything that works with Windows Mobile devices at this time, sorry.  One way might be to sync your desktop programs with Google calendar and address book, I think Thunderbird and Sunbird can do that, and then see if there is a Windows Mobile program that can do the same thing from the Blackjack side.

---

### Post by trwrt on 2008-04-21
I should have searched first, here's someone who got it to work:

[http://ubuntuforums.org/showthread.php?t=717807&highlight=activesync](http://ubuntuforums.org/showthread.php?t=717807&highlight=activesync)

Looks like a real battle, though.

---

### Post by mypetduck on 2008-04-21
Thanks for finding that. Subsequent to my post I found something about Mandriva's support for syncing, but that's a whole different Linux, correct?

---

### Post by PartisanEntity on 2008-04-21
Have a look at Evolution in combinational with Multisync I think it's called. It worked very well for me when I had a Sony Ericcson. It is not working for me with my Nokia 6300 although other users with the same phone have had success.

---

### Post by mypetduck on 2008-04-22
I'll check that out, though I'm beginning to think I might have to stick with Windows for my mobile PIM needs for the time being. Also because as a writer I'm told I'd have a hard time ensuring Word compatability with Linux options. 

Otherwise, I am giving Xubuntu a try for what I can use it for. I installed it on an old but very very portable Toshiba Portege 7200CT. Sure beats my Dell Inspiron 5160 weight-wise.

---

### Post by habibbijan on 2008-04-22
Give this a shot - [Sync Windows Mobile Contacts and Calendar with Thunderbird and Google for Free]("http://www.tipsfor.us/2008/04/19/sync-your-windows-mobile-contacts-and-calendar-with-plaxo-thunderbird-and-google-for-free/")

Full disclaimer: I wrote the article. The beauty of this method is that it is operating system independent. Windows, Mac, and Linux users can all take advantage of it. 

If you don't need Thunderbird support, there's a much simpler method [using the open-source Funambol client]("http://www.tipsfor.us/2008/04/15/sync-your-windows-mobile-contacts-and-calendar-using-funambol-for-free/"). Both methods are totally free.

---

### Post by mypetduck on 2008-04-23
> **habibbijan said:**
> Give this a shot - [Sync Windows Mobile Contacts and Calendar with Thunderbird and Google for Free]("http://www.tipsfor.us/2008/04/19/sync-your-windows-mobile-contacts-and-calendar-with-plaxo-thunderbird-and-google-for-free/")


This looks cool, and I really wanted to try Thunderbird/Sunbird--but when I looked into it a ways back, it couldn't reliably (with an add-on) import my .pst files. I save a ton of email in Outlook much like I used to in Gmail (I like having it on my desktop).

Recently, however, I did see a way to import Outlook stuff into Gmail...hmmm...

I know a lot of folks don't like Outlook in particular (and of course MS in general), but I've got a lot of legacy information in there. If I can find a way to move it smoothly into another app, such as Thunderbird, I'll be very happy.

What I like about your above suggestion is that it adds an online component to my calender, which currently I don't have (just have it on my Windows desktop and phone).

---

### Post by gdiepen on 2008-04-25
> **mypetduck said:**
> 
Does any Linux app (PIM and sync software) do what ActiveSync does?

There does exist the SynCE project ([http://www.synce.org](http://www.synce.org)) which supplies a plugin for the OpenSync Synchronisation framework. This plugin will do the actual 'activesync' talking to wm5/wm6 device.

Furthermore, I have written an ActiveSync like application called SynCE-KPM (written in python in combination with the Qt4 widgets) that will allow you to manage your phone and that will show you the progress of an ActiveSync session that is going on (The synce-kpm screen will show something similar to the activesync screen on your device while it is syncing). SynCE-KPM will not do the actual syncing itself to your PIM application, again, that is done via OpenSync.

If you want to see how SynCE-KPM looks, please visit my website for screenshots and a screencast of the application while doing its work: [http://www.guidodiepen.nl/](http://www.guidodiepen.nl/)

Currently we are in the process of packaging the new 0.11.1 release for debian, and hopefully soon the ubuntu packages will follow also. If you want to use the latest synce-kpm right now, that is possible also, download the 0.11.1 release of sync-engine from [www.synce.org](www.synce.org) and download the 0.11.1 release of synce-kpm from [www.synce.org](www.synce.org). Both are python programs and both will work with the 0.11 version of the rest of the synce-components. 

If you have more questions, feel free to ask them.

---

### Post by christianxxx on 2008-04-25
As I suspected, SynCE-KPM is in fact a KDE application, and I've noticed while reading many posts on the subject, that there are far more alternatives for KDE.

Are there any Gnome-based projects for a similar functionality? Are there limitations to Gnome, or is it just that KDE is coincidentially preferred among the developers of this functionality?

I'm planning to buy a HTC TyTN II (with WM6 I think) or similar, and syncronising contacts, calendar and possibly other items is really needed...

---

### Post by gdiepen on 2008-04-26
> **christianxxx said:**
> As I suspected, SynCE-KPM is in fact a KDE application, and I've noticed while reading many posts on the subject, that there are far more alternatives for KDE.

Are there any Gnome-based projects for a similar functionality? Are there limitations to Gnome, or is it just that KDE is coincidentially preferred among the developers of this functionality?

I'm planning to buy a HTC TyTN II (with WM6 I think) or similar, and syncronising contacts, calendar and possibly other items is really needed...

I just want to stress once more that synce-kpm does NOT do the syncing part, it only shows the information regarding the sync process. The actual syncing is done regardless of the DE and is done via opensync through a plugin provided by our sync-engine.

This being said, the reason that I started to write synce-kpm was that most of the tools available were all gnome tools and nothing was there for KDE. That got me started with creating synce-kpm.

With regards to your HTC TyTN II, I have such a device and I have the syncing working (don't use it all the time though, but it is working ;) )

---

### Post by nutpants on 2008-04-26
i have been battling synce and my windows mobile 6 device forever.. and its the same battle when i had my WM5 device and my WM2003 device..

i dont understand why,
  if you can add software to make your pocket pc or smart phone act like a usb drive, they dont just work with the files in the smartphone or pocket pc and bypass active sync on the device.
just put the WM device in usb mode and then work out how to read the files on it.

nutz

---

### Post by gdiepen on 2008-04-26
> **nutpants said:**
> i have been battling synce and my windows mobile 6 device forever.. and its the same battle when i had my WM5 device and my WM2003 device..

i dont understand why,
  if you can add software to make your pocket pc or smart phone act like a usb drive, they dont just work with the files in the smartphone or pocket pc and bypass active sync on the device.
just put the WM device in usb mode and then work out how to read the files on it.

nutz
Your last suggestion is really not gonna work, due to locking issues etc. In theory it would be possible to directly edit the database volume on the device, but this really will create more problems than actually solve. (For one, if MS decides to change the internal storage mechanism, you will have to rewrite that also again). Again, I really think accessing the files directly is NOT the way to go.

Furthermore, if you provide us with the issues you are having with synce and your phone, we might be able to help you out and in the process update instructions :)

The current version of synce works for both wm5 and wm6 devices. The old style wm2003 devices are less supported, but the guy working on the sync-engine also is trying to put in the legacy sync-stuff for these devices also.

---

### Post by christianxxx on 2008-04-26
> **gdiepen said:**
> This being said, the reason that I started to write synce-kpm was that most of the tools available were all gnome tools and nothing was there for KDE. That got me started with creating synce-kpm.


Thanks for your enlighting answer. Could you please give me a hint about what Gnome tools to look for?

---

### Post by nutpants on 2008-04-26
[QUOTE=.

Furthermore, if you provide us with the issues you are having with synce and your phone, we might be able to help you out and in the process update instructions :)
.[/QUOTE]

im all for beating at this untill it works...

at the moment im at..
[ 5167.457143] usb 5-2.3: new full speed USB device using ehci_hcd and address 19
[ 5167.545020] usb 5-2.3: device descriptor read/64, error -71
[ 5167.736764] usb 5-2.3: device descriptor read/64, error -71

[ 4942.323568] usb 5-2.3: device not accepting address 16, error -32
[ 4942.411479] usb 5-2.3: new full speed USB device using ehci_hcd and address 17
[ 4942.818815] usb 5-2.3: device not accepting address 17, error -32


so my device will not even connect to ubuntu..
this is my HTC 621 with windows mobile 6.1  ce os 5.2.19700 standard installed on it.

my sx-66 with windows mobile 6 professional connects fine
[ 5300.199711] usb 5-2.4: new full speed USB device using ehci_hcd and address 27
[ 5300.396416] usb 5-2.4: configuration #1 chosen from 1 choice
[ 5302.129979] rndis0: register 'rndis_host' at usb-0000:00:1d.7-2.4, RNDIS device, 80:00:60:0f:e8:00

but i almost never use it anymore.

nutz
as always thanks for any help
(i dont see why there would be locking problems dealing with the data bases on the devices i have used many back up programs that work "on the fly" on the devices them selves that only back up the data bases, no resets or anything.. but im a noob what do i know)
(even with the sx66 working i dont know what to do next i have not even looked as the htc device is the one i want to work, maybe i should just play with it and keep checking back to see if the htc starts working)

---

### Post by gdiepen on 2008-04-27
> **christianxxx said:**
> Thanks for your enlighting answer. Could you please give me a hint about what Gnome tools to look for?

I know that there was a program called synce-trayicon. At least the current SVN version does do wm5/wm6 devices also. The only problem is that I don't know that much about the gnome programs, because I don't use it. But when I joined the synce team, pretty much everybody was using gnome.

Because I was one of the few KDE guys, I just looked at the stuff available for kde and saw that there existed a program called synce-kde. Unfortunately this didn't work with the wm5/wm6 devices, so then I wrote synce-kpm.


> **nutpants said:**
> im all for beating at this untill it works...

at the moment im at..
[ 5167.457143] usb 5-2.3: new full speed USB device using ehci_hcd and address 19
[ 5167.545020] usb 5-2.3: device descriptor read/64, error -71
[ 5167.736764] usb 5-2.3: device descriptor read/64, error -71

[ 4942.323568] usb 5-2.3: device not accepting address 16, error -32
[ 4942.411479] usb 5-2.3: new full speed USB device using ehci_hcd and address 17
[ 4942.818815] usb 5-2.3: device not accepting address 17, error -32


so my device will not even connect to ubuntu..

Wow. This really is an interesting one. This goes even wrong before loading the driver I guess :)

The only thing I can think of for this is not which version of Windows Mobile you have, but more the fact that one device (the wm6.1 device) might be a USB 2.0 device, while the other is not. Besides that, I really don't know what could cause this error.

---

### Post by nutpants on 2008-04-27
maybe ill start messing with the sx66 and see how it goes
then ill come back to the htc621

now ill i have to find out is how to actually sync with something
since the sx is recognized

nuts..

all in one solution??  
more like piecemeal 
as long as it works thats what matters

(working from this web page([http://ubuntuforums.org/showthread.php?t=345176&highlight=synce+how+to](http://ubuntuforums.org/showthread.php?t=345176&highlight=synce+how+to)) i have run into the error
[ 4029.790932] sr 1:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[ 4029.790945] sr 1:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present
[ 4029.790953] end_request: I/O error, dev sr0, sector 0
[ 4306.582231] rndis0: no IPv6 routers present)

from sudo odccm -f
i get nothing at all....

so i am working on that now.)
(every link i find to the synce website for info turns up a empty page with no info) i could use a newer walk though for newer devices

---

### Post by nutpants on 2008-04-27
update

i did not wait long enough.. about 5 mins later..(after i went to make lunch came back and found)

 sudo odccm -f


** (odccm:11396): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'


but the command
pls gets me 

@linux-laptop:~$ pls

** (process:11634): WARNING **: synce_info_from_odccm: Failed to get a connection for WM_Nut: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
pls: Could not find configuration at path '(Default)'

im still working at it..

then i found the error 5 more mintues later

** (odccm:12242): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device
** (odccm:12242): DEBUG: PDA disconnected! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00', device='rndis0'

 
nutz
(maybe my pain will help others..)

---

### Post by gdiepen on 2008-04-27
> **nutpants said:**
> update

i did not wait long enough.. about 5 mins later..(after i went to make lunch came back and found)

 sudo odccm -f


** (odccm:11396): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'


but the command
pls gets me 

@linux-laptop:~$ pls

** (process:11634): WARNING **: synce_info_from_odccm: Failed to get a connection for WM_Nut: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
pls: Could not find configuration at path '(Default)'

im still working at it..

then i found the error 5 more mintues later

** (odccm:12242): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device
** (odccm:12242): DEBUG: PDA disconnected! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00', device='rndis0'

 
nutz
(maybe my pain will help others..)

Please make sure that:
[LIST]
[*]You have installed usb-rndis-lite (see our wiki for instructions, you can either install the drivers from SVN, or via the module assistant way.)
[*]You have removed the original rndis_host, cdc_ether, and usb-net drivers (see the ubuntu page on our wiki)
[*]You don't have a firewall running
[/LIST]

If you can verify that all of the above are true for you, then you can try to plugin the device and run:
sudo dhclient rndis0

If you get an IP address then, please let me know what the IP address is that you got and what the IP address of the dhcp server is (this is the phone in this case). Again, this step is only useful if you are absolutely sure that the above steps are completely done.

Furthermore, regarding your message that you only see empty pages on the wiki, which pages are that? For ubuntu everything is pretty much present AFAIK. The only thing is that for installing the actual syncing stuff for hardy is a bit more difficult, because something is changed by the opensync guys in their PPA IIRC.

---

### Post by nutpants on 2008-04-27
got the error

linux-laptop:~$ sudo rm /lib/modules/`uname -r`/kernel/drivers/net/usb/{rndis_host,cdc_ether,usbnet}.ko
rm: cannot remove `/lib/modules/2.6.24-16-generic/kernel/drivers/net/usb/rndis_host.ko': No such file or directory
rm: cannot remove `/lib/modules/2.6.24-16-generic/kernel/drivers/net/usb/cdc_ether.ko': No such file or directory
rm: cannot remove `/lib/modules/2.6.24-16-generic/kernel/drivers/net/usb/usbnet.ko': No such file or directory


following directions on page... [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

after doing my best to make sure that everything was up to date
(and everything said it was)
and building rndis lite from the instructions here
[http://www.synce.org/moin/SynceInstallation/Source?highlight=(usb-rndis-lite](http://www.synce.org/moin/SynceInstallation/Source?highlight=(usb-rndis-lite))

i get this


Listening on LPF/rndis0/80:00:60:0f:e8:00
Sending on   LPF/rndis0/80:00:60:0f:e8:00
Sending on   Socket/fallback
DHCPREQUEST of 169.254.2.2 on rndis0 to 255.255.255.255 port 67
DHCPACK of 169.254.2.2 from 169.254.2.1
bound to 169.254.2.2 -- renewal in 1271852 seconds.

sudo odccm -f

gives me
@linux-laptop:~/downloads/usb-rndis-lite-0.11$ sudo odccm -f
** (odccm:18653): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'
    
** (odccm:18653): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device

** (odccm:18653): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device
** (odccm:18653): DEBUG: PDA disconnected! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00', device='rndis0'

any other info i can provide i will.

nutz

---

### Post by gdiepen on 2008-04-28
> **nutpants said:**
> got the error

linux-laptop:~$ sudo rm /lib/modules/`uname -r`/kernel/drivers/net/usb/{rndis_host,cdc_ether,usbnet}.ko
rm: cannot remove `/lib/modules/2.6.24-16-generic/kernel/drivers/net/usb/rndis_host.ko': No such file or directory
rm: cannot remove `/lib/modules/2.6.24-16-generic/kernel/drivers/net/usb/cdc_ether.ko': No such file or directory
rm: cannot remove `/lib/modules/2.6.24-16-generic/kernel/drivers/net/usb/usbnet.ko': No such file or directory


following directions on page... [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

after doing my best to make sure that everything was up to date
(and everything said it was)
and building rndis lite from the instructions here
[http://www.synce.org/moin/SynceInstallation/Source?highlight=(usb-rndis-lite](http://www.synce.org/moin/SynceInstallation/Source?highlight=(usb-rndis-lite))

i get this


Listening on LPF/rndis0/80:00:60:0f:e8:00
Sending on   LPF/rndis0/80:00:60:0f:e8:00
Sending on   Socket/fallback
DHCPREQUEST of 169.254.2.2 on rndis0 to 255.255.255.255 port 67
DHCPACK of 169.254.2.2 from 169.254.2.1
bound to 169.254.2.2 -- renewal in 1271852 seconds.

sudo odccm -f

gives me
@linux-laptop:~/downloads/usb-rndis-lite-0.11$ sudo odccm -f
** (odccm:18653): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'
    
** (odccm:18653): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device

** (odccm:18653): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device
** (odccm:18653): DEBUG: PDA disconnected! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00', device='rndis0'

any other info i can provide i will.

nutz

The fact that dhclient works would indicate that the driver is functioning properly. Just to be 100% sure, could you install the latest driver from SVN, because this has a modified message for dmesg.
You can install this with:
svn checkout [http://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite](http://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite)
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install
cd ..

After that, can you stop any running odccm processes (killall -9 odccm).
After this you can start odccm with "sudo odccm -f" and then you can plugin the device.

Could you give the output of the last couple of  lines of dmesg and the output of odccm.

Guido Diepen

---

### Post by nutpants on 2008-04-28
[  168.600584] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  168.600826] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  168.602174] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  168.602351] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  561.366036] usb 5-2.3: new full speed USB device using ehci_hcd and address 5
[  561.564225] usb 5-2.3: configuration #1 chosen from 1 choice
[  563.682960] usbcore: registered new interface driver cdc_ether
[  563.400190] rndis0: register 'rndis_host' at usb-0000:00:1d.7-2.3, RNDIS device (SynCE patched), 80:00:60:0f:e8:00
[  563.400235] usbcore: registered new interface driver rndis_host





@linux-laptop:~/usb-rndis-lite$ sudo odccm -f
** (odccm:7204): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'
** (odccm:7204): DEBUG: device_info_received
** (odccm:7204): DEBUG: cf 1b f6 05 7f a4 f1 ed 99 18 44 d7 5e 4e 85 c0 05 00 00 00 02 00 00 00 0c 00 00 00 57 00 4d 00 5f 00 4e 00 75 00 74 00 70 00 61 00 6e 00 74 00 73 00 31 00 00 00 05 02 54 06 11 0a 00 00 05 00 00 00 e7 49 ff 72 fc 12 ca 43 0f 00 00 00 50 6f 63 6b 65 74 50 43 00 53 53 44 4b 00 00 06 00 00 00 50 48 32 30 42 31 00 02 00 00 00 05 00 00 00 02 00 00 00 05 00 00 00 02 00 00 00 00 00 00 00 10 00 00 00 0c 00 00 00 5d 00 00 00 01 00 00 00
** (odccm:7204): DEBUG: extradata:
** (odccm:7204): DEBUG: 10 00 00 00 0c 00 00 00 5d 00 00 00 01 00 00 00
** Message: device_info_received: registering object path '/org/synce/odccm/Device/_05F61BCF_A47F_EDF1_9918_44D75E4E85C0_'



great..

now pls give me a file listing..

so it should be working..
the new driver made the difference..

thank you.

---

### Post by nutpants on 2008-04-28
what was working before no longer works now..

im back to not getting any info from the device anymore

with the error

 (process:8226): WARNING **: synce_info_from_odccm: Failed to get a connection for WM_Nutpants1: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
pls: Could not find configuration at path '(Default)'

the only thing that has changed on my system is that i installed quake 2
this morning.

linux-laptop:~$ synce-gnome &
[4] 8574
linux-laptop:~$ Created CeDevice with obj_path="/org/synce/odccm/Device/_05F61BCF_A47F_EDF1_9918_44D75E4E85C0_"
  GetIpAddress: 169.254.2.1
  GetGuid: {05F61BCF-A47F-EDF1-9918-44D75E4E85C0}
  GetOsVersion: (dbus.UInt32(5L), dbus.UInt32(2L))
  GetName: WM_Nutpants1
  GetVersion: 106168837
  GetCpuType: 2577
  GetCurrentPartnerId: 1929333223
  GetId: 1137316604
  GetPlatformName: PocketPC
  GetModelName: PH20B1
  GetPasswordFlags: 0
Device is not requiring a password
Waiting for device to hotplug


$ sudo odccm -f
** (odccm:8509): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'

** (odccm:8509): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device

** (odccm:8509): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device
** (odccm:8509): DEBUG: PDA disconnected! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00', device='rndis0'
** (odccm:8509): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'

** (odccm:8509): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device

** (odccm:8509): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device
** (odccm:8509): DEBUG: PDA disconnected! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00', device='rndis0'

dmesg 


[ 2663.338120] rndis0: unregister 'rndis_host' usb-0000:00:1d.7-2.3, RNDIS device (SynCE patched)
[ 2830.500663] usb 5-2.3: new full speed USB device using ehci_hcd and address 28
[ 2830.588547] usb 5-2.3: device descriptor read/64, error -32
[ 2830.780172] usb 5-2.3: device descriptor read/64, error -32
[ 2830.971919] usb 5-2.3: new full speed USB device using ehci_hcd and address 29
[ 2831.059804] usb 5-2.3: device descriptor read/64, error -32
[ 2831.395365] usb 5-2.3: new full speed USB device using ehci_hcd and address 30
[ 2831.803071] usb 5-2.3: configuration #1 chosen from 1 choice
[ 2831.510042] rndis0: register 'rndis_host' at usb-0000:00:1d.7-2.3, RNDIS device (SynCE patched), 80:00:60:0f:e8:00
[ 2952.066279] rndis0: kevent 0 may have been dropped
[ 2952.170143] rndis0: kevent 0 may have been dropped
[ 2952.178132] rndis0: kevent 0 may have been dropped
[ 2952.222075] rndis0: kevent 0 may have been dropped
[ 2954.282330] usb 5-2.3: USB disconnect, address 30
[ 2954.283695] rndis0: unregister 'rndis_host' usb-0000:00:1d.7-2.3, RNDIS device (SynCE patched)


nutz

---

### Post by gdiepen on 2008-04-29
This is really weird.

Although the rndis0 device is regsitered, I am not happy with the messages above it:
2830.588547] usb 5-2.3: device descriptor read/64, error -32

This really shows something is going wrong. IIRC ehci is the usb2.0 driver. Could you please try once to rmmod this driver and have your computer only use usb1.0 drivers (that would be only uhci and ohci I think)

Guido Diepen

---

### Post by nutpants on 2008-04-29
@linux-laptop:~$ sudo rmmod ehci
[sudo] password for nut: 
ERROR: Module ehci does not exist in /proc/modules


nutz

---

### Post by gdiepen on 2008-04-29
Ok, that was my mistake, I should have mentioned the complete name:
rmmod ehci_hcd

Guido Diepen

---

### Post by nutpants on 2008-04-29
and i just found it..

it worked once.. and i could get a listing from pls...

here is the out put from odccm -f
linux-laptop:~$ sudo modprobe -r ehci_hcd
[sudo] password for nut: 
nut@linux-laptop:~$ sudo echo "blacklist ehci_hcd" > /etc/modprobe.d/blacklist-ehci
bash: /etc/modprobe.d/blacklist-ehci: Permission denied
linux-laptop:~$ sudo odccm -f
** (odccm:7655): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'

** (odccm:7655): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device

** (odccm:7655): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device
** (odccm:7655): DEBUG: PDA disconnected! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00', device='rndis0'
** (odccm:7655): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'

** (odccm:7655): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device

** (odccm:7655): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device
** (odccm:7655): DEBUG: PDA disconnected! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00', device='rndis0'
** (odccm:7655): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'


i got one listing from pls and nothing else.

im back to having no connecting again.
ill try reseting everything and try again.

nutz

---

### Post by nutpants on 2008-04-29
yes i can confirm that it works for one connecting only..
then i have to reboot the computer.
i can connect once then i remove the Wm device or let it turn it self off  i have to restart ubuntu to connect again.

ill put the usb 2 driver back in and make sure that is what is happening with them too.

nutz

update 
i did a sudo modprobe ehci-hcd to put the usb 2 drivers back

then rebooted and it acts the same
one connection only if the device times out or is removed i have to reboot ubuntu

(silly me i can kill odccm then it works again)
linux-laptop:~$ sudo odccm -f
** (odccm:7322): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'
** (odccm:7322): DEBUG: device_info_received
** (odccm:7322): DEBUG: cf 1b f6 05 7f a4 f1 ed 99 18 44 d7 5e 4e 85 c0 05 00 00 00 02 00 00 00 0c 00 00 00 57 00 4d 00 5f 00 4e 00 75 00 74 00 70 00 61 00 6e 00 74 00 73 00 31 00 00 00 05 02 54 06 11 0a 00 00 05 00 00 00 e7 49 ff 72 77 ae b4 4c 0f 00 00 00 50 6f 63 6b 65 74 50 43 00 53 53 44 4b 00 00 06 00 00 00 50 48 32 30 42 31 00 02 00 00 00 05 00 00 00 02 00 00 00 05 00 00 00 02 00 00 00 00 00 00 00 10 00 00 00 0c 00 00 00 5d 00 00 00 01 00 00 00
** (odccm:7322): DEBUG: extradata:
** (odccm:7322): DEBUG: 10 00 00 00 0c 00 00 00 5d 00 00 00 01 00 00 00
** Message: device_info_received: registering object path '/org/synce/odccm/Device/_05F61BCF_A47F_EDF1_9918_44D75E4E85C0_'

now it seems to work
but i have to kill odccm each time
one more update
if i kill odccm then after it seems to work fine for hot pluging
and now it sees both my sx66 and my htc 621
ill try it a few more times to see if it is relibile. then ill look to see what i have to do to sync with the computer.

nutz

---

### Post by gdiepen on 2008-04-29
I still  think that the fact that you see the error messages with device descriptor read might also be something that could explain this issue, unfortunately I don't know how. 

This is really the first time that I see these error messages.

---

### Post by nutpants on 2008-04-29
both devices give the error messages
 the sx66 and the htc621

but at least they are both working and recognized now 
that is better than it was before
and i know i have to kill odccm for it to work (strange)

if they will sync or not is a different story.

not much use if they dont sync

ok i am running odccm -f in a term and synce-gnome in another term
and it is recognizing me swapping devices on the usb cable
(it will not allow 2 devices at the same time(that i can live with)
what next?
how do i get synce to communicate with opensync to talk to multi sync to talk to evolution mail....

(i AM taking notes so i can post a "it happen to me but it worked" when i am all done)

nutz

---

### Post by gdiepen on 2008-04-30
Next thing is to install the 0.22 of opensync. Our sync-engine provides a plugin for opensync such that the phone can be used as an endpoint for syncing in the opensync-framework. Another endpoint will be a plugin for evolution. 

More information about this is on our wiki ([www.synce.org](www.synce.org))

---

### Post by nutpants on 2008-04-30
i have read and check and double checked the required install packages

but for some reason

linux-laptop:~$ sync-engine
bash: sync-engine: command not found

 /usr/bin/sync-engine
bash: /usr/bin/sync-engine: No such file or directory


the closest i have after searching is

/usr/share/pycentral/synce-sync-engine/

what am i missing here?

nutz.

---

### Post by gdiepen on 2008-04-30
ah. It looks like you have hit a bug in one of our packages. This still up for being solved, but it really is a packaging problem ;)

What I can advice for the moment is to download the latest sync-engine (=0.11.1) from out website. You can untar the tarball and go into the new directory and just run sync-engine with: ./sync-engine

This will give you the additional advantage of running the 0.11.1 version of sync-engine which contains a large number of improvements over the 0.11 version. The 0.11.1 version is not packaged yet at the moment for ubuntu AFAIK, but we are working on it.

---

### Post by nutpants on 2008-04-30
thanks got the new one it seems to be working
( or at least it runs)
(btw your website needs a downloads page i finally found it by googling the name which pointed me to source forge.)
now 

linux-laptop:~$ msynctool --addmember synce-sync synce-opensync-plugin
Unable to instance plugin with name synce-opensync-plugin: Unable to find the plugin "synce-opensync-plugin"


following the instructions here
[http://www.synce.org/moin/SynceSetup/OpenSync?highlight=(opensync](http://www.synce.org/moin/SynceSetup/OpenSync?highlight=(opensync))

i found i have a directory
/usr/lib/opensync/plugins/python-plugins

with the right plugin..
but the website said it should be..
/usr/lib/opensync/python-plugins.

so i copyied the directory or just to be on the safe side...

but still no go.

nutz

(i must be related to murphy as what can go wrong is going wrong.)

---

### Post by gdiepen on 2008-04-30
Ah... Then we must be related, murphy is a close relative of me also ;)

Could you tell me which exact version of opensync you have installed?

Furthermore, the directory in theory should be:
/usr/lib/opensync/python-plugins 
(as stated on the website)

Guido Diepen

---

### Post by nutpants on 2008-04-30
now i always get confused here..
as there was a older sync project called multisync
but they changed to opensync but kept the name??? i think maybe

any hoo..
libopensync0
Synchronisation framework for email/pdas/and more

Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>

version 0.22-2
(the one that comes with ubuntu 8.04)
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libopensync0
/usr/share/doc/libopensync0/README
/usr/share/doc/libopensync0/TODO
/usr/share/doc/libopensync0/README.Debian
/usr/share/doc/libopensync0/copyright
/usr/share/doc/libopensync0/changelog.Debian.gz
/usr/lib
/usr/lib/libopensync-xml.so.0.0.0
/usr/lib/libopensync.so.0.0.0
/usr/lib/libosengine.so.0.0.0
/usr/lib/opensync
/usr/lib/opensync/formats
/usr/lib/opensync/formats/contact.so
/usr/lib/opensync/formats/data.so
/usr/lib/opensync/formats/event.so
/usr/lib/opensync/formats/file.so
/usr/lib/opensync/formats/note.so
/usr/lib/opensync/formats/todo.so
/usr/lib/opensync/formats/xml-evolution.so
/usr/lib/opensync/formats/xml-kde.so
/usr/lib/opensync/formats/xml-vcal.so
/usr/lib/opensync/formats/xml-vcard.so
/usr/lib/opensync/formats/xml-vnote.so
/usr/lib/opensync/formats/xmldoc.so
/usr/lib/opensync/osplugin
/usr/lib/libopensync-xml.so.0
/usr/lib/libopensync.so.0
/usr/lib/libosengine.so.0

and just incase this helps

python-opensync  version 0.22-2
Python bindings to the opensync synchronisation engine
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/python-opensync
/usr/share/doc/python-opensync/copyright
/usr/share/doc/python-opensync/changelog.Debian.gz
/usr/share/python-support
/usr/share/python-support/python-opensync
/usr/share/python-support/python-opensync/opensync.py
/usr/lib
/usr/lib/python-support
/usr/lib/python-support/python-opensync
/usr/lib/python-support/python-opensync/python2.5
/usr/lib/python-support/python-opensync/python2.5/_opensync.so


multisync-tools   version 0.91.0-4.1ununtu1
PIM Synchronization Command Line Tools
/.
/usr
/usr/bin
/usr/bin/msynctool
/usr/bin/convcard
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/convcard.1.gz
/usr/share/man/man1/msynctool.1.gz
/usr/share/doc
/usr/share/doc/multisync-tools
/usr/share/doc/multisync-tools/README
/usr/share/doc/multisync-tools/copyright
/usr/share/doc/multisync-tools/changelog.Debian.gz

multisync0.90
PIM Synchronization Tool
version 0.91.0-41unbunu1
/.
/usr
/usr/share
/usr/share/multisync-gui
/usr/share/multisync-gui/multisync-gui.glade
/usr/share/pixmaps
/usr/share/pixmaps/multisync-gui
/usr/share/pixmaps/multisync-gui/multisync.png
/usr/share/applications
/usr/share/applications/multisync-gui.desktop
/usr/share/doc
/usr/share/doc/multisync0.90
/usr/share/doc/multisync0.90/copyright
/usr/share/doc/multisync0.90/changelog.Debian.gz
/usr/bin
/usr/bin/multisync0.90


and while im at it

opensync-plugin-synce
SynCE plugin for OpenSync
version 1.11-hardy1-synce1
/.
/usr
/usr/lib
/usr/lib/opensync
/usr/lib/opensync/plugins
/usr/lib/opensync/plugins/python-plugins
/usr/lib/opensync/plugins/python-plugins/synce-opensync-plugin-2x.py
/usr/share
/usr/share/doc
/usr/share/doc/opensync-plugin-synce
/usr/share/doc/opensync-plugin-synce/copyright
/usr/share/doc/opensync-plugin-synce/changelog.gz
/usr/share/doc/opensync-plugin-synce/changelog.Debian.gz



and i still might have missed the info that you are looking for.

nutz

i dont know if i am the titanic or the iceberg  but time will tell with this.
(btw is there a command line that will tell me what version things are like "where" tells me where things are.)

---

### Post by gdiepen on 2008-05-02
We are trying to update the wiki for hardy users. The problem is that the names of the opensync packages have changed for some reason...

I can only advice you to look at the syncing-with-ubuntu guide on the wiki and check it for updates for hardy. If I don't forget I will mention it in this thread also that the wiki has been updated.

Guido Diepen

---

### Post by gdiepen on 2008-05-06
Ok, small update. Our wiki for ubuntu has been updated to work with hardy (gutsy and feisty are not shown on the page anymore though)

Let me know if the new instructions work out

Guido Diepen

---

### Post by nutpants on 2008-05-06
> **gdiepen said:**
> Ok, small update. Our wiki for ubuntu has been updated to work with hardy (gutsy and feisty are not shown on the page anymore though)

Let me know if the new instructions work out

Guido Diepen

[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

i followed everything line by line
had an update after through synaptic 
and now every thing works great.
everything synced up (calendar and contacts) that i tried

now all i have to do is automate it to sync with a script.

(and how to change the partnership created with (create_partnership.py "Linux desktop" "Contacts,Calendar" )

Thanks for all the great work.
and all the great help.

nutz

---

### Post by gdiepen on 2008-05-07
For the moment in theory it is possible to have the device initiate a sync (from the activesync menu on the device). This is then caught by sync-engine which has the possibility of running a given script when the device wants to sync (you have to define this via the ~/.synce/config.xml file). In theory this should work, but I don't know about the exact details.

Furthermore, changing a partnership through the synce tools is not (yet) possible. One way that might work, but I can't guarantee anything, is to unplug the device, goto start -> programs -> activesync. Change the settings of the partnership there and plugin the phone again. I have heard of people that this worked for, but I can't guarantee that it won't remove any data or so! Always make sure that you have a backup of the PIM data!!! :)

Guido Diepen

---

### Post by nutpants on 2008-05-07
i was able to delete the settings on the pda.

everything that i tried to sync worked both ways
calender tasks contacts.

with evolution

thanks for all the help..
this has always been one of the reasons that i have put off going to linux full time.

(this and mapping software like memory map and ozi explorer)

thank you again.

nutz

---

### Post by gdiepen on 2008-05-08
> **nutpants said:**
> i was able to delete the settings on the pda.

everything that i tried to sync worked both ways
calender tasks contacts.

with evolution

thanks for all the help..
this has always been one of the reasons that i have put off going to linux full time.

(this and mapping software like memory map and ozi explorer)

thank you again.

nutz

Happy that I could help :)

Users like you, that are running into problems while installing everything, actually help us also: we know what to change/update in the documentation :)

---

### Post by nutpants on 2008-05-08
your welcome..

now i just have to deal with linux duplicateing my contacts 4 times on my pda.  i have 4 of everything...

what a pain..

maybe it was my settings. ill have to check everything just to be sure and test it again...

i think i synced 3 times, which might be the reason i have 4 of everything.

nutz

---

### Post by markyb on 2008-05-13
> **gdiepen said:**
> Ok, small update. Our wiki for ubuntu has been updated to work with hardy (gutsy and feisty are not shown on the page anymore though)

Let me know if the new instructions work out

Guido Diepen

Hi,

your instructions mention windoes mobile 5/6, should they also work with WM2003?

Thanks.

---

### Post by nutpants on 2008-05-13
i was trying to get my wireless broadcom device working with the fwcutter

now my ppc no longer connects

errors

** (odccm:22119): DEBUG: PDA disconnected! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00', device='rndis0'
** (odccm:22119): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'

** (odccm:22119): WARNING **: failed to send trigger packet. sendto() failed: Operation not permitted

** (odccm:22119): WARNING **: failed to send trigger packet. sendto() failed: Operation not permitted

** (odccm:22119): WARNING **: failed to send trigger packet. sendto() failed: Operation not permitted

** (odccm:22119): WARNING **: failed to send trigger packet. sendto() failed: Operation not permitted

** (odccm:22119): WARNING **: failed to send trigger packet. sendto() failed: Operation not permitted

** (odccm:22119): WARNING **: failed to send trigger packet. sendto() failed: Operation not permitted

** (odccm:22119): WARNING **: failed to send trigger packet. sendto() failed: Operation not permitted

** (odccm:22119): WARNING **: failed to send trigger packet. sendto() failed: Operation not permitted

** (odccm:22119): WARNING **: failed to send trigger packet. sendto() failed: Operation not permitted

** (odccm:22119): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device

** (odccm:22119): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device
** (odccm:22119): DEBUG: PDA disconnected! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00', device='rndis0'




i think it is firewall related.. maybe..

---

### Post by gdiepen on 2008-05-13
> **markyb said:**
> Hi,

your instructions mention windoes mobile 5/6, should they also work with WM2003?

Thanks.

SynCE-KPM is developped with wm5/6 in mind. It might work to a certain limit for wm2003 devices, but I can't give any guarantees. Furthermore, the syncing (done via opensync via our plugin that talks to the sync-engine program) will not work (yet) for wm2003 devices because they use a different protocol for syncing. The person working on the sync-engine has mentioned he is trying to put support for this legacy syncing in the sync-engine also, but that is not there yet.

> 
** (odccm:22119): WARNING **: failed to send trigger packet. sendto() failed: Operation not permitted

** (odccm:22119): WARNING **: failed to send trigger packet. sendto() failed: Operation not permitted

** (odccm:22119): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device

** (odccm:22119): WARNING **: _odccm_configure_interface: failed to configure rndis0. ioctl(SIOCSIFADDR) failed: No such device
** (odccm:22119): DEBUG: PDA disconnected! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00', device='rndis0'




i think it is firewall related.. maybe..


I am pretty sure that this is firewall related. To start the communication between the computer and the device, odccm must send a special UDP packet. After receiving this, the device will initiate a TCP connection to the computer. I don't know the exact ports by heart, but I would advice you to just allow all communication on the rndis devices.

Guido Diepen

---

### Post by Stefanie on 2008-06-02
i have the same problem as nutpants, i'm afraid. when i run synce-pls, i get this message: 
```
** (process:13442): WARNING **: synce_info_from_odccm: Failed to get a connection for SGH-i320_1: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
synce-pls: Could not find configuration at path '(Default)'

```

sometimes, after trying a hundred times (plugging and unplugging the device, typing sudo odccm,...) it works and i get
```
** Message: Hal reports no devices connected
--D-----S-              2005-12-31 23:00:08  My Pictures/
Directory               2005-12-31 23:00:14  My Videos/
--D-----S-              2005-12-31 23:00:34  Notes/
Directory               2007-12-07 17:46:10  My Sounds/

```

I think it works if i run killall -9 odccm, unplug my device, run sudo odccm and then plug in the device.

the problems started after i upgraded from gutsy to hardy. i also had to download the latest version of sync-engine and run ./sync-engine instead of just sync-engine. 

another annoying problem is that my wireless connection is dropped when i plug in my phone, in favor of "wired connection. unkown usb interface". i need this usb connection to run synce-pls, but it is annoying that it disables my wireless.

---

### Post by nutpants on 2008-06-03
> **Stefanie said:**
> 

another annoying problem is that my wireless connection is dropped when i plug in my phone, in favor of "wired connection. unkown usb interface". i need this usb connection to run synce-pls, but it is annoying that it disables my wireless.

i found this to fix that..

> If you have the Gnome Network Manager running on Ubuntu, it will setup your device as the new default network connection. Check what ethernet device was given to your device with by running the following command in a terminal after you have connected your device:

/sbin/ifconfig -a | grep 80:00:60:0f:e8:00  | cut -d " " -f 1

then add the next line to /etc/network/interfaces:

iface <interface of your device> inet dhcp

This will make Gnome Network Manager ignore the interface. Then restart the networking with the command:

sudo /etc/init.d/networking restart


from here

[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

mine was rndis0
hope it helps

nutz

---

### Post by Stefanie on 2008-06-03
thanks, i'll try that!

---

### Post by Stefanie on 2008-06-03
it didn't work :-( it removed the interface altogether. i need to use the "wired usb connection" for synce-pls and sync-engine to work, and this wasn't possible anymore. 
apparently it isn't possible to have a usb connection and a wireless connection at the same time... 

i must say i really appreciate the work that has been done on this project, it must be a real pain to get those windows devices working. for me, syncing works sometimes, but sometimes it doesnt ("error connecting to one of the members" or something like that when i run msynctool --sync, even when synce-pls works and sync-engine is running!)

---

### Post by nutpants on 2008-06-03
interesting..
it removed it on my network manager but did not affect my syncing ability at all.
without it on my network manager  i can connect wifi or cable and sync just fine.

nutz.

---

### Post by Chr0mis on 2008-06-04
I've used Funambol for a month now, and overruling the lack of thunderbird, it works for me.

---

