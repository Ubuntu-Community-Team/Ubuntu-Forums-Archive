---
title: "Xbox 360 Media Streaming"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by Quicky on 2006-07-31
Searching for 'Xbox 360' on these forums hasn't yielded too many results which isn't particularly surprising considering it's creators, but I am a passionate gamer and I'm very impressed with it. However since my migration to Ubuntu, I've been unable to take advantage of it's media streaming capabilities as I did under Windows.

The 360 allows for music and pictures to be streamed from an XP computer, and worked perfectly well when I ran XP, but since my move to Linux I was hoping to be able to do the same from my Ubuntu machine. I've read about a commercial program called Twonkymedia which can perform media streaming to the 360 (amongst other hardware), and runs under Linux, but my knowledge of installing and configuring software outside of Synaptic is pretty much negligible.

Has anybody here had any experience with Twonky or other media streaming software under Ubuntu to some media hub (not necessarily the 360)? It's a great feature I'd really like to take advantage of, so any help would be appreciated.

Cheers.

---

### Post by PR3DAT0R on 2006-08-02
Thers a program called twonkyvision that works very well with the 360, It's not free though. you can download a free trial here [http://www.twonkyvision.de/UPnP/download-trial.html](http://www.twonkyvision.de/UPnP/download-trial.html) (the trial only lasts 30 min)

---

### Post by Quicky on 2006-08-03
Yeah cheers, I had come across this before and it seems to be exactly what I’m looking for (albeit not free). Trouble is, I’m still quite inexperienced with Ubuntu and had some difficulty installing it and getting it to run. Generally, if a program isn’t available in the repositories, it’s safe to assume I’ll struggle to get it to work.

Has anybody else used Twonky on their Ubuntu machine successfully? I’d be interested in hearing from anybody who has managed to stream music to some other device.

---

### Post by PR3DAT0R on 2006-08-04
ok this is what you need to do. Download this file [http://www.twonkyvision.de/UPnP/trial-download/3.1/twonkymediatrial-i386-glibc-2.2.5.sh](http://www.twonkyvision.de/UPnP/trial-download/3.1/twonkymediatrial-i386-glibc-2.2.5.sh)
then open up a terminal and cd into the download directory and run
sudo sh twonkymediatrial-i386-glibc-2.2.5.sh

---

### Post by kah00na on 2007-07-26
I have been looking for something to do this same thing.  I downloaded the script and made the changes for a non-root user and then ran it.  It hung at the end saying it was starting... I have come to find out that this means it is running.  My xbox360 can now see all my pictures, mp3s (it can't ogg files), and videos.  Pretty sweet and EXTREMELY easy to get running. 

I just wish it was free, but I'm willing to pay for cool apps like this one.

---

### Post by nutz on 2007-08-23
I am using twonkeymedia with my 360 also. I don't mind paying for it since no other native Linux app works so well. I just wish it did transcoding so you could view and play any format. But at least for now I can listen to my music, view some moves and browse pictures on my Ubuntu machine from my 360!

---

### Post by guilly on 2007-08-23
i use tversity thru Vmware... but i've heard that it is supported thru wine as well. 

[www.tversity.com](www.tversity.com)

it does transcoding as well. It'll let you play any video format you wish and not only .wmv.

---

### Post by nutz on 2007-08-23
> **guilly said:**
> i use tversity thru Vmware... but i've heard that it is supported thru wine as well. 

[www.tversity.com](www.tversity.com)

it does transcoding as well. It'll let you play any video format you wish and not only .wmv.

I tried running it through wine and it wouldn't work. Besides I would rather support a native Linux app than a Windows one. Gives developers more incentive to port applications over to Linux.

---

### Post by nutz on 2007-08-23
What is the easiest way to get twonkey to run on startup instead on manually launching it every time?

---

### Post by Acglaphotis on 2007-08-23
System>Preferences>Sessions

---

### Post by nutz on 2007-08-23
> **Acglaphotis said:**
> System>Preferences>Sessions

I already tried that; perhaps I am using the wrong command. This is the command I am using...

sudo sh /home/nutz/twonkymedia-i386-glibc-2.2.5.sh

Is it failing because of sudo? I noticed it does not ask me for my password.

---

### Post by phyrewall on 2007-08-24
if you need to sudo to get twonky to load, try using **gksudo **instead of **sudo**, it'll pop up a gui window asking for your password.

---

### Post by guilly on 2007-08-24
> **nutz said:**
> I tried running it through wine and it wouldn't work. Besides I would rather support a native Linux app than a Windows one. Gives developers more incentive to port applications over to Linux.

I'd love to support a native app instead of windows... if there was one, how much does twonky cost? and is there a good open source convertor that convert my videos to wmv format?

thanks

---

### Post by Acglaphotis on 2007-08-24
Mencoder and ffmpeg both can, i think. But twonkymedia is cool.

---

