---
title: "Help me setup PLDT DSL w/ Ubuntu"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-09
I wanna know how to set-up my internet connection! My ISP is PLDT DSL, connection type PPPOE. Anyone from the Philippines that could possibly help me? 
Pls help in a step by step process. I'm really new to this so pls! 
BTW I don't know if my modem is compatible w/ Ubuntu? Basing on the labels on the modem it says its a Nortel Universal Edge 20R. I don't have the manual or the box w/ me.
Another question! How do I move files from Ubuntu to Windows? Coz I have Creative PMC & I transfer some vids & mp3 files there.

---

### Post by Jucato on 2006-07-09
Step by step, as requested:
1. Go to Applications > Accessories > and launch Terminal
2. type in the command line:
```
sudo pppoeconf
```
It will ask for your administrator password (your password)
3. It will then detect your network card/device. If successful (I'm betting it will be), it will ask you for some technical details. It's ok to just accept the defaults. There are 4 questions, though, that you need to take note of:
- it will ask for the username: enter the username for PLDT myDSL
- it will ask for the password: enter the password for PLDT myDSL
- later on, it will ask if you want to connect at startup: meaning you won't have to manually connect to the internet anymore. It will do this automatically. I recommend this, unless you really have a reason not to.
- after that, it will ask if you want to connect now: of course answer yes, because if you answer no, you will have to manually connect.

As for the 2nd question:
Do you want to move files **from** Ubuntu **to** Windows, or from Windows to Ubuntu? If it's the first one, I wouldn't recommend directly moving files from Ubuntu to a Windows partition that's using NTFS filesystem, as that could produce a lot of errors on the Windows side. The only way around that is to use a shared partition which is formatted in FAT32 or get the files from Ubuntu when you are in Windows, using software like fsdriver or explore2fs.

However, I think what you really wanted to ask was how to get files from Windows into Ubuntu (or do I presume too much :D). In that case, it's safer and easier than the first one. Just copy from your Windows partition directly to Ubuntu. Just copy, don't move (because move is equal to copy + delete, which will affect your Windows system).

In the end, I recommend having a separate partition in FAT32, if you are going to share a lot of files between Ubuntu and Windows. FAT32 is the common denominator between the two and is the safest way to share between them.

Hope that helps.

---

### Post by kris2pe on 2006-07-09
LOL! Hard parts over LOL! 
Now wiggle my big toe! [-o< I thought no one would reply! Thanks a bunch! 
I'm actually replying to you in Ubuntu's live cd lol!!! All I have to do is clear my disk & b ready to amaze!!! 
Now what's the best bittorrent client for linux?
BTW yes I want to tranfer linux files to windows. Can I access it more safely w/ fsdriver or explore2fs?
Coz I have Creative PMC & it actually needs wmp10 to convert videos & stuff! 
BTW do I need a firewall linux sorry very ignorant question?

---

### Post by Jucato on 2006-07-09
Best bittorrent client for Linux? I might be a bit biased, but I prefer KTorrent, which is a KDE app. You can safely install it without having to install all Kubuntu/KDE stuff (just the needed libraries). If you have the RAM to burn, you can install Azureus. Just be warned that it uses up a bit of RAM because it uses Java. Ubuntu has a very basic/simple bittorrent client installed by default (you have to make it appear on the menu using Alacarte). The problem with this client is that you need to have one window open per torrent, and that you can't choose which file to download or not to download in a multifile torrent.

It's safer to get files from Linux to Windows using fsdriver or explore2fs, and you have to be in Windows. But it's completely safe to copy (again, copy, not move) from Windows to Linux when you're in Linux. But if you really are going to do a lot of copying back and forth, I suggest you set aside a separate partition for shared files. Probably 5GB would be enough (or too much, depending on the size of the files you need to share). 

You wouldn't really need a firewall (or an anti-virus) in Linux. AFAIK, our DSL modem/routers has a hardware firewall already (not 100% sure). You generally don't need a firewall because of Linux's own safety mechanissms. But if you're a bit paranoid :D, you can install one. Just don't ask me. I don't know how. :D

Btw, there's a [Pinoy Ubuntu Users Thread](http://www.ubuntuforums.org/showthread.php?t=68805). You might want to drop by a bit every now and then. :D

---

### Post by kris2pe on 2006-07-09
I tried fully installing it sa laptop and I notice n slightly mabagal cya! I don't know 256 mb ang ram. Is there a reason 4 this?

---

### Post by Jucato on 2006-07-09
slower than when running it on the Live CD? That's strange, because by all means an installed system should be faster than a Live CD system. 

But 256 RAM is really the minimum recommended memory for Ubuntu and Kubuntu. Don't expect it to fly, though. By the way, having a swap partition should help your memory usage. Did you make one when you installed Ubuntu? I'm not sure, but I think the installer makes a default swap partition even if you didn't specify it. I'm just not sure how much space it creates. When I had only 256MB RAM, I made a 1GB swap space, and usually that's more than enough. Now that I have 640MB, that 1GB is barely used.

But if you don't have plans on buying new RAM in the future, but want a usable system that's really fast and still uses Ubuntu and GNOME, might I suggest you try out Xubuntu. It's an Ubuntu based derivative that uses Xfce for it's desktop environment. It's the perfect desktop for those who want a fast desktop but still want to be able to use GNOME apps (or even KDE ones).

---

### Post by kris2pe on 2006-07-09
Actually b4 I used my pc during the live cd. But the full install was done in the laptop! 
What mtu are using when logging into pldt? 
Coz I notice that the dl speed is slower in Ubuntu than in my xp?

---

### Post by Jucato on 2006-07-09
I forgot what settings were offered to me during pppoeconf. I just accepted the defaults. I find that the internet is a bit faster in Linux than in XP, but the difference is at most times negligible. Btw, my subscription is the 256kbps DSL (Php 999/month).

BTW, desktop PCs and Laptops behave differently when it comes to speed/performance, I think. I'm not sure. I don't own a laptop :(

---

### Post by kris2pe on 2006-07-09
> **Fenyx said:**
> I forgot what settings were offered to me during pppoeconf. I just accepted the defaults. I find that the internet is a bit faster in Linux than in XP, but the difference is at most times negligible. Btw, my subscription is the 256kbps DSL (Php 999/month).

BTW, desktop PCs and Laptops  differently when it comes to speed/performance, I think. I'm not sure. I don't own a laptop :(

Surfing wise ok nman. Pro if you start downloading, that's the time that you'll see the difference kc Im a 512 kc eH!!!
download K sa pc umabot ng like 20-40 d2 halos hindi mka abot ng 15!

---

### Post by shinkaide on 2006-08-07
BTW, if you connect your PC directly to the DSL modem, sometimes hindi mag-au-otokonek yung  pppoe plugin. you gotta open the terminal and type:

[INDENT][FONT="Courier New"]sudo pon dsl-provider[/FONT][/INDENT]

you'll be asked for your password. After that it's okay.

Lately yung myDSL ko nagloloko e. Pag dun sa Ubuntu box ko, kokonek tapos myamya wala nang internet. Pero sa Windows box ko okay naman... nagkalokoloko na!

Apir!

---

### Post by md5hash on 2007-11-18
bump..  how can i have internet connection with this setting

xp -> router - > ubuntu 

xp ip: 192.168.0.1
sub: 255.255.255.0

---

### Post by chinocracy on 2008-03-01
I'd also like to ask any of the Ubuntu gurus here, since I have Kubuntu at home and have tried to use my new Bayantel DSL, though I could not find any GUI connecting program in Kubuntu. Is pppoeconf the only way? I do wait for a more graphical solution to DSL connection for Kubuntu since that is for me is the right direction for development. Thanks.

---

