---
title: "(Newbie) Concerns Before Installing Ubuntu 6.06"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by trenog on 2007-01-18
Alright. Since my nice post got vaporized in my stupidity, I'll make this as brief as possible.

Ubuntu looks interesting, Vista looks like it's in bed with DRM. I may be wrong, but at least right now I want to try Ubuntu 6.06 dual booting with my existing Windows XP system.

I have two harddrives, 1x 40GB NTFS with Windows XP, 1x 250GB NTFS with "My Documents".

Fat32 looks like it is crap compared to ext3 and ntfs. Is this so? If so, I want to either migrate my personal data to an ext3 partition and have Windows XP still see it, or keep it on the ntfs partition and have Ubuntu still see it. I know of two helpers with those "Ext2 IFS", "Paragon NTFS for Linux 5", and a third one that is also like the Paragon software but free and I can't remember it right now.

The only other concerns I have for Ubuntu are the following:

Hardware - DWL-G132 Wireless Reciever, Epson CX3200 Printer, Multimedia Wireless Keyboard, Wireless Mouse, USB Flash Drives

Software - Good mp3+wma player, Good wmv+mov+avi+mpg player, good dvdr+cdr burner, good java ide, good c++ ide, good messenger im client, good instructions on making the desktop look cool

Can I get some wisdom and some help please?

Thanks

---

### Post by nsleiman on 2007-01-18
well u can do this,

give a partition (10gb is more than enough) to your linux partition (ext3?) and have a swap partition (also for linux, double size of your RAM), personally i still have a partition for sharing between windows and linux (and its fat32) because if you attempt to write on ntfs from linux, you may end up with a corrupted thing :)

have windows installed first!

as for sofware, u dont even need maybe for any driver at all to install manually; wireless mouse, wifi*
MSN: i use kopete, i connect msn/icq/yahoo mesengers to it.
Media player: Amarok! (the best ever)
JAVA; i have java5 JVM, IDE: Netbeans and Eclipse
GCC: built in!
....

not to mention all great other softies :)

good luck

---

### Post by Spr0k3t on 2007-01-18
I'm a new user so I'll give you a good view of things to come when you do the install.

Vista is a DRM with an operating system enveloped around it.  The DRM removes your rights to do what you want so they (RIAA/MPAA/Microsoft/Whoever) can sell you a service which unlocks those rights they've legally stolen (a la DMCA).  You can dual boot if you want, but I keep seeing more and more reasons to drop Windows completely.  I went cold turkey.

EXT# is a journaling filesystem, that's about all I know.  I'm sure others will chime in with their views and offer a good comparison of the whys and hows.  I've seen nothing but awesome guides and how-tos galore in these forums.

You don't need to worry about mp3, mov, avi, mpg, dvdr/cdr burner, ide im clients and whatnot.  You may want to ditch the wmv and wma but you might be able to find codecs for those as well.  I've found very few things that will not work with Linux in some way or another.  Even then, I've found alternatives which make it futile to bother trying.  The best IM client I've found anywhere is Linux... and take your pick of the litter, lightweight, non-clunky, multiple IM supported clients to boot.

All of my wireless USB stuff works so far and the flash drives have not given me any problems.  They are even formated NTFS.

---

### Post by oracle5 on 2007-01-18
Mplayer or Vlc would be good for all the video formats. I personally like vlc better but try both and see what works best for you. I haven't used mp3 in a long time since ogg is better but I think rhythmbox will play them fine even though it seems like i'm the only person who likes rhythmbox. K3b is the best for burning dvd/cd in my opinion over all other ones only any operating system. For Im you could use gaim, kopete, and many others.

oracle5

---

### Post by crispy_420 on 2007-01-18
I would use ext3 for shared data. The drivers for Win to read/write ext3 are more stable than ntfs for linux. This is due to one thing, ntfs is reversed engineered when ext3 is open source. For software to read ext3, look at sourceforge for go free solutions. fat32 is almost universally read/write, only a few downsides: fragmentation & 4GB file size limit.

_HARDWARE:_

Multimedia Keyboard = easy setup in gnome (system -> preferences -> keyboard shotcuts)
Mouse = depending on model you can setup "extra" keys just as in windows
USB flash drives = they are usually formatted as fat32 and instantly recognized
wireless = might need some work and walkthroughs (hopefully native linux driver, if not ndiswrapper)

_SOFTWARE:_

mp3 player: xmms or beep (wma is not that great and may have DRM)
messenger: gaim (OS independent, can try for windows)
CD/DVD burner: k3b
movie player: mplayer, xine. vlc (good after codecs installed like win32, libdvdcss, lame, etc.)
desktop appearance: many good guides depending on what you are looking for)
java/c++: can be run natively

Hope that helps.

---

### Post by cairnsww on 2007-01-18
I suggest that you check your USB devices (using a live CD) before committing yourself to Dapper. There are a few people who have reported problems (I am one of them) in accessing USB drives from old machines. I have been forced to abandon Dapper on that machine as a result.

---

### Post by Tux Aubrey on 2007-01-18
Not sure about the rest of the hardware, but I had to abandon my wireless keyboard - driver only loaded when booting into Ubuntu - therefore I had no option selection in grub, just the default.  Mind you, I didn't really try to get it working as I didn't like it much anyway!

---

### Post by jd65pl on 2007-01-18
For software see this [http://jamie.dumbill.googlepages.com/ubuntusoftwaresuggestions](http://jamie.dumbill.googlepages.com/ubuntusoftwaresuggestions)

To check hardware compatibility see this [http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)

---

### Post by sm1thson on 2007-01-18
> **trenog said:**
> good instructions on making the desktop look cool

search for 'beryl xgl' in youtube and you will see just how cool you can get it looking! -that should give you the motivation to get everything above working first! for future referance here is the guide for installing beryl: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu")

---

### Post by laidback on 2007-01-18
Suggest K3b (sometimes written KIIIb) for DVD/CD burning. You may need KDE installed as well as Gnome, i.e. Kbuntu. This can be done via Synaptic, search for Kubuntu. I have both but use Gnome as default desktop. K3b loads within Gnome, as do other KDE applications.

---

### Post by dwblas on 2007-01-18
You might want to download knoppix and burn it to a cd.  Reboot from the cd, and if knoppix can see everything, you shouldn't have any problems with Ubuntu.  Knoppix is KDE, like KUbuntu so it will appear different than Ubuntu, but all you care about is if it recognizes everything.

---

### Post by dwblas on 2007-01-18
Sorry, here are the links:
[http://www.knoppix.org/](http://www.knoppix.org/)   --> click on the appropriate language's flag
[http://www.knoppix.net/](http://www.knoppix.net/)

---

### Post by trenog on 2007-01-18
I have a knoppix cd lying around somewhere so I'll put that in and test it out on my machine. And yes, I will make sure to test out the Ubuntu Live CD before I install to make sure I like what I see.

Also, I was wondering about uTorrent. I really like its low-resource nature and want to be able to use that in Ubuntu as well. Are there any proven solutions for it?

Ultimately, my greatest concern would be for my internet activities since I'm always on it. That's why I mentioned my WiFi receiver by name. I want to be able to not spend any additional money if I don't have to.

Thanks for all the replies so far by the way.

Edit: Also, what is this technique I've heard in brief about storing user settings in a separate place so that when upgrading the Ubuntu OS, the settings remain in place and aren't lost or overwritten?

---

### Post by butchd on 2007-01-18
I don't think anyone has posted on Automatix, but it really saved me a lot of time when setting up my IBM ThinkPad 600e---sound card, etc. Here is a guide on installing it: [http://ubuntuforums.org/showthread.php?t=190025]("http://ubuntuforums.org/showthread.php?t=190025")

---

### Post by pissedoffdude on 2007-01-18
> **trenog said:**
> I have a knoppix cd lying around somewhere so I'll put that in and test it out on my machine. And yes, I will make sure to test out the Ubuntu Live CD before I install to make sure I like what I see.

Also, I was wondering about uTorrent. I really like its low-resource nature and want to be able to use that in Ubuntu as well. Are there any proven solutions for it?

Ultimately, my greatest concern would be for my internet activities since I'm always on it. That's why I mentioned my WiFi receiver by name. I want to be able to not spend any additional money if I don't have to.

Thanks for all the replies so far by the way.

Edit: Also, what is this technique I've heard in brief about storing user settings in a separate place so that when upgrading the Ubuntu OS, the settings remain in place and aren't lost or overwritten?

Personally I use azereus to download torrents as their is no linux native utorrent.  However, I believe that you can run utorrent using wine.  The technique that you are probably talking about is having a separate /home partition.

---

### Post by dannyboy79 on 2007-01-18
i use bittornado for torrents. as for keeping your settings seperate that's right and is a great idea. you will want to have a partition for your /home directory along with your root partition and your swap parition. so you'll have 3 paritions. /, /home, and your swap parition. I actually created a /boot partition also but it's all about personal preference. the other advantage of having /home seperate is that some  people have even said that you can install another distro and it will still work. as for your comment, "Ultimately, my greatest concern would be for my internet activities since I'm always on it. That's why I mentioned my WiFi receiver by name. I want to be able to not spend any additional money if I don't have to." I would strongly suggest trying out a live cd first before diving in. this will tell you what will work out of the box and what won't.

---

### Post by arnieboy on 2007-01-19
> **butchd said:**
> [http://ubuntuforums.org/showthread.php?t=190025]("http://ubuntuforums.org/showthread.php?t=190025")
That thread is way outdated and will not work. 
Please redirect all users to the following link in future:
```
http://www.getautomatix.com
```
Thanks

---

### Post by butchd on 2007-01-19
Thanks for the link, dude.

---

### Post by laidback on 2007-01-20
I used Automatix for my Codecs solution (DVD, MP3 etc). I had no problems but other people report issues with it.

---

