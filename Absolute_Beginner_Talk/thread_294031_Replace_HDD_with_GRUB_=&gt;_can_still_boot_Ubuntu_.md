---
title: "Replace HDD with GRUB =&gt; can still boot Ubuntu ?!"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by LLRNR on 2006-11-06
Hi all, again !

I currently have a perfectly running dual-boot machine : I've got both Dapper 6.06 LTS and WinXP Prof. I have 2 HDDs - the primary master is a 20 GB HDD and it's the HDD with Windows and with the GRUB bootloader, and the second one is a 80 GB HDD with a ~40 GB NTFS partition and a ~40 GB Ext3 partition, on which I currently run Ubuntu. 

My problem is that I'll soon buy another HDD and I want to donate the small one (the 20 GB one, the one which has the bootloader). Instead of it, I would like to install the new HDD (I still want to keep it as the primary master, since my current 80 GB HDD is not very reliable). The question I have is wether it's possible to do that i.e. to format the new HDD, to install Windows again on it and still keep Ubuntu on my 80 GB HDD just the way it is now.

I hope I put it in clear terms...

Thanks in advance, 

LLRNR

---

### Post by Bartender on 2006-11-06
I'm not absolutely 100% sure about this, but couldn't you use the CD that comes with retail HDD's to just copy the data from the old 20 GB to the new 80?  I'm not sure how the unused part of the disc would be formatted, but is sure seems to me like you could just copy it.  
The CD copies the data from the old HDD.  It doesn't move it.  So if this didn't work (don't know why it wouldn't) there'd be no harm done.  You could try something else.

---

### Post by LLRNR on 2006-11-06
Hi Bartender, I'm sorry for my delay, I was at school :) Well to me it sounds a little confusing: when I bought my last HDD it didn't come at all with a CD, it didn't even have a box of itself (it was only wrapped in a special plastic-thing which has, as far as I understand, anti-electrostatic effects) - I guess it was a "bulk" HDD pack, am I wrong ? I had to pre-format it myself (in fact I never had a retail HDD before).

Your idea seems ok and brightly clear to me. I was wondering if I could avoid the retail HDD install CD... I'm not sure, but I heard something about a ultimate boot CD or so ([ultimatebootcd.com](http://ultimatebootcd.com)), no, I'm not lazy, but I haven't had the chance yet to test this out and I guess that someone around here must have used something like this before (the list of apps is a very long one, and I'm not even sure what do I have to check for), so, could such a utility provide me with the copying process that Bartender described ?

Thanks again, 

LLRNR

---

### Post by jhenager on 2006-11-06
Check out this page. It talks about using a little command line program called boot.exe to read and write boot sectors.
[http://www.tburke.net/info/ntldr/ntldr_hacking_guide.htm#lilo](http://www.tburke.net/info/ntldr/ntldr_hacking_guide.htm#lilo)
That should help you.
May the source be with you.

---

### Post by LLRNR on 2006-11-06
Thanks, jhenager and Bartender ! When I'll have my new HDD, I'll try the methods pointed out by you and I'm sure I'll get positive results. Until then... may the source be with all of us ! :D

---

### Post by louieb on 2006-11-06
If you buy a Maxtor drive it come with Max Blast software. When I bought a larger drive a couple of years ago I used Max Blast to move the operateing system and data to the new drive. Check out there web site. Oh by the way Seagate bought Maxtor. also you might want to check the Westren Digital site to. I belive they have something similar for there drives.

---

### Post by bulldog on 2006-11-06
Then there's another option to confuse you even more :D ,it's called Super GRUB Disk,and you can find it here,

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

---

### Post by LLRNR on 2006-11-06
Thanks bulldog ! It seems a little bit confusing at first for a newcomer to find there are sooo many alternatives to do one certain thing, but I'm starting loving it more and more and more. I never before had the possibility to find flexible solutions to my problems... and although it's kind of time consuming at first glance, it sure DOES worth trying out every each of them. Super Grub Disk seems very appealing to me, I'll surely try it out when I'll be able to fetch my new HDD... and then again, I like louieb's solution also, except I'm not at all confident in Maxtor (I've had problems before with my Maxtor HDD); well the MaxBlast sounds like a cool option, but I myself have been a WD lover for ages (lol, since my first WD Caviar Series 80 MB HDD which still runs today perfectly well it has DOS and Win3.11 on it :) ), so I'd like to know wether a similar utility (similar to MaxBlast for Maxtor) is available to use with a WD... just in case ! ;)

---

### Post by bulldog on 2006-11-06
There should be,I'm having a WD too and I remember I've used it several times on a broken hdd.
Should be something on their website.

---

### Post by Bartender on 2006-11-06
If you buy a "white box" HDD it won't come with cable, screws, or CD.  I was referring to a retail box.  You can always go to the HDD manufacturer's website and download their utility.  It's the same utility as on the CD in a retail box.

---

### Post by louieb on 2006-11-06
There is also an open source clone sortof Norton Ghost. Look for something called partimage.

---

### Post by b_martinez on 2006-11-13
Then there's the old-school way and that means hooking up the new hdd , keeping the old one hooked up and using a live cd , the command line and the 'dd -r if /dev/hda of /dev/hdb'. I personally would use Knoppix and get the info from their recue FAQ on how to do it all in one session, including the formatting, partitioning (including re-sizing),copying and mbr copying.
Just my $0.02  :rolleyes: 
Bill

---

