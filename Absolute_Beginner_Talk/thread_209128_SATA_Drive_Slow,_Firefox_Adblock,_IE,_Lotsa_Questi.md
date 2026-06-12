---
title: "SATA Drive Slow, Firefox Adblock, IE, Lotsa Question"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by TorxT3D on 2006-07-04
figured i'd lay em all out for today

---------------------------
heres the performance of my 200GB sda drive

[I]/dev/sda:
 Timing cached reads:   1524 MB in  2.00 seconds = 760.43 MB/sec
 Timing buffered disk reads:  162 MB in  3.03 seconds =  53.50 MB/sec[/I]

wth, this is super slow.  Im running nforce2 abit nf7s v2.0 board.  I think the controller is sil3112a

What can i do to speed this drive up?  Its currently formatted as ntfs and theres too much data on it to try and format to a linux type.  I dont wanna take any risks.
---------------------------
I used the adblock script with my windows firefox and adblock extension.
I tried to install the extension and it gave an error, what is everyone using?
---------------------------
I have to access certain websites that are IE specific only, firefox doesnt display the sites like they should, so what can i do to emulate IE to view these sites?  (other than installing ie and wine)
---------------------------
What are the latest openoffice tweaks to speed it up, i read around about adjusting memory parameters but i didnt know how old the info was.  Is it worth it to uninstall it and use AbiWord?
---------------------------
Are there any XP cursor themes that are true to the XP style?  Ive fiddled with several already and im not pleased
---------------------------
what are the key services to disable for faster bootup thats guaranteed not to cause problems, im just running a regulr ol desktop setup, nothing outlandish.
---------------------------
Is there an equivelent of newsbin pro(newsgroup binary downloader) for linux?


THANKS!

---

### Post by Kilz on 2006-07-04
[QUOTE=TorxT3D]figured i'd lay em all out for today

---------------------------
heres the performance of my 200GB sda drive

[I]/dev/sda:
 Timing cached reads:   1524 MB in  2.00 seconds = 760.43 MB/sec
 Timing buffered disk reads:  162 MB in  3.03 seconds =  53.50 MB/sec[/I]

wth, this is super slow.  Im running nforce2 abit nf7s v2.0 board.  I think the controller is sil3112a

What can i do to speed this drive up?  Its currently formatted as ntfs and theres too much data on it to try and format to a linux type.  I dont wanna take any risks.
---------------------------
I used the adblock script with my windows firefox and adblock extension.
I tried to install the extension and it gave an error, what is everyone using?
---------------------------
I have to access certain websites that are IE specific only, firefox doesnt display the sites like they should, so what can i do to emulate IE to view these sites?  (other than installing ie and wine)
---------------------------
What are the latest openoffice tweaks to speed it up, i read around about adjusting memory parameters but i didnt know how old the info was.  Is it worth it to uninstall it and use AbiWord?
---------------------------
Are there any XP cursor themes that are true to the XP style?  Ive fiddled with several already and im not pleased
---------------------------
what are the key services to disable for faster bootup thats guaranteed not to cause problems, im just running a regulr ol desktop setup, nothing outlandish.
---------------------------
Is there an equivelent of newsbin pro(newsgroup binary downloader) for linux?


THANKS![/QUOTE]

First. Dont play around with the drive in linux if its formated ntfs. Reading is about all you can do. 
Second I use adblock, there is a linux extension. What error did you get?
Third IE is the only browser I know that ignores standerds and displays like it dose. Wine isnt that hard to set up, then use the [ies4linux]("http://www.tatanka.com.br/ies4linux/index-en.html") script. It will be up in no time. But be carefull wine is a bug for bug windows emulator. I wouldnt use it for surfing all over.
Forth Abiword is pretty nice.
Fifth Take a look [here]("http://www.gnome-look.org/") for cursor themes.
Sixth Not sure.
Seventh Search synaptic. Im sure there are a few.

---

### Post by TorxT3D on 2006-07-04
im not gonna try to have write access to it, maybe after i convert to fat32

adblock got installed, mustve been something with the download

Alright, how safe is using ie6 via wine?  I got it setup and i'll only be using it with one specific website.

yea gnome-look is where ive been looking but nothing interesting for my specifics, just wondering if there was an off the wall set elsewhere.

i just dont wanna get into the habit of installing, uninstalling, and losing track of misc files getting stashed everywhere, maybe its my wndows habit.

---

### Post by droogy on 2006-07-04
[QUOTE=TorxT3D]figured i'd lay em all out for today

---------------------------
heres the performance of my 200GB sda drive

[I]/dev/sda:
 Timing cached reads:   1524 MB in  2.00 seconds = 760.43 MB/sec
 Timing buffered disk reads:  162 MB in  3.03 seconds =  53.50 MB/sec[/I]

wth, this is super slow.  Im running nforce2 abit nf7s v2.0 board.  I think the controller is sil3112a

What can i do to speed this drive up?  Its currently formatted as ntfs and theres too much data on it to try and format to a linux type.  I dont wanna take any risks.
---------------------------
I used the adblock script with my windows firefox and adblock extension.
I tried to install the extension and it gave an error, what is everyone using?
---------------------------
I have to access certain websites that are IE specific only, firefox doesnt display the sites like they should, so what can i do to emulate IE to view these sites?  (other than installing ie and wine)
---------------------------
What are the latest openoffice tweaks to speed it up, i read around about adjusting memory parameters but i didnt know how old the info was.  Is it worth it to uninstall it and use AbiWord?
---------------------------
Are there any XP cursor themes that are true to the XP style?  Ive fiddled with several already and im not pleased
---------------------------
what are the key services to disable for faster bootup thats guaranteed not to cause problems, im just running a regulr ol desktop setup, nothing outlandish.
---------------------------
Is there an equivelent of newsbin pro(newsgroup binary downloader) for linux?


THANKS![/QUOTE]
How did you get the performance numbers?  I'd like to check mine.

---

### Post by Kilz on 2006-07-05
[QUOTE=TorxT3D]im not gonna try to have write access to it, maybe after i convert to fat32[/quote] fat32 is your best bet

> adblock got installed, mustve been something with the download
It happens, most of the time extensions in firefox dont error, so I understand

> Alright, how safe is using ie6 via wine?  I got it setup and i'll only be using it with one specific website. Slightly safer than running it under windows, but only slightly. As long as your running it as a user and just for one or two must have sites you should be ok.  Another safe use is if you are using it to see how pages you create look for people with IE. But dont surf all over with it.

> yea gnome-look is where ive been looking but nothing interesting for my specifics, just wondering if there was an off the wall set elsewhere.
[This is my personal favorite.]("http://www.gnome-look.org/content/show.php?content=5533")

> i just dont wanna get into the habit of installing, uninstalling, and losing track of misc files getting stashed everywhere, maybe its my wndows habit.
A good pratice, especialy with the way windows installs things. But if you install a linux program with synaptic and then remove it, it deletes everything it installed. Pretty much the same with sudo apt-get install <packagename> and sudo apt-get remove <packagename>.

---

