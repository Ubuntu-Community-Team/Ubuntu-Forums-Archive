---
title: "Powerbook G4 12&quot; powerpc ubuntu 9.10 - login and install problem"
date: 2009-12-02
forum: Apple Hardware Users
---

### Post by kg3000 on 2009-12-02
Hello, 

I have recently tried to install ubuntu 9.10 on my powerbook (G4 12" titanium / powerpc).

I have downloaded this ISO from here: [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
*[http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-desktop-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-desktop-powerpc.iso)* 
And burned to dvd. 

So, my problem; the dvd boots fine and seems to start the install. I get the pretty ubuntu loading graphic and then the login page. 

Here is the trouble: I cannot login! Auto-login fails "Authorisation Failed" and typing a new login name /pwd doesn't work either.

I have a feeling this is a very simple problem, any help would be appreciated!

Many thanks,

kg

---

### Post by adamdotanderson on 2009-12-02
You know, I had this same problem with the release candidate of this software and then my dvd burner burned up so when the actual release came out I was forced to use the alternative install since it was the only image small enough to burn to regular cd and it worked fine. I don't know if that had anything to do with it but you might try using the alternative install image instead. Its on the same page. Third option in the list.

---

### Post by linuxopjemac on 2009-12-02
are you sure that your PRAM battery is still working ?

[http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram](http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram)

---

### Post by kg3000 on 2009-12-02
Thanks for both the responses, I will try the alternate ISO and then check the PRAM.

I'll report back if I manage to get it to work.

Thanks again

kg

---

### Post by kg3000 on 2009-12-02
Success! I decided to follow this tutorial to change the time in Open Firmware: [http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram](http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram)

Using the original ISO mentioned in my first post, I managed to boot and I am now running the install!

Thanks so much for pointing me to this tutorial, a simple solution but very affective!

kg

---

### Post by svtguy88 on 2009-12-02
Does your fan behave properly, or is it running full-bore all the time?  How is wireless support?  Batter life?

Sorry, just curious.  I installed Ubuntu on my 12'' PB as a secondary OS a few weeks ago, but my fan runs ALL the time at full speed.   There's a launchpad bug on it, but it doesn't seem to be getting any attention...

---

### Post by rednose0607 on 2009-12-02
Hi, just disable the therm module in /etc/modules. it is not ... needed. when my pb15" need it, a slow an silent fan a-la-apple starts anyway, regardless of the module.so far so good, but use it at yor risk ;)

---

### Post by svtguy88 on 2009-12-02
haha..yeah.  I figured deleting that would shut the fan down...but it just rubs me the wrong way...sort of like deleting the appletherm.kext (or something similar) to get my G4 upgrade to work correctly in OS X...

---

### Post by kg3000 on 2009-12-03
pkmgarf - good to see someone else is trying this! I haven't got far enough to discover those problems, but will keep you posted.

I'm currently stuck on the install (at 78%) with the error:
[I]
 [Erno 30] Read-only file system: '/target/boot/vmlinux-2.6.31-14-powerpc'[/I]

Think my hard disk drive is a bit frazzled or in need reformatting so I'm going to try another one.

I'll let you know what happens with a new disk drive.

kg

---

### Post by svtguy88 on 2009-12-03
Are you partitioning manually or giving the installer the whole disk?  I ran into some issues originally, but after playing with the partition table for a bit, I managed to get Karmic installed in a dual-boot setup with OS X.

---

### Post by kg3000 on 2009-12-03
I've gone for a new (well it was 'lying around' from an old machine) disk drive. 

I've managed to install ubuntu 9.10 on the disk but have got a few problems:

Once booted up I get several Error windows:
[I]
"The panel encountered a problem while loading "OADIID:GNOME_NotificationAreaApplet"
Delete/Don't Delete

"The panel encountered a problem while loading "OADIID:GNOME_IndicatorApplet"
Delete/Don't Delete

 "The panel encountered a problem while loading "OADIID:GNOME_ClockApplet"
Delete/Don't Delete

"The panel encountered a problem while loading "OADIID:GNOME_FastUserSwitchApplet"
Delete/Don't Delete

"The panel encountered a problem while loading "OADIID:GNOME_WorkspaceSwitcherApplet"
 Delete/Don't Delete

"The panel encountered a problem while loading "OADIID:GNOME_Panel_TrashApplet"
  Delete/Don't Delete

"The panel encountered a problem while loading "OADIID:GNOME_WindowListApplet"
   Delete/Don't Delete

[/I][I]"The panel encountered a problem while loading "OADIID:GNOME_WindowListApplet"
    Delete/Don't Delete[/I][I]"The panel encountered a problem while loading "OADIID:GNOME_ShowDesktopApplet"
    Delete/Don't Delete

[/I]On the desktop the time /date info icons in the top right og the screen don't appear and also the whole bottom bar is not showing. I think this is related to the errors above. 
Anyone experienced similar?

kg

---

### Post by linuxopjemac on 2009-12-04
These issues are related to your dead PRAM battery. Once you have that working, your Gnome won't give those error messages anymore.

You can also set up NTP before Gnome is loaded. In that case you will always pick up the right time, and Gnome won't complain.

---

### Post by kg3000 on 2009-12-04
Thank you for your reply.

Could you explain to me how to set up NTP? 

It would be really appreciated.

Thanks again,

kg

---

### Post by linuxopjemac on 2009-12-04
[https://help.ubuntu.com/community/UbuntuTime#Time%20Synchronization%20using%20NTP](https://help.ubuntu.com/community/UbuntuTime#Time%20Synchronization%20using%20NTP)

You will need to setup a working network before you get into GNOME, i.e. you need to have /etc/networking/interfaces setup correctly, otherwise ntpd cannot get it's time/date information during boot. Î hope you know how to do this. Otherwise you can google a bit about this. Maybe I can help, provided that you don't have wireless connection with WPA(2). That you have to ask someone else/google.

---

### Post by kg3000 on 2009-12-04
Thanks for your help. 

I am a little bit stuck on this (as a first-time linux user) but I will see if I can get a network working using a standard network cable.

kg

---

### Post by kg3000 on 2009-12-04
update:

Just plugging in my local network cable and starting up the computer and the errors mentioned above do not appear. The applets seem to be working.

I'm not sure if all the issues are completely resolved as the fan seems to be stuck on full power (a similar problem mentioned earlier in this thread) and the machine switches itself off after a few minutes.

Many thanks for all your help,

kg

---

### Post by linuxopjemac on 2009-12-04
try the following in 

```
sudo nano/etc/networking/interfaces
```

then add the following lines:

```
auto eth0
iface eth0 inet dhcp
```

see [here]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/")

---

### Post by kg3000 on 2009-12-04
Thank you. 

I think the machine was switching off because it was over-heating... I have created a stand (one cake rack and a phone book) which allows airflow underneath the machine. 

It seems to be working better since then, I know the aluminum powerbooks are famous for over-heating. 

kg

---

### Post by svtguy88 on 2009-12-04
^^^Even with the fan running full speed all the time you get overheating problems? 

Between the fan and the whole computer case being a heat sink, this should not be happening.

My PB gets hot under OS X (as has every one I've used), but the runaway fan seems to keep mine under control in Linux...

---

### Post by kg3000 on 2009-12-04
Sorry I forgot to mention; the fan is now running intermittently. (I didn't find a fix for this it just ran for a long period of time at the initial boot-up and now runs occasionally)

Also, this may not be an overheating problem. 

Did you get the wireless working on your machine?

Thanks,

kg

---

### Post by adamdotanderson on 2009-12-07
I used to have the PRAM problem with my iBook. One workaround I found if I did not have internet access was to change my login session to a xterm session and then run "sudo date mmddhhttyyyy" where mm is a two digit month, dd is day, hh is hour, tt is minute, and yyyy is the year. Of course this would be without the quotes and with the correct time and date. Then I could log out and log back into Gnome just fine. Hope that helps!

---

### Post by .ubik on 2009-12-25
I also got a 12" powerbook, with Fedora 11 installed. I run into this problem every time my powerbooks battery runs out, as this model does not have an internal clock battery. I wonder if it would be possible to change the runlevel sequence to get NTP and network to both load and update the clock before it tries to load X11?

Thanks for the Open Firmware tip btw!

---

