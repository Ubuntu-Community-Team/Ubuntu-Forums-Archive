---
title: "Xine dvd play problem"
date: 2005-03-24
forum: Apple PPC Users
---

### Post by wxm505 on 2005-03-24
Hi I am new to Ubuntu. I  was using Fedora core for a while.
The Xine and totem worked well for playing dvd under Fedora.
But when I use Xine under Ubuntu to play dvd
It player about 15 seconds then pop up a error message : 
Error reading NAV packet.

Then I tired it with Totem. The player closed unexpectly.

error message pop up:

An error occured
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

I did installed the libdvdcss.
So I do not know how to solve it out
Any help???
Cheers

---

### Post by Castaa on 2005-03-25
Xine runs on my 600MHz iBook.  Albeit not very smoothly. :-(

---

### Post by blchalifax on 2005-03-30
if it isn't running smoothly there are a few things I did that seemed to work... most importantly was 

sudo hdparm -d1 /dev/hdc

it turns DMA on for your drive... it's talked about more in depth elsewhere in the forums... I suggest checking it out before trying anything.... but I can now watch movies with no problem so it might be worth your while.

blchalifax

---

### Post by chascon on 2005-03-31
the reason that totem with xine works well is because xine is a 'better' backend (at least in playing encryted DVDs) than gstreamer.  Look around there are instructions on this forum on how to get xine working with totem.  Why not just install xine-ui?
And you have to install CSS, this too is explained.

---

### Post by butchershook on 2005-04-10
I had this problem with xine and xine-ui with some DVDs (even with libdvdcss2 installed). It played intro/logo stuff but then failed to play the main DVD chapters. It gave "The source seems encryted ...bla bla bla" error message at the end.  To get it to work,  I clicked the little "N" button on the xine-ui interface while the introductory logos were playing back and then clicked the "Title" button. The DVD main menu then appeared and playback continued without any more problems. Never had any luck with totem-gstreamer though, it just crashed when paying back troublesome DVDs. VLC (vlc-gnome) works faultlessly but you may need to install 'vlc-esd' if you have no sound.

---

### Post by Castaa on 2005-04-11
[QUOTE=blchalifax]if it isn't running smoothly there are a few things I did that seemed to work... most importantly was 

sudo hdparm -d1 /dev/hdc

it turns DMA on for your drive... it's talked about more in depth elsewhere in the forums... I suggest checking it out before trying anything.... but I can now watch movies with no problem so it might be worth your while.

blchalifax[/QUOTE]

Yep.  I've done that.  What type and speed of CPU are you running?  I believe my CPU is just too slow.

---

### Post by pasha on 2005-04-12
Hi, 

I had this problem until I enabled dma on my dvd drive.
My PC is a PIV 2.6 Ghz with 512 MB RAM.
The other 'old' one is a 800Mhz PIII with 512 MB RAM.
Hope it helps.

---

### Post by kuleali on 2005-04-12
check sudo hdaparm /dev/...

---

