---
title: "Totem Help --- Totely Lost"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by KrayzeKaliber on 2006-12-25
Happy holidays everyone. Hope you can take some time from celebrating to help me with a problem.

I've previously never watched a dvd on my comp before, and i was just trying to view my dvd on Totem movie player,  After choosing to play the dvd from the Movie menu, I recieve the message: 

> Totem was not able to play this disc Failed to find mountpoint for /dev/hdc

So I look online for the solution and I come across: [COLOR="SandyBrown"][http://www.linuxforums.org/forum/redhat-fedora-linux-help/71813-cd-rom-drives.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/71813-cd-rom-drives.html)[/COLOR]

I end up making the directory /media/test and then executing 'mount /dev/hdc /media/test'. Now I have the cd's content in the folder (VIDEO_TS.BUP, VIDEO_TS.IFO, ...) but now choosing the dvd is no longer an option in Totem! What have I done!?

Some holiday advice-giving is very much appreciated. :-D

---

### Post by doom3d on 2006-12-27
Hello,

I have even more weird problems with Totem player.

- It shows DVD menu, but chapter selection doesn't work (nothing happened)
- When I try to play whole DVD, I receive a nice "Requested audio codec family {mp3} (afm=mp3lib) not avalaible. Enable it at compilation." error message. No mp3 reading support?!
 It plays separate *.vob files with sound, but..
-  it says, that the film is approx. 24 hours long, (5h55 per *.vob file)
- can not jump to a given timepoint 
- sometimes it says, that DVD is not supported media format (??) ](*,) 

Actually I would watch the DVD: Discovery Ch.: Legendary Warriors..  

Doom3d

P.S.  I have Linux since 10 days. Please, help. I want to be MS free..

---

### Post by rajeev1204 on 2006-12-27
that is cos totem sucks!!

install gxine from the repos along with libxinemain and libxineextracodecs . things will run fine.

totem -xine may also work for u instead of gstreamer


also install libdvdnav and libdvdread from repos . 

regards

rajeev

---

### Post by pseudonym on 2006-12-27
Hi,

If you haven't done so already, I highly recommended both of you to read [this wiki entry]("https://help.ubuntu.com/community/RestrictedFormats"). It sounds like at least one of you hasn't enabled mpeg support yet.

I also recommend using either totem-xine or ogle for dvd watching, rather than totem-gstreamer. When you try to install totem-xine in Synaptic you might have to remove the totem you have now, but it's no biggie.

Also, one thing you defintiely do NOT want to do with a media CD or DVD, is mount it. The way the computer reads these discs is different to thge way it reads data discs.

HTH

---

### Post by deep.tinker77 on 2006-12-27
@ Krazekaliber & doom3d:

Guys, just install VLC. I havent had  a single problem playing any kind of dvd, avi, mpeg or whatever else you want to play.

Edit: pseudonym's link is very helpful and will get you up and running in no time :)

---

### Post by r.cannell on 2006-12-28
I too, have had a number of problems with totem (wmv files from a cd in my case). I updated it as per the wiki - still no good. gxine played the file but was very jerky. VLC, however was fine. VLC also worked when playing avi files from a Mustek dv3000 - totem played the movie but not the sound. So, for me, it's thumbs up to VLC and down to the others.
I would like to set VLC as my default player but haven't yet worked out how.

---

### Post by deadgobby on 2006-12-28
Here is a cool DVD program. Ogle. Install Ogle from Synaptic and when it has installed. Place in DVD disc and open up Terminal and type in ogle. You can use your mouse to click on the menu.
Gobby

---

### Post by riven0 on 2006-12-28
Perhaps your dvd is encrypted? Have you tried this?:

> sudo apt-get install libdvdread3 && sudo /usr/share/doc/libdvdread3/./install-css.sh

---

