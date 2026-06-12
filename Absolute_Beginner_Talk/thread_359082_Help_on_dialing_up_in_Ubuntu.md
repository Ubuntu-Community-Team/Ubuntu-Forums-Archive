---
title: "Help on dialing up in Ubuntu"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by jcloud on 2007-02-11
Hello,

I have successfully installed Ubuntu 6.10 on my PC, deciding to do so after Windows XP caught a very BAD virus that refuses to be scanned or removed by any virus programs... even online ones.

However, I cannot get online with this PC. Ubuntu successfully discovered my modem and I set up the dial up connection in the Networking utility (enable connection, username, password, checked everything, etc). Yet this alone does not allow my PC to dial up when I start the Firefox browser. 

I tried using the wvdialer but every port I tried (0-4) refused to dial anything up with the pon command. My modem seems to be on it's own port, "/modem".

I looked up some things and saw that I might need Gnome-PPP utility to dial up in Ubuntu as this particular distribution of Linux has alot of problems getting online with a dial up connection straight from the install.

So I downloaded Gnome on another computer (I've been using my old Sega Dreamcast to browse the web from home, I know I know /laugh) and tried to install it but got an error. Here were my steps:

1) Opened up the .tar package of Gnome PPP into a folder named Gnome_PPP on my desktop.

2) Used the terminal to switch to the folder:
cd /home/myname/Desktop/Gnome_PPP/
(this took me a very long time as I am horrible with Command line interfaces).

3) Typed in:
./configure
Just as the installation readme said to do.

4) After a while of setting up the configuration file I got some strange text at the end of the print out in the terminal:

```
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtk+-2.0 >= 2.4.0 libglade-2.0 >= 2.4.0 were not met
Consider adjusting the PKG_CONFIG_PATH environment variable if you installed software in a non-standard prefix.

Alternatively, you may set the DEPS_CFLAGS and DEPS_LIBS environment variables to avoid the need to call pkg-config
```

As a complete noob to Linux (I've been using it for 4 days now), Command Line Interfaces, and installing anything on Linux I have no idea what this could mean. All I know is it stopped my PC from configuring the install file for Gnome PPP so I cannot make the install in the terminal.

Can someone please point me in the right direction of what I am supposed to do or if I am doing anything wrong?

Thanks,
j

---

### Post by shareMenaPeace on 2007-02-11
For the virus, some virus write themself into the MBR (where the GRUB boot loader is too).
Did you tried

```
pppoeconf
pon dsl-provider
```

EDIT
And the GRUB updated the MBR so i think it is gone :) (If it ever was a MBR virus)

---

### Post by pistcivet on 2007-02-11
```
sudo wvdialconf /etc/wvdial.conf
```If that finds a modem, you can edit /etc/wvdial.conf
then dial with```
sudo wvdial
```

Have you looked here yet:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

If you can get that to work, I might have a few more tips.

---

### Post by jcloud on 2007-02-11
WOW! Very quick answers.

Thank you very much.

I will give the WVDIAL another shot and see if that works. I do know that my modem is on /dev/modem but what exact port it is on is something I don't know.

The virus is still there unfortunately.

To get rid of it I have:

Reinstalled XP
Reformatted and reinstalled XP
Reformatted, zeroed out the drive and reinstalled XP
Installed Linux on top of it and just now I set up a dual boot with XP on the drive.

When I load up XP the 3.5" floppy drive still spins like mad, the Spyware Doctor still reports crap messing with it's database files, and my antivirus refuses to even load after the first scan lol.

Oh well. At least when I boot up Linux nothing acts up!

---

### Post by oilchangeguy on 2007-02-11
if you've reformated the drive correctly the virus should no longer be there. are you using a factory restore disc? or a stand alone xp disc? with the xp only disc you can delete the partition, and start fresh before you format. with the restore disc you're probably just re-loading the os with out deleting the partition and creating a new partition and formating.

---

### Post by jcloud on 2007-02-11
> **oilchangeguy said:**
> if you've reformated the drive correctly the virus should no longer be there. are you using a factory restore disc? or a stand alone xp disc? with the xp only disc you can delete the partition, and start fresh before you format. with the restore disc you're probably just re-loading the os with out deleting the partition and creating a new partition and formating.

I used the Ultimate Boot CD to delete the partition and zero out the hard drive, then reinstalled windows with a full reformat. I think that would be enough? Is the virus attaching itself to other things like USB flash drives and CD-R's that I used to back up my pictures and MP3s? All the virus scanners can't find anything on those either?!

Anyways, back onto the dial up problems...

Ubuntu recognizes my modem in the Networking tool on /dev/modem/ ppp0 but won't dial out with Modem Monitor tool (it has the Activate and DeActivate buttons greyed out, but on configure it takes me back to the Networking tool settings). I checked the Hardware configuration and here is where I found my modem:

nForce2 External PCI Bridge
|
--> ES2989 Modem

I used WVdial's config and it said it didn't see a modem at all. 

My modem is a Broadxent PCI-bus modem I bought a while back. Did Ubuntu load it with an incorrect driver?

On Windows XP my modem is recognized as ESS ES56T-PI Data Fax Modem in Device Manager.

Can anyone make sense of this? I am a bit confused as to how Ubuntu would find my modem on the PCI-bus slot but won't use it.

Again, thank you.
- j

---

### Post by shareMenaPeace on 2007-02-11
This seems to be the modem
[http://www.pcidatabase.com/search.php?device_search=1&device_search_str=ES56T-PI&sort=chip_description](http://www.pcidatabase.com/search.php?device_search=1&device_search_str=ES56T-PI&sort=chip_description)

HOWTO: Using Option 3G PCMCIA card on Edgy - link found in below post
[https://help.ubuntu.com/community/forum/hardware/Option3gCard](https://help.ubuntu.com/community/forum/hardware/Option3gCard)

Modem will never work in ubuntu?
[http://ubuntuforums.org/showthread.php?t=59717&highlight=Broadxent](http://ubuntuforums.org/showthread.php?t=59717&highlight=Broadxent)

Well i have no idea if this is correct but see for yourself maybe try a google search aswell for the device name and linux/ubuntu or mabye someone else has more infos.

---

### Post by oilchangeguy on 2007-02-11
if you've got the factory restore disc or a windows xp only disc. you don't need this ultimate boot cd, which may be the reason you've still got a virus. and will continue to have a virus until you do a proper windows re-install, 'cause if the virus screws up your hard drive bad enough you may not be able to get ubuntu to load either.

---

### Post by shareMenaPeace on 2007-02-11
> **oilchangeguy said:**
> if you've got the factory restore disc or a windows xp only disc. you don't need this ultimate boot cd, which may be the reason you've still got a virus. and will continue to have a virus until you do a proper windows re-install, 'cause if the virus screws up your hard drive bad enough you may not be able to get ubuntu to load either.
No, windows executables (eg. virues) dont effect linux file systems.

---

### Post by jcloud on 2007-02-11
I have a standard Windows XP disc.

Like I said before I just did a normal reformat/reinstall from the XP cd.

Still there.

Then a partition delete/reformat/reinstall from the XP cd.

Still there.

Then a partition delete/zero'ed out hard disk with the Ultimate Boot CD and then reformat/reinstall from the XP cd.

Still there.

Then a partition delete/zero out/reformat/install of Ubuntu Linux Edgy.

Then a partition delete/zero out/reformat/install of Windows XP.

Then an install of Ubuntu Linux Edgy on top of that.

Still there on the Windows XP partition left over after installing Ubuntu again.

------------------------------------------------------------------------------------------

Symptoms of the virus (only on Windows XP, not on Linux) are this:

3.5" floppy drive spins randomly by itself (no disc in drive, I don't use it anymore).
3.5" floppy drive spins really fast when loading up an anti-virus program.
3.5" floppy drive spins when scanning with any spyware/malware/antivirus program.
Sometimes Spyware Doctor will report that something is messing with it's databases, a known malware activity.
Windows Malicious Software Removal tool caught it on one of the reformats but said it could not remove this type of virus, it also did not say what it was.
3.5" floppy drive spins when downloading and installing any update from Microsoft.
3.5" floppy drive spins when accessing the Microsoft Windows Update website.
I've tried Avira, AVG Free, PC Tools Antivirus, PC-Cillin, and Norton to try and remove this bug. None of them will detect it.

What happened was, I lost a critical piece of Adobe software (someone stole it from my room) and having spent ALOT of money on it I went in search of another copy. But I had to crack this copy... so I went to a site that my browser informed me was "suspicious" and when I downloaded and activated the crack my anti-virus and everything went crazy. Then when I did a full scan nothing was found and then all of my anti-virus/malware software said that my system was fine... then my floppy drive started to spin. I looked it up and some Anti-Virus websites said that was activity from a virus hiding itself from scanning.

Apparently it's a brand new virus as nothing will find it.

------------------------------------------------------------------------------------------

None of the symptoms show up in Linux so I was going to just go ahead and use Ubuntu for everything.

Now I know that even Linux won't really "get rid" of the virus and I know the OS isn't affected by the virus but I am afraid that just having it in my hard drive will spread the virus if I need to share files like a text document or pictures or what have you with someone else.

I don't know if any of my files I backed up (music, pictures, artwork [graphic artist here], and many text documents that are important to me) have the virus on it as well or even if the virus can spread that way. The symptoms of the virus show up whether I use my backed up files or not after a full format and reinstall.

Anyways, it looks like I might need to get a new hard drive, and I might just get a new modem as well then.

-------------------------------------------------------------------------------------------

It looks like my modem is one of the evil ones that just refuse to work in Linux.

/sigh

Oh well, thanks for the help guys! I really do appreciate it.

-jcloud

---

