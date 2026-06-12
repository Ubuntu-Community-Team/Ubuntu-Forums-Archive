---
title: "Is Ubuntu Persistent Boot-up Different on Macs?"
date: 2007-06-11
forum: Apple PPC Users
---

### Post by jimwg on 2007-06-11
Hi All!

After late hours in the night and forsaking lunch hours I managed to partition my 1gig UBS flash drive and got Ubuntu 6.10's Live-CD running off it -- once. The very first time I rebooted with the newly formatted USB , Ubuntu threw me into a custom user environment which was nice. To test out whether the settings stuck in the flash drive, I did all the recommended re-setting and customizing screen and mail and app prefs, and the USB's light flashed as all the info was streaming into the flash drive. One hang-up I had (in testing) was creating several new user names. Some didn't take after I did a log-out log-back in under new user name, and two utterly disappeared from the Group users box. Two's passwords didn't take. It might it to do with wiping Ubuntu as a user name (but remaining root) when i tried renaming it I wonder? But what is most frustrating is after I did full restart, persistence mode doesn't work anymore! Now, when I first booted up from the USB I have to say that the first Unix text screen didn't mention anything about hitting F6 like Ubuntu's own Persistence tutortial stated (F6 didn't work anyway). Instead it mentioned using Tab to push you into the Options listing, and even then I'm unsure whether I typed in Live (space) persistance or persistence or persistent to've gotten in the first time. I tried every space and live and mis-lettered combination of "Persistence" since to no avail. I should've been video taping how I got in the first time because it's not taking anymore. Off Ubuntu, my Mac sees all the Ubunto files and folders all set up in the flash drive ready to go, so unless they're corrupted somehow (would that even affect the kernel's initial options selection and booting to begin with?) I might have do this circus all over. I really am trying to be a Ubuntu hawk here, because its speed and OpenOffice text clarity on my Mac is something else! A princess in distress needs a knight, guys!

I have Live-CD 6.10 with a 900mHz 640meg G3 iBook.

Be grateful for any assist!

James Greenidge

---

### Post by jimwg on 2007-06-13
So much for customer service.

---

### Post by arkstfan on 2007-06-15
> **jimwg said:**
> So much for customer service.

I could be terribly wrong but I was under the belief that a PPC Mac will absolutely not boot off a USB drive (flash drive or hard disk) unless you hold down the OPTION key at boot.

I'm the last person you want helping you but the statement about your iMac seeing the file structure really caught my eye. My iMac does not acknowledge the existence of the Ubuntu files or even partitions on my internal or external firewire drive unless I go into Disk Utility and even then it only shows the partitions exist but no data about contents.

---

### Post by jimwg on 2007-06-15
> **arkstfan said:**
> I could be terribly wrong but I was under the belief that a PPC Mac will absolutely not boot off a USB drive (flash drive or hard disk) unless you hold down the OPTION key at boot.

I'm the last person you want helping you but the statement about your iMac seeing the file structure really caught my eye. My iMac does not acknowledge the existence of the Ubuntu files or even partitions on my internal or external firewire drive unless I go into Disk Utility and even then it only shows the partitions exist but no data about contents.

Hello arkstfan:

I WISH I could boot Ubuntu on my USB flash drive! Since booting on Mac USB is impossible, the second best thing is using Persistence mode, in which your flash drive is configured to be recognized by the Ubuntu live-CD as its start-up driver that holds all the prefs and settings and whatever programs you upload in Ubuntu, all without touching your Mac hard drive! It's almost like magic except for the CD's four-minute boot-up and occassional access, but it beats the hassle of reformatting your main drive! Now, what's probably confusing you is thinking my Mac can read or even see my "casper-rw" Ubuntu drive, and it can't! What I did was to partition my flash drive into a Linux partition and a DOS partition. The DOS partition can be "seen" by both Ubuntu and Mac, and I use it as a "go between" to shuttle doc files between Ubuntu and my Mac.  I _think_ Fiesty Fawn can actually see your Mac hard drives which would happily dump this DOS go-between stuff, but until I'm sure that Feisty won't corrupt your flash drive's Edgy preferences and many mail and program settings -- like it has (hours and hours of prefs set-ups up in smoke), I won't touch it with a ten foot pole.


James Greenidge

---

### Post by arkstfan on 2007-06-16
> **jimwg said:**
> Hello arkstfan:

I WISH I could boot Ubuntu on my USB flash drive! Since booting on Mac USB is impossible, the second best thing is using Persistence mode, in which your flash drive is configured to be recognized by the Ubuntu live-CD as its start-up driver that holds all the prefs and settings and whatever programs you upload in Ubuntu, all without touching your Mac hard drive! It's almost like magic except for the CD's four-minute boot-up and occassional access, but it beats the hassle of reformatting your main drive! Now, what's probably confusing you is thinking my Mac can read or even see my "casper-rw" Ubuntu drive, and it can't! What I did was to partition my flash drive into a Linux partition and a DOS partition. The DOS partition can be "seen" by both Ubuntu and Mac, and I use it as a "go between" to shuttle doc files between Ubuntu and my Mac.  I _think_ Fiesty Fawn can actually see your Mac hard drives which would happily dump this DOS go-between stuff, but until I'm sure that Feisty won't corrupt your flash drive's Edgy preferences and many mail and program settings -- like it has (hours and hours of prefs set-ups up in smoke), I won't touch it with a ten foot pole.


James Greenidge

Well I was of no help to you but the DOS partition thing helps me because my son was asking if there were a decent way to bring files across the two OS's. Duh that'll do it. 

Off to reformat my external drive!

---

