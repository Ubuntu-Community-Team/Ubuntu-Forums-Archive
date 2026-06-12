---
title: "Help a Newbie Get Media?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by Genotrius on 2006-12-24
I'm new to Linux, and I'm using Xubuntu Edgy Eft on a very old PC, which I got for $10 at a garage sale. It has an ethernet PCI card in it, but I can't seem to get the internet on it (no doubt a hardware problem- not what I'm trying to solve here.) 
I've been tryng to get media support on it by installing the gstreamer (etc., etc., etc.) packages, but those packages have all these dependancies, and those dependancies all have dependancies, and some of *those* dependancies have dependancies- very ( ](*,)  ) when done with a 128 MD flashdrive, sneakernet, and no idea what I need to install, except what GDebi says. 
Can anyone help?

---

### Post by MkfIbK7a on 2006-12-24
you have the internet on another computer?,
if so download all the dependencies of the internet and install them on this computer

---

### Post by pseudonym on 2006-12-24
You should be able to get the internet on that pc (this of course assumes you connect to the net via ethernet).. what type of nic is in it? type lspci in a console to find out.

---

### Post by Genotrius on 2006-12-24
lspci returns:

00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 47)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C586B ACPI (rev 10)
00:11.0 USB Controller: NEC Corporation USB (rev 43)
00:11.1 USB Controller: NEC Corporation USB (rev 43)
00:11.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
>>>00:12.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78) <<<
00:13.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI]
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)

I've included the rest just in case.

wert613: That's what I've been trying to do, but it's very difficult to do with a 128 MD flash drive and little idea what you all you need. I was wondering if someone might have a list of everything they downloaded to get media support on Xubuntu, or better yet, an archive of all the packages they used.

---

### Post by pseudonym on 2006-12-24
The 3com 3c905 is a well supported card. Are you sure you're unable to create a network connection? Or do you need some login software for your isp?...

---

### Post by Genotrius on 2006-12-24
You know, that's probably it! I haven't heard much on the ISP our family uses, but I do beleive it's Road Runner, and I think that I've seen some sort of Road Runner disc somewhere, or at least a disc with the Road Runner cartoon character on it. Would that be it?

---

### Post by pseudonym on 2006-12-24
You could try, but I'd be very surprised if they included a linux login client on that disc. This is assuming you need one, of course. In windows, did you have to enter a username/password to get on the net with that isp?

Also, after hooking your modem/router up to this machine and rebooting, check system > network to verify that you have an active network connection...

---

### Post by Genotrius on 2006-12-24
No, I never had to type anything in in windows.
Also, it's kind of a pain to lug everything downstairs, set it up again, and plug it into the router, so I can't check now, but I'm fairly certain that last time I did all that, I pulled up Network and nothing seemed to be different than usual. I have activated the ethernet connection it has listed, and set it on DHCP, but there's no change anywhere from when I had it unplugged.

In Networking on the General tab, what do enetering a Host and Domain name effect, and what does that checkbox do?

P.S. Happy 200th bean, pseudonym!

---

### Post by pseudonym on 2006-12-24
> **Genotrius said:**
> No, I never had to type anything in in windows.
Also, it's kind of a pain to lug everything downstairs, set it up again, and plug it into the router, so I can't check now, but I'm fairly certain that last time I did all that, I pulled up Network and nothing seemed to be different than usual. I have activated the ethernet connection it has listed, and set it on DHCP, but there's no change anywhere from when I had it unplugged.
Hmm... the issue could be with your router then, but I'd try and plug the machine back in again some time and see what happens

> **Genotrius said:**
>  In Networking on the General tab, what do enetering a Host and Domain name effect, and what does that checkbox do?
If you're a home user on broadband ineternet, nothing. The important fields on the next tab are the DNS servers, which you'll see if you get an IP address from your router.

> **Genotrius said:**
> P.S. Happy 200th bean, pseudonym!
Thanks! The champagne corks are popping as I type! :)

To go back to your original post, just a quick tip to enable at least mp3 playback - installing the package 'libxine-extracodecs' should do the trick. I wouldn't worry about all that gstreamer stuff if this is all you want to do.

---

### Post by Genotrius on 2006-12-24
Actually, I picked up libxine-extracodecs earlier, but it wanted me to have libxine-make1 instead of libxine1. I picked up libxine-make1 and tried to uninstall libxine1 in Synaptic and install that, but it said that uninstalling libxine would also uninstall gxine and xubuntu desktop, which sound important.

---

### Post by macogw on 2006-12-24
Do you have access to a computer with internet and a DVD burner?

Main Repo:
[http://torrents.thepiratebay.org/hashtorrent/3552440.torrent/Ubuntu_6.10_-_Edgy_Eft_-_Main_Repository_-_i386.3552440.TPB.torrent](http://torrents.thepiratebay.org/hashtorrent/3552440.torrent/Ubuntu_6.10_-_Edgy_Eft_-_Main_Repository_-_i386.3552440.TPB.torrent)

Restricted Repos:
[http://torrents.thepiratebay.org/hashtorrent/3552441.torrent/Ubuntu_6.10_-_Edgy_Eft_-_UMR_Repositories_-_i386_-_1_of_3.3552441.TPB.torrent](http://torrents.thepiratebay.org/hashtorrent/3552441.torrent/Ubuntu_6.10_-_Edgy_Eft_-_UMR_Repositories_-_i386_-_1_of_3.3552441.TPB.torrent)
[http://torrents.thepiratebay.org/hashtorrent/3552442.torrent/Ubuntu_6.10_-_Edgy_Eft_-_UMR_Repositories_-_i386_-_2_of_3.3552442.TPB.torrent](http://torrents.thepiratebay.org/hashtorrent/3552442.torrent/Ubuntu_6.10_-_Edgy_Eft_-_UMR_Repositories_-_i386_-_2_of_3.3552442.TPB.torrent)
[http://torrents.thepiratebay.org/hashtorrent/3552444.torrent/Ubuntu_6.10_-_Edgy_Eft_-_UMR_Repositories_-_i386_-_3_of_3.3552444.TPB.torrent](http://torrents.thepiratebay.org/hashtorrent/3552444.torrent/Ubuntu_6.10_-_Edgy_Eft_-_UMR_Repositories_-_i386_-_3_of_3.3552444.TPB.torrent)


If you burn those DVDs, you can load them into the drive of the computer where you want to install the codecs and use the DVDs as repositories (just add them in the Repositories dialog of Synaptic).

---

### Post by Genotrius on 2006-12-24
Wow, torrents! I do happen to be using a computer with a DVD burner, but I'm not sure that my mother would appreciate me downloading bittorrent onto her computer... I shall have to find another way, but I will copy those links!

---

