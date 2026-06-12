---
title: "Forum Etiquette &amp; Standards"
date: 2013-09-06
forum: Any Other OS
---

### Post by Mark_in_Hollywood on 2013-09-06
All Philosophy --- All The Time, Folks.

Is there really a way to know how long or how much research a person should perform before coming to this or any other forum and asking for help?

I'm posting this here, because, I'm in my 6th decade and don't want to spend a great deal of time on something as simple as this, below. And I should have been able to find a useful example before 30 minutes of time went by. But, I couldn't.

I have a desktop computer with 12.04 LTS (thank you very much) and I have a Raspberry PI with RaspBMC. I have to copy a file named: dvbhdhomerun into the PI's /etc sub-directory folder from my /home/mark/Desktop/pinetwork 

I have tried:

pi@raspbmc:/$ scp /home/mark/Desktop/pinetwork/dvbhdhomerun pi@raspbmc /etc

and a few other permutations. I'm outta luck and outta time. I'm guessing that I need the partition name that /etc sits in but have no way to find that without another 30 minutes or so. So, here is the problem: 

How many hours of searching go into using _a_ command? This is likely to be a command I will use only once, as after the PI/RaspBMC has this file in it's /etc, the webgui for TVHeadEnd will work, and I will have no reason to use the ssh again. Not for a long time with luck.

Just Sayin' - Mostly a Philsophical Query.

---

### Post by montag dp on 2013-09-07
Assuming you can get into the Pi over the network via ssh, you need to use 

scp file pi@raspbmc:/etc 

Note the colon. And 'file' is the file you want to transfer. You also may need to open up the /etc directory to write access on the pi for it to work, or transfer the file the /home directory instead and then move it to /etc using sudo while using the Pi.

---

### Post by sanderj on 2013-09-07
+1 to montag dp

Furthermore:

Your prompt says "pi@raspbmc:/$", so you're typing this on your Raspi. If so, you're typing it on the wrong computer (well, at least conform what you're describing what you want to do).

You can do it the graphical way: on Ubuntu, start Nautilus -> Files -> Connect to server. Then type sftp://<raspi-IP-addres> . Then: FIle -> Enter Location to manoevre throught the raspi directory structure.

---

### Post by Bucky Ball on 2013-09-07
*Thread moved to **Other OS/Distro Support**.*

> **Mark_in_Hollywood said:**
> Mostly a Philsophical Query.

But a support query none the less. If you'd like me to change the title to reflect this and increase your chances of getting help with it, just ask and suggest a couple of new ones.

For what it's worth, I use Putty to communicate with the Pi most of the time. Good luck.

---

### Post by Mark_in_Hollywood on 2013-09-07
This post is marked as solved because there is no reasonable way for me to determine whether the file is or is NOT required on the Raspbmc's /etc subdirectory.

---

