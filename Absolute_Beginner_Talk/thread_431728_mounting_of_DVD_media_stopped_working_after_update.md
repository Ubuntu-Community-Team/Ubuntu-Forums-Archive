---
title: "mounting of DVD media stopped working after updates and installs"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by kazuya on 2007-05-03
Automounting of DVD media stopped working after updates and installs. I do not know what I changed. I installed NTFS-fuse 3g, and avant, and even reinstalled ubuntu-desktop and kubuntu-desktop.... DVDs still no longer automount nor can I mount them by clicking on the CDROM icon under media>

It worked before. Now, I can burn DVDs with gnome-baker and k3b, cannot view my data from konqueror or nautilus..

How do I resolve this? I bet this would soon puzzle many a new user if not resolved or prevented from happening in later updates....

My issue could stem from using restricted, and multiverse repos though..

What is going on? To Feisty's credit, it used to work before,; After an update or so, it stopped working...

Any ideas? I cannot access my DVD media from the external DVDROM device any longer, but I can burn DVDs and CDs from it.  What is even more interesting is that I can launch data CDs from the DVDROM and view them, but DVDs do not launch when I try to open them...

USing Feisty Fawn, external DVDROM, e17, gnome, kubuntu, fluxbox.

---

### Post by ronb on 2007-05-03
I'm having a similar problem. I upgraded to Feisty recently and now DVDs do not show up in Nautilus or on the Desktop. CDs, however, do show up.

I'm using an internal read/write DVD/CD player and Gnome.

The preferences for Removable Media and Devices show as auto-mounting.

---

### Post by kazuya on 2007-05-03
I shall try copying my fstab file from before over my new fstab to see if that helps. Any ideas guys. Two folks having this same issue. I had this before as well during the Feisty Test stages.

---

### Post by noneofthem on 2007-05-04
Same problem here. Reported this as a bug already. There must be something wrong with the automount system in Feisty. Cannot mount my CD-/DVD-ROM-drive and my external HDD cannot be unmounted. These things shouldn´t happen after the final is out.

---

### Post by kazuya on 2007-05-04
Try it out again. It started to work fine for me again. I do not recall doing anything to make it work though. Cannot complain. I would recommend doing an update if possible and then see if any changes. I should perhaps try testing this out in kubuntu-desktop as on my Ubuntu-desktop it works fine. Perhaps, my issue rose up in my kde desktop environment.. Perhaps, something is still missing there.. I'll find out later today. Tell me if it works for you also....

---

### Post by ronb on 2007-05-05
It seems to be working again here also. I don't know why it failed or why it's back. I'm not really certain that it's completely back because I don't have the original DVDs that wouldn't mount. What I have now is mounting OK. Good enough for now.

---

### Post by kazuya on 2007-05-07
This is pretty complicated problem. I tested gnome on Ubuntu and it mounts and opens the drives no with no issue. However, on kubuntu-desktop, it fails to open or allow me to view the DVD. Why is it successful in Ubuntu, but not in Kubuntu-desktop?

Any ideas? I bet some other guys are having this same issue.

---

### Post by rggavubt on 2007-05-14
I'm having the same problem after I upgraded to Feisty.  I can no longer mount or play DVD's.  Is there any solution to this problem???

---

### Post by kazuya on 2007-05-23
This problem still exists. On Ubuntu's gnome, I can mount my DVDs from external device, from Kubuntu-desktop session, I cannot mount my DVDs.  Why is this? How do we correct this..?

---

### Post by veetz on 2007-05-23
Hi 
I'm having the same problem.
ubuntu 7.04

a cd mounts a dvd doesn't.
not even the origional ubuntu dvd that the system was installed from. 

not a data dvd or a movie dvd. 

worked under 6.06 but no longer...
I'm a real newbie ...if anyone solves this issue...
let me know.
:-)
veets

---

### Post by mthei on 2007-05-23
Hi. I started a thread about this yesterday, as I am also having the same problem, only I have been able to run some data DVDs, the ones that I know were burned with either Nero or the default Gnome CD/DVD Creator. The ones that do not read have been burned with either Roxio (back when I was on Windows) and K3b. Other computers can read these disks with no problem at all.
I've only had this problem since doing a clean install yesterday with Ubuntu 7.10.

---

### Post by kazuya on 2007-05-24
Hey Chief, I would say open up your topic as a new post with a new heading under bugs.
There you can state exactly your symptom and see if any help arises...

Nobody seems to look at this post any longer.. and your issue is slightly different from mine. I was having your similar issue before Feisty was released, but the solutions did not help...Some guys tried alot, but it was to no help and I was impatient and simply reinstalled the new Feisty...

I would suggest looking into the restricted drivers in synaptic and trying out or looking for pmount, etc..and installing that and trying to use that...

But open a new topic explaining that you upgraded from 6.06 to Feisty..

---

### Post by klytu on 2007-05-26
> **kazuya said:**
> Automounting of DVD media stopped working after updates and installs. I do not know what I changed. I installed NTFS-fuse 3g, and avant, and even reinstalled ubuntu-desktop and kubuntu-desktop.... DVDs still no longer automount nor can I mount them by clicking on the CDROM icon under media>

It worked before. Now, I can burn DVDs with gnome-baker and k3b, cannot view my data from konqueror or nautilus..

How do I resolve this? I bet this would soon puzzle many a new user if not resolved or prevented from happening in later updates....

My issue could stem from using restricted, and multiverse repos though..

What is going on? To Feisty's credit, it used to work before,; After an update or so, it stopped working...

Any ideas? I cannot access my DVD media from the external DVDROM device any longer, but I can burn DVDs and CDs from it.  What is even more interesting is that I can launch data CDs from the DVDROM and view them, but DVDs do not launch when I try to open them...

USing Feisty Fawn, external DVDROM, e17, gnome, kubuntu, fluxbox.

I have basically the same issue, but I just noticed it today. I did a clean install of Feisty´s April 19th release when it first became available. DVDs used to mount and automatically play - now they don´t show up in Nautilus and consequently totem won´t play them. However, even though they don´t appear in Nautilus or mount, I can actually still play a DVD with gxine (I installed Xubuntu-desktop in addition to Ubuntu). I just insert the DVD, ignore the fact that it doesn´t appear in Nautilus, open gxine, click DVD from the file menu in its GUI and the DVD plays! Weird.

CDs mount and play normally.

---

### Post by kazuya on 2007-05-29
do a system update. This fixed my issues with the mount issue on both kde and gnome environment... Try thisa and see what happens for you guys...

---

### Post by LaSaDa on 2007-05-29
Hi,
I also have this problem.. (i run feisty dual-booted with Vista) It started when i did run the latest updates. what updates are you talking about?

---

### Post by jrickard on 2007-05-30
Same problem here. Plextor drive.  New install of Fiesty 7.04 64 bit with updates.

Jack Rickard

---

### Post by kazuya on 2007-05-30
Are you folks using gnome or kde? Try both. I am assuming this is issue with mounting DVD from external device..?

---

### Post by LaSaDa on 2007-05-30
i'm using gnome desktop, and it is with an internal drive, but it is possible to "eject" it. it is the drive on my laptop :)

---

### Post by veetz on 2007-05-30
1) I was using 6.06
2) upgraded to 7.04 from an internal combo drive(cd write/dvd read)
3)after upgrade the system would not mount the combo if a dvd was in the drive. Because it was    not mounted it would also not eject.
4)after reading and posting the above post etc I reinstalled 7.04.
5) the next time I booted I left the install dvd in the drive. It got mounted!

try a reinstall of 7.04 if this looks like what's going on with your systems...
It worked for me. I was heading back to 6.06....
veets

---

### Post by mthei on 2007-06-01
> **kazuya said:**
> do a system update. This fixed my issues with the mount issue on both kde and gnome environment... Try thisa and see what happens for you guys...

Thanks for the information.
I had gone back to 6.10 until this bug was fixed, then I upgraded rather than a clean install. My data-DVDs are reading perfectly, plus I'm not having any issues with some of my KDE applications.

---

### Post by klytu on 2007-06-02
> **kazuya said:**
> do a system update. This fixed my issues with the mount issue on both kde and gnome environment... Try thisa and see what happens for you guys...

My issue cleared up with a reboot. Still seems bizarre ...

---

### Post by LaSaDa on 2007-06-02
Hi again, i'm still having this problem, but i messed a little around with my fstab file, and now the dvd movies are able to play through totem and gxine, but they do not show up under "computer" nor do they appear on the desktop.. any ideas??

Here's my fstab:
> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=a23001d0-7495-4c0d-a809-6f5922f0c37b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=04b9ca2d-71e8-4b3f-aa87-2bb94861ed15 none swap sw 0 0
/dev/hda1 /media/Vista ntfs-3g defaults,locale=da_DK.UTF-8 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by LaSaDa on 2007-06-06
please anyone?

---

### Post by Meelis on 2007-06-06
Same here.
Clean insatll Ubuntu 7.04 on the 5th of jun & update.
Can't watch DVD, no avi, no mp3
Automatix2
Can't watch DVD & data DVD, from HDD avi can be watched.
DVD writer & CD writer not mounting (2 min HDD led not blinking on boot-up)
/dev/hdd to /dev/sr0
/dev/hdc to /dev/sr1
DVD writer mounting CD not mounting (1 min HDD led not blinking on boot-up)
Loading CD & DVD on drives, restart, both mounted (extreem speed on boot-up, HDD led starting blinking & ubuntu booting up immediatly WOV ). Cant read data from DVD drive, CD OK.
CD not mounting, DVD mounting (can see file icons from nautilus but not open ..DVD).

Can't see my CD writer model nr.

SCSI Host Adapter
---SCSI Device
------SCSI Generic interface----------**/dev/sg1**
------DVDRW SHM-165H6S----------**/dev/scd0** & **/media/cdrom0** & **/sys/block/sr0**

Mounted DVD rom
[IMG]http://www.hot.ee/meelissoosaar/ubuntu/1-totem%20dvd%20avi.png[/IMG]
[IMG]http://www.hot.ee/meelissoosaar/ubuntu/2-mplayer%20dvd%20avi.png[/IMG]
[IMG]http://www.hot.ee/meelissoosaar/ubuntu/3-vlc%20dvd%20avi.png[/IMG]

Can't mount DVD
[IMG]http://www.hot.ee/meelissoosaar/ubuntu/4-dvd%20mpeg2.png[/IMG]
[IMG]http://www.hot.ee/meelissoosaar/ubuntu/5-dvd%20mpeg2.png[/IMG]

Eject CD from CD rom & reload DVD to DVD rom (DVD mounted)
[IMG]http://www.hot.ee/meelissoosaar/ubuntu/6-eject%20cd%2c%20reload%20dvd.png[/IMG]
[IMG]http://www.hot.ee/meelissoosaar/ubuntu/7-dvd-mpeg2.png[/IMG]

---

### Post by DeathStar on 2007-06-06
Hi,

Not sure if it's the same issue, but I had a problem with DVD's not mounting.

[[COLOR="Blue"]TRY THIS[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2794119#post2794119")

DS

---

### Post by Meelis on 2007-06-06
[COLOR="Blue"][TRY THIS]("http://ubuntuforums.org/showthread.php?p=2794119#post2794119")[/COLOR]

Thanks, this not worked.

CD drive not mounted or-?... But I can use cd drive after restarting computer with cd loaded in.
DVD drive always mounted, but files & folders are gray and 0 byte in size.

I read a little in the forums, seems to be kernel problem.
:(

---

### Post by LaSaDa on 2007-06-07
didnt work for me either.. but my system is up to date, and i have libdvdcss2 installed..
Where are all the geeks, sorry DeathStar thanks for your help, but i had figured that out myself.. we need someone who knows ubuntu "under the hood".. :p

---

