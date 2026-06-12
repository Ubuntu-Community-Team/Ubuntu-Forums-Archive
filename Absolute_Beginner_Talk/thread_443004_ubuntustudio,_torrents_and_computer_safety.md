---
title: "ubuntustudio, torrents and computer safety"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-14
I wanted to look at ubuntustudio, but their site has been down for a few days (anybody have any news on that, BTW?) so I googled for an alternative, and a series of torrent possibilities came up, 

After dithering for a day or two (who are these torrent people? What's in it for them?) I bit the bullet and tried three or four of the most promising-sounding. They all came up with a whole series of entirely questionable ads on the page which presented the download, which made me think twice before downloading stuff, as well as the statement that downloading would ake several days (?) -so I cancelled. Did I do right? What kind of protection should be installed on my PC so as to avoid unwitting contamination from unhealthy sources?

---

### Post by mcduck on 2007-05-14
Here's the 'official' mirror link for you: [http://mirror.imbrandon.com/ubuntustudio/7.04/]("http://mirror.imbrandon.com/ubuntustudio/7.04/")

I found it from Ubuntustudio's pages in Ubuntu Wiki: [https://wiki.ubuntu.com/UbuntuStudio]("https://wiki.ubuntu.com/UbuntuStudio")

---

### Post by ginestre on 2007-05-14
Thanks for the link; while this site has no extraneous or questionable ads on it, it still gives me an estimated time of 3 days for the download. Is that normal? And should I have some kind of protection on the PC with this type of download? Under windows I would have had a couple of anti virus progs as well as  an anti spy scan. And I'd have been behind a firewall. 
I feel kind of naked like this, just connected with no cares, after reading the google scare stories over the last few days- especially when some of those other torrent places carry just the kind of porn ads Google said was being used to lure the unwary and unprotected.....

---

### Post by mcduck on 2007-05-14
Torrent's are no problem, as long as you get them from some reliable site.

And, there are practically no viruses for Linux, and zero adware or spyware so you really are safe. If you feel like it, you can enable the built-in firewall of Linux kernel by installing Firestarter (a graphical tool to control the Linux firewall). But even that is not necessary as Ubuntu , by default, doesn't have any ports open for incoming connections.

3 days of download time for the torrent sounds a bit long, but it depends on your internet connection, and how many people are sharing the same torrent. But also note that when using torrents the speed will change all the time as new people start sharing the torrent and some peers disappear. And it takes a bit time for the torrent download toget to full speed. Anyway, I downloaded that ISO in about 3 hours, with 1MB/512KB ADSL connection.

---

### Post by ginestre on 2007-05-14
Thanks for the clear and comprehensive reply.

---

### Post by ginestre on 2007-05-14
Well, it only took 5 hours rather than the original estimate of 3 days, and I learned something from this.  However, the ubuntustudio site is still down and I don't know where else to ask this- so I'll ask it here in the hope someone will be kind enough to answer. The question is, now that I have downloaded the torrent, what do I do? I suppose I ought to check its integrity by means of the arcane md5 process- but how? And when I have, then what? Is it an iso?

Thanks once again

---

### Post by ginestre on 2007-05-14
I'll at least answer my own stupid question before others do (I hope)- yes, it's an iso. I should have looked at it better before firing off my question. 

Sackcloth and ashes.

---

### Post by mcduck on 2007-05-15
For the arcane md5sum:

Just run 'md5sum /path/to/your/file.iso' (use the actual path and filename of course). Then compare the sum you get with the one they provide on their website (might be a bit hard as it's down..). If the sums are same, you know you have the real thing, and with no errors.

(usually there's no errors anyway, as torrent downloads automatically check the files while downloading. So in that case it's just a way to check that you got the file you wanted and nobody has made any changes to it)

---

