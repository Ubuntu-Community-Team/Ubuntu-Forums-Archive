---
title: "Problems with Backtrack 5"
date: 2011-11-16
forum: Any Other OS
---

### Post by CJ-1990 on 2011-11-16
Heya guys and gals :)

I recently made a live usb of Backtrack 5 with UNetbootin
When I boot off said usb it boots fine and dandy, Backtrack 5 live comes up no problems...

But when I try to install Backtrack 5, that's where it really annoys me... 

I got the following error messages when I got up to and tried to complete the partitioning stage.

"ubi- summary failed with exit code 141"

I then tried restarting it a few times, didn't work...

I then chose the "continue anyway"option which gave me the following error message.

"ext4 filesystem creation failed"



Does anybody know what I could be doing wrong? Or if I'm not, what BT5 could be doing wrong? Was it improperly installed on my live usb? Have there been many problems with BT5 since the distro came out?

Thanks for any and all help you can give me, kinda miffed about it... 

Here are my "specs" atmoe:

Toshiba Netbook

1gb RAM

250gb internal HDD running Ubuntu Natty 10.04

And I am trying to install BT5 on my external 80gb HDD


Cheers

CJ

---

### Post by Dangertux on 2011-11-16
Are you trying to install it to your hard drive or the USB drive (make sure you're trying to partition the right thing) Ubiquity will freak out of the install media is mounted (in the case of if trying to install to the USB drive).

Also you might have better luck on the [backtrack forums]("http://www.backtrack-linux.org/forums/").

---

### Post by CJ-1990 on 2011-11-16
Trying to install to my external HDD which is mounted at sdd1, the installer actually wanted me to mount it lol...

Normally I would partition manually but I thought I'd use the full install option... 

I check the install to which disk option and choose my 80gb external, it comes up with the usual partition indication bar, everything fine and dandy...

Then it comes up with the first error message "ubi summary failed with exit code 141"

What does that error message denote? And how do I fix it?

Dw with using certain words and/or phrases, I am quickly learning :)

---

### Post by Dangertux on 2011-11-16
> **CJ-1990 said:**
> Trying to install to my external HDD which is mounted at sdd1, the installer actually wanted me to mount it lol...

Normally I would partition manually but I thought I'd use the full install option... 

I check the install to which disk option and choose my 80gb external, it comes up with the usual partition indication bar, everything fine and dandy...

Then it comes up with the first error message "ubi summary failed with exit code 141"

What does that error message denote? And how do I fix it?

Dw with using certain words and/or phrases, I am quickly learning :)

You can check syslog but generally 141 is partman crashing for some reason.

---

### Post by CJ-1990 on 2011-11-16
I'll check the syslog when I try to install it again...

How would the partman failure affect the install? What does partman do? 

Could the partman failure be attributed to an improper live installation?

Could the partman need updating? 

Cheers

CJ

---

### Post by Dangertux on 2011-11-16
> **CJ-1990 said:**
> I'll check the syslog when I try to install it again...

How would the partman failure affect the install? What does partman do? 

Could the partman failure be attributed to an improper live installation?

Could the partman need updating? 

Cheers

CJ

Partman is partition manager. It could be attributed to a bad install, or a dying flash drive, or it could just be a bug.

Are you using the KDE version of Backtrack or the Gnome? I googled it and noticed alot of people having issues with the KDE version, you may want to try the Gnome version of BT. 

Incidentally if it helps I'm using KDE Backtrack 5 r1 and didn't have any problems with partman.

Some people have also reported that manually partitioning doesn't cause the crash.

---

### Post by CJ-1990 on 2011-11-16
Well, just to be sure I will re-install BT5 live on my usb and see how it goes again...

I'm using the GNOME 32bit version

I will do the automatic install first to see how it goes, then I'll try manual install

I normally use:

10gb mount point primary beginning ext4

2gb swap beginning ext4

remaining space mount point home logical beginning ext4


Would that still work with BT5 or would I have to partition differently?

Cheers

CJ

---

### Post by Dangertux on 2011-11-16
> **CJ-1990 said:**
> Well, just to be sure I will re-install BT5 live on my usb and see how it goes again...

I'm using the GNOME 32bit version

I will do the automatic install first to see how it goes, then I'll try manual install

I normally use:

10gb mount point primary beginning ext4

2gb swap beginning ext4

remaining space mount point home logical beginning ext4


Would that still work with BT5 or would I have to partition differently?

Cheers

CJ


That should work , you might make the 10gb a little larger, just because if you do any large packet captures or generate any type of wordlists you may run out of space wicked fast.

---

### Post by CJ-1990 on 2011-11-16
So, instead of 10gb would you recommend 20gb? I have 80gb on my external HDD, and I'm only going to be using it for BT5, so should I make it as large as possible? :)

Thanks for all your help dood, I'll get started on the re-installation after your reply to this

Cheers

CJ

---

### Post by Dangertux on 2011-11-16
> **CJ-1990 said:**
> So, instead of 10gb would you recommend 20gb? I have 80gb on my external HDD, and I'm only going to be using it for BT5, so should I make it as large as possible? :)

Thanks for all your help dood, I'll get started on the re-installation after your reply to this

Cheers

CJ

If you're not planning on using the space for anything else, and you're serious about learning more about using backtrack I would give yourself as much space as you can. There is a lot of functionality in that distro that can eat up hard drive like no there's no tomorrow.

Hope this helps. Good luck with your install.

---

### Post by CJ-1990 on 2011-11-16
I am very serious about learning more about Backtrack :)

I'm only going to run amsn, and maybe mah-jong when I get bored or have to wait for something so the majority (79gb) is gonna be used for BT5, so should I just use?:

75gb mount point primary beginning ext4

2gb swap space ext4

3gb FAT32 for file storage


I currently moderate a site, am part of the Airsoft Australia team, and partly tech support for the other team members :) Gonna use BT5 to effectively run the forum, and broaden my knowledge, I learn new things for fun :) I have 2 other HDD's with Linux distros installed, which I did for fun :P

Thanks for all the help dood, I'll mark this thread as solved if it works, and also.

A massive bit of luck to your application on this forum site, you very muchly deserve it :)

Cheers

CJ

---

### Post by Dangertux on 2011-11-16
> **CJ-1990 said:**
> I am very serious about learning more about Backtrack :)

I'm only going to run amsn, and maybe mah-jong when I get bored or have to wait for something so the majority (79gb) is gonna be used for BT5, so should I just use?:

75gb mount point primary beginning ext4

2gb swap space ext4

3gb FAT32 for file storage


I currently moderate a site, am part of the Airsoft Australia team, and partly tech support for the other team members :) Gonna use BT5 to effectively run the forum, and broaden my knowledge, I learn new things for fun :) I have 2 other HDD's with Linux distros installed, which I did for fun :P

Thanks for all the help dood, I'll mark this thread as solved if it works, and also.

A massive bit of luck to your application on this forum site, you very muchly deserve it :)

Cheers

CJ

Thanks for the support on the membership :-)

If you have any other questions with this (or anything else for that matter) feel free to post. Just keep in mind, obviously BT is a penetration testing distro and sometimes the topics that come up with it aren't always in alignment with the forum code of conduct. Just a head's up to keep from getting posts closed -- there is a lot of information about BT and different things you can do with it on the forums I linked eariler so if you're needing application specific help be sure to look there.

---

### Post by CJ-1990 on 2011-11-16
No problems dood :)

And yeah haha, I know what you mean :P

Honestly, I am only using this for ethical means, the forum I help run means alot to me :)

---

### Post by Dangertux on 2011-11-16
> **CJ-1990 said:**
> No problems dood :)

And yeah haha, I know what you mean :P

Honestly, I am only using this for ethical means, the forum I help run means alot to me :)

I can certainly understand the concern, and the desire to protect your haven on the internet :-)

---

### Post by CJ-1990 on 2011-11-17
I re-installed BT5 on my usb with the built in STart up disk creator instead of UNetbootin and it worked perfectly, no error messages at all...  UNetbootin must be playing up or something...  Thanks for trying to help dood, really appreciate it aye.  Best of luck with your application again, you really do deserve it :)  I'm now going to mark this post as solved for the following reason/s:  I re-installed BT5 live on my usb with Start up disk creator instead of UNetbootin, do not use UNetbootin for creating live OS', for some reason it does not create a full working disk.  Cheers (Y)  CJ

---

### Post by Dangertux on 2011-11-17
> **CJ-1990 said:**
> I re-installed BT5 on my usb with the built in STart up disk creator instead of UNetbootin and it worked perfectly, no error messages at all...  UNetbootin must be playing up or something...  Thanks for trying to help dood, really appreciate it aye.  Best of luck with your application again, you really do deserve it :)  I'm now going to mark this post as solved for the following reason/s:  I re-installed BT5 live on my usb with Start up disk creator instead of UNetbootin, do not use UNetbootin for creating live OS', for some reason it does not create a full working disk.  Cheers (Y)  CJ



Glad you were able to figure it out.
     	  [CENTER] 	[LEFT] 		[LEFT]  	 	           				       





[/LEFT]
[/LEFT]
[/CENTER]

---

