---
title: "audio and ntfs mounting problems"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by Aybara on 2006-01-17
I'm trying to get my Dell Inspiron 6000 to run Ubuntu, but I have a few problems.

I mounted an ntfs drive with audio/video/photos to try out some multimedia, but I couldn't get any sound. Totem Player whined about not having the necessary codecs, while VLC appeared to play ok, but without me hearing anything... Then I downloaded an mp3 from a website, and it played with sound in VLC. Is it a problem to play media from an ntfs drive? I haven't downloaded any audio and video codecs after I installed. 

I also thought I'd download mplayer, but I can't find it in the packet manager. Which repository do I have to add to get mplayer?

---

### Post by ignorance on 2006-01-17
well i mounted some of the mp3's that i have on my windows disk and they appear to be playing just fine. but are you sure that the mediafiles are mp3's and not wma? But if nothing is working try to install xmms not a bad player

sudo apt-get install xmms
wget -c [http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb](http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb)
sudo dpkg -i xmms-wma_1.0.4-2_i386.deb

then for the codecs (only install those which you will be needing)

sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo cp /usr/share/applications/defaults.list /tmp/defaults.list_tmp
sudo sed -e 's/audio\/mpeg=.*/audio\/mpeg=XMMS.desktop/g' /tmp/defaults.list_tmp > /tmp/defaults.mp3
sudo sed -e 's/audio\/x-mpegurl=.*/audio\/x-mpegurl=XMMS.desktop/g' /tmp/defaults.mp3 > /tmp/defaults.m3u
sudo sed -e 's/audio\/x-wav=.*/audio\/x-wav=XMMS.desktop/g' /tmp/defaults.m3u > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list
sudo rm -f /tmp/defaults.*

hope this helps a bit.

cheerz

---

### Post by Aybara on 2006-01-21
Hi. All worked better after I installed mp3-support...

---

