---
title: "A few gaming and music questions"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2006-07-03
Hi, i just made a new ubuntu linux install and i have a few questions.

1. How would i go about setting up mp3 playability in ubuntu?

2. I'm a big Football Manager 2006 fan, how would i go about installing that on ubuntu, or steam for that matter?

3. How would i go about setting up wine?

4. What is the best WYSIWYG editor available on Ubuntu?

Thanks in Advance,
Kris

---

### Post by Jagot on 2006-07-03
Enable the universe repository as described here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then: 

1) [https://help.ubuntu.com/community/RestrictedFormats#head-e18f2d510b1efe975368b818b5aa3ae2b2eee5c8](https://help.ubuntu.com/community/RestrictedFormats#head-e18f2d510b1efe975368b818b5aa3ae2b2eee5c8)

3) ```
sudo aptitude update
sudo aptitude install wine
winecfg
```

---

### Post by woedend on 2006-07-03
mp3 playability is a broad question.  If you install xmms it will play your mp3s by default.  If you want integration into gnome/gstreamer, install the ugly package as suggested.

---

### Post by richbarna on 2006-07-03
Here is winehq's list of games that work, scroll down and you will see the football games :-[http://appdb.winehq.org/appbrowse.php?catId=86]("http://appdb.winehq.org/appbrowse.php?catId=86")

I used Automatix to install codecs for mp3 etc (see my signature for Automatix)
|
|
v

---

### Post by KrisDwyer on 2006-07-03
Hey guys do u know any decent bittorrent programs for ubuntu as well?

---

### Post by richbarna on 2006-07-03
[QUOTE=KrisDwyer]Hey guys do u know any decent bittorrent programs for ubuntu as well?[/QUOTE]
Ktorrent it's in the repos

---

### Post by woedend on 2006-07-03
hey rich isnt there some kind of bittorrent program that comes with dapper?  I remember seeing the init script for it but never using it.

---

### Post by KrisDwyer on 2006-07-03
[QUOTE=richbarna]Ktorrent it's in the repos[/QUOTE]

I'm on hoary, how do i go about getting that?

Also how to i get xmms?

---

### Post by richbarna on 2006-07-03
woedend: "hey rich isnt there some kind of bittorrent program that comes with dapper? I remember seeing the init script for it but never using it."

yeah, bittorrent client.
There is a Bittorrent Gui that can be downloaded from synaptic and also Gnome-btdownload GUI

---

### Post by richbarna on 2006-07-03
> **KrisDwyer]I'm on hoary, how do i go about getting that?

Also how to i get xmms?[/QUOTE]

Open your terminal: Applications/Accessories/Terminal and type (or copy and paste  said:**
> sudo aptitude update && sudo aptitude install xmms

You can also get it in synaptic.

---

### Post by Dazaablack on 2006-07-03
Hey 

76 meg is pretty steep for a torrent program, ahh well I will try out Ktorrent.
It better have a nice interface.

Use xmms. You can get skins for it. But there are not as many as winamp.

sudo apt-get install xmms
(takes a few secs).

Also i got wine working, its pretty easy if you use apt-get. It creates a c drive in a hidden folder in your /home/username/.wine/
and you just exectute windows files as the like. 

$ wine /home/daz/.wine/drive_c/Warcraft\ III/Warcraft\ III.exe -opengl

If you want to play games, I installed warcraft 3 TFT and played a battlenet game about an hr ago, and I have no need to ever go back to use xp again.

---

### Post by woedend on 2006-07-03
right...but only after adding the universe/multiverse repos.  Just follow the link above about repositories if you haven't added them yet.  except naturally if you are on 5.04 use hoary in place of dapper.
i think xmms is in universe(right?) and the ugly codecs are in multiverse if you ever wanted them.
Oh, and once you install XMMS, at least from the beginning set the skin to default away from that cheesy debian aberration.

@Rich - I see, thanks.  Attempting to help from another type distro is hard, I think i'll throw ubuntu back on soon enough.

time for sleep..take care all :p.

---

### Post by KrisDwyer on 2006-07-03
Cheers mate

Would any of you know how to install a .deb?

---

### Post by Jagot on 2006-07-03
[QUOTE=KrisDwyer]Would any of you know how to install a .deb?[/QUOTE]

```
sudo dpkg -i whatever.deb
```

---

### Post by KrisDwyer on 2006-07-03
[QUOTE=Jagot]Enable the universe repository as described here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then: 

1) [https://help.ubuntu.com/community/RestrictedFormats#head-e18f2d510b1efe975368b818b5aa3ae2b2eee5c8](https://help.ubuntu.com/community/RestrictedFormats#head-e18f2d510b1efe975368b818b5aa3ae2b2eee5c8)

3) ```
sudo aptitude update
sudo aptitude install wine
winecfg
```[/QUOTE]

For some reason i cant use 'winecfg' after i installed it.

---

### Post by christhemonkey on 2006-07-03
If you type wine into a terminal, then press <tab> twice, it should list all the commands beginning with wine.
One of which should be winecfg or something like that.

---

