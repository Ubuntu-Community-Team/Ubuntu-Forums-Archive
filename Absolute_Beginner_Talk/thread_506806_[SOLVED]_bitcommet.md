---
title: "[SOLVED] bitcommet"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-07-22
can i use bitcomet with fisty fawn

---

### Post by xpod on 2007-07-22
Fisty fawn?????????

:shock:

You might be able to run it In wine(emulator?) possibly or i know it works fine in virtual box.(virtual machines)
Better yet why dont you try a native torrent app?

Ktorrent(the best imo)
Azureus
Deluge
Torrentflux
Bittornado
rtorrent
qtorrent........

To name a few
Possibly even Opera browser with the built in Bit torrent:)

And just in case none of them suit your needs:)
[http://www.winehq.org/](http://www.winehq.org/)
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by trucker33377 on 2007-07-22
guess i chose it because i know how it works ive always used it. also i know fisty can already download torrents. but its not working right or more likely i dont know how to use it. ive started a download with it and it went ok but if i try to do a second one i get an error message.

---

### Post by ADT on 2007-07-22
> rtorrent

rtorrent is a great recommendation. 

Commandline but very easy to use:

[http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide]("http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide")

---

### Post by trucker33377 on 2007-07-22
ok how do i get rtorrent is there a command for it is

---

### Post by xpod on 2007-07-22
Applications>accesories>terminal

> sudo aptitude install rtorrent

If your not accustomed to the terminal i would really try something with a gui ....at least until you feel more comfortable with the terminal.

Of course it might also be the best thing you could do i suppose:)

The same command above though,replacing "rtorrent" with any of the others i mentioned will install them too.
Or you can find them in synaptic and add/remove

---

### Post by xubu_caapn on 2007-07-22
eh, it doesn't sound like rtorrent is a good solution for you......

I've tried many torrent apps for Linux. I always stay with deluge torrent, here is a package for it (assuming you're on i386): [http://http.us.debian.org/debian/pool/main/d/deluge-torrent/deluge-torrent_0.5.2-1_i386.deb](http://http.us.debian.org/debian/pool/main/d/deluge-torrent/deluge-torrent_0.5.2-1_i386.deb)

download that to your desktop, right click install, then you're good to go.
another good one is transmission: [http://http.us.debian.org/debian/pool/main/t/transmission/transmission_0.72.dfsg-1_all.deb](http://http.us.debian.org/debian/pool/main/t/transmission/transmission_0.72.dfsg-1_all.deb)

if you're on KDE, ktorrent is the best.

---

### Post by RomeReactor on 2007-07-22
> **trucker33377 said:**
> guess i chose it because i know how it works ive always used it. also i know fisty can already download torrents. but its not working right or more likely i dont know how to use it. ive started a download with it and it went ok but if i try to do a second one i get an error message.

Is "**error 98: address already in use**" or something very similar the error message you get with the included BitTorrent client In Feisty? if so, the solution is simple:
* Open a terminal (Applications->Accessories->Terminal) and enter:
```
gconf-editor
```
In it, go to **apps->gnome-btdownload->settings** and change the **max_port** (by double-clicking it) to **6889**.

---

### Post by xpod on 2007-07-22
> if you're on KDE, ktorrent is the best.

Not much KDE round these parts but ktorrent is still the best for me...even in gnome:)

---

### Post by mikewhatever on 2007-07-22
> **trucker33377 said:**
> ok how do i get rtorrent is there a command for it is

Yeah right! All you need after Bitcomet is rtorrent.

---

### Post by trucker33377 on 2007-07-22
b4 i do much more here i need to find out a few things.

 (1) ive downloaded and installed opera is this a good browser for fisty. i used it alot in windows but it didnt download very well for me bitcomet had much better speeds. here it slows down plus i cant open any other web pages i have to reboot to open anything in opera or firefox. i use cable dsl  wireless i should have plenty of band width

 (2) ive done the same for Bittornado, i think cant seem to find it now. i want to be carefull not to make more problems  then i solve here. 

i dont know alot about linux at all so please keep this in mind when offering advice. if fisty has a torrent program worked out i feel i need to just learn how to use it and make it work thanks

---

### Post by trucker33377 on 2007-07-22
> **RomeReactor said:**
> Is "**error 98: address already in use**" or something very similar the error message you get with the included BitTorrent client In Feisty? if so, the solution is simple:
* Open a terminal (Applications->Accessories->Terminal) and enter:
```
gconf-editor
```
In it, go to **apps->gnome-btdownload->settings** and change the **max_port** (by double-clicking it) to **6889**.

ok i did that now i get error 111

---

### Post by weblordpepe on 2007-07-22
I dunno about you guys, but the best torrent program on Windows is uTorrent. uTorrent works perfectly (perfectly) under wine.

It gets better speeds than any native client I've installed. And it sits in the notification tray. Beautiful program.

---

### Post by trucker33377 on 2007-07-22
> **weblordpepe said:**
> I dunno about you guys, but the best torrent program on Windows is uTorrent. uTorrent works perfectly (perfectly) under wine.

It gets better speeds than any native client I've installed. And it sits in the notification tray. Beautiful program.

ok whats wine?

---

### Post by weblordpepe on 2007-07-22
Its what lets you run Windows programs in Linux. It stands for 'Wine Is Not an Emulator'.

Its not an emulator because what it does is provide all the resources that Windows progams need to run properly in Linux. Or at least it tries to. The majority of Windows programs work well in Wine.

You should be able to find it in Synaptic if you enable the Universe repository.
And the homepage is at [URL="http://www.winehq.com"]http://www.winehq.com
[/URL]

---

### Post by trucker33377 on 2007-07-22
i got it now also downloaded utorrent but it stops after about 30 mins

---

### Post by weblordpepe on 2007-07-22
wierd.

---

### Post by misfitpierce on 2007-07-22
forgot Transmission... Very light and fast. Can be found on [http://getdeb.net](http://getdeb.net) Only made for mac and gnu/linux

---

### Post by trucker33377 on 2007-07-22
ok how do i uninstall out of wine now

---

