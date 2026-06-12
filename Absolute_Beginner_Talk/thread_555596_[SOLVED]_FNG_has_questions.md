---
title: "[SOLVED] FNG has questions"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by PIMPINLINUX on 2007-09-20
hey everyone, I am new to Linux, I read that it is more reliable, and it runs much better than windows,  but how diffiicult would it be for me to  change from Windows to Ubuntu? No dual boot, nothing like that, just Ubuntu running the show. Mind you I have a old dell P4 1.9mhz, with about 768 megs of memory. Could it be a problem? Will I able to interact with my windows based laptop when I plug in to my home network? The reason I will keep the laptop windows because of my wife, so she can still have  a computer to use. By the way, I love this forum because no one here trys to belittle you even if is a dumb question!!

---

### Post by Pumalite on 2007-09-20
No problema. Tell me your specs. You can communicate with Windows through Samba.

---

### Post by PIMPINLINUX on 2007-09-20
well it is a dell deminsion, p4 with 768 megs of ram, it is about 5 years old, 80 gig hard drive. has a 64 meg video card and a generic network card. Also a stata cruz sound card.  What kind of other info do you need? I can use a computer, but you have to break it down and tell me exactly what you need to know. By the way, thanks for the help!!!:)

---

### Post by hyper_ch on 2007-09-20
you must know that you cannot run windows programs on linux (well, there are some ways) but generally you can't.

---

### Post by PIMPINLINUX on 2007-09-20
OK, the only thing is if I can find some thing that will replace what I currently use, then it will be ok. But I do listen to music, burn cds and dvds and internet etc. I do not do alot of heavy duty computing. I dont even play games, just work and play music.  ohh I also have itunes for my ipod. is there a linux version or there a llinux replacement for itunes?

---

### Post by hyper_ch on 2007-09-20
Listening music: Amarok
Burn CDs/DVDs: K3b
Internet: Firefox / Opera
Email: Thunderbird / Evolution / Kontact
iTunes: Amarok

---

### Post by Pumalite on 2007-09-20
If dual booting XP: defrag several times, erase all temp files, then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Right click on XP partition, on the menu, choose: 'resize' partition.

---

### Post by PIMPINLINUX on 2007-09-20
Amarok will work with my ipod!! cool!!
thanks for the help, and i will keep everyone posted on my Ubuntu progress!!!

---

### Post by hyper_ch on 2007-09-20
Well, I read so in the forums and [wikipedia]("http://en.wikipedia.org/wiki/Amarok_%28software%29") also says it:

> 
Although a more technical list of features is listed below, here are the primary functions or uses for Amarok:

Playing media files in various formats including but not limited to (depending on the setup) FLAC, Ogg, MP3, AAC, WAV, WMA, and Musepack. Note that Amarok will not play digital music files embedded with DRM. 
Tagging digital music files (currently Ogg, WMA, AAC, MP3, and RealMedia). 
Associating cover art with a particular album, and retrieving the cover art from Amazon.com 
Creating and editing playlists, including smart and dynamic playlists. The dynamic playlists can use such information as the "score" given to a song by an Amarok script, and the playcount which is stored with the song. 
**Synching, retrieving, playing, or uploading music to digital music players, such as iPods or Creative Zens.**
Displaying artist information from Wikipedia and retrieving song lyrics. 
Last.fm support, including submitting played tracks (including those played on some digital music players) to Last.fm, retrieving similar artists, and playing Last.fm streams. 
Podcast 


---

### Post by PIMPINLINUX on 2007-09-20
I just went to the web site and saw the little ad that told you more about amarok. Too cool!!!

---

### Post by Pumalite on 2007-09-20
If you want your Amarok to play MP3 files; the first thing you have to do after you install Ubuntu is go to the Terminal:

sudo apt-get install ubuntu-restricted-extras

---

### Post by PIMPINLINUX on 2007-09-20
and what does that do?

---

### Post by hyper_ch on 2007-09-20
install codecs so that you can listen to mp3s ;)

---

### Post by PIMPINLINUX on 2007-09-20
what about viruses? is linux much made to with stand viruses, or do I still need to get an anti-virus program. I think AVG has a linux version.

---

### Post by Pumalite on 2007-09-20
Forget antivirus; you don't need it in Linux, unless you are connected to a Windows LAN or Server.

---

### Post by PIMPINLINUX on 2007-09-20
what about my home network? And being that I will have a windows computer still on the network, will it still not need it?

---

### Post by Pumalite on 2007-09-20
You need a Firewall and good anti virus in your Windows machine, but if you have a home LAN, I assume you have a router and therefore a hardware firewall, which is more than you'll ever need for Linux.

---

### Post by PIMPINLINUX on 2007-09-20
Well my windows has Grisoft AVG and you are right, I have it all hooked up to a router, so it is settled, no anti-virus!!! Very nice!!
:)

---

### Post by Pumalite on 2007-09-20
Then use the 'Thread Tools' and mark it as Solved.

---

### Post by PIMPINLINUX on 2007-09-20
One more thing, is Redhat Linux similar to umbuntu? or is that just a brand of linux? Can other programs that are made for linux work on all other brands of linux?

---

### Post by Pumalite on 2007-09-20
No. You have to choose your distro and stick to its repositories. I wouldn't go near RedHat. You are fine in Ubuntu. I have tried them all and I'm here.

---

### Post by justin whitaker on 2007-09-20
> **PIMPINLINUX said:**
> One more thing, is Redhat Linux similar to umbuntu? or is that just a brand of linux? Can other programs that are made for linux work on all other brands of linux?

Yes, it is similar. All distributions are somewhat similar: they use the Linux Kernel, have the Xorg graphical server, have a desktop, etc....they mainly differ in the type of package management they use, and on details.

Red Hat/Fedora compiles their own applications, and uses the Red Hat Package Manager, or [RPM ]("http://www.rpm.org/") for its programs. Ubuntu is Debian based, so it uses the [.deb]("http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html") format...the underlying software (Amarok, for example) does not change. 

You can use [alien]("http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/") to install packages from other distributions. Alien converts the file to something apt can use, then you can install it.

Generally, Pumalite is right: check the Ubuntu repositories first before going to grab files from source or another distro.

---

### Post by PIMPINLINUX on 2007-09-20
sound easlier to use Ubuntu than ty to do that other stuff. Is there more of the Debian based programs or more of the RPM? or being that RPM is a redhat thing, there will be more Debian ?

---

### Post by PIMPINLINUX on 2007-09-20
Also when I try to install Ubuntu, do I need to format my whole HD or do I need to something special?

---

### Post by Pumalite on 2007-09-20
Do you want to install Ubuntu solely? (highly recommended)

---

### Post by Pumalite on 2007-09-20
Do you want to dual boot?

---

### Post by PIMPINLINUX on 2007-09-20
I want just Ubuntu on my computer. No dual boot.

---

### Post by Pumalite on 2007-09-20
Get Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Boot from it, delete all partitions you might have, then make one large partition of your entire disk, formatted ext3 if you want, then install Guided>Use Entire Disk, and you are done!
.

---

