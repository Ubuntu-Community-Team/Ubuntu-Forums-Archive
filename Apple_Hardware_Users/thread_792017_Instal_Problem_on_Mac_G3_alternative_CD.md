---
title: "Instal Problem on Mac G3 alternative CD"
date: 2008-05-12
forum: Apple Hardware Users
---

### Post by Gondor81 on 2008-05-12
I recently acquired a Mac G3 tower. I did not like the Mac OS 9 install that was running on the system so I decided to put Ubuntu linux on the system. It has a 6 GB HD with 512 MB of RAM. I checked the system by running the Live CD with no known issues. I could browse the web, play games, creating office documents with open office work. So I decided to install using the live install. This did not work. It would hang at 46% everytime. I let it run over night with no progress and no error messages. I was able to move the mouse around, but nothing responded when I clicked on it so I shut the system off and tried to install with the alternate CD. Everything was going great until I got to the Install and Select Software section. The alternate CD gave an error message and said that I could skip this part so I went on to the next section and it had an error as well. When I selected the yaboot section it continued on and I was able to do the Finish the Install. Then when I rebooted I got a prompt instead of the gnome desktop. I thought, OK and used apt-get to install ubuntu-desktop. While it was installing there were errors on hda. I am thinking, I must have a bad HD so I replaced it with another HD. This did not help.

I went through the process again with a different HD and had the same issue. When I got to the Install and Select software section it died. This time I did a Disk check and there was a file that was corrupt. So I burned a new disk at 8x and tried again. The same file was corrupt when I did a CD check. Not sure where to go next. Does anyone have suggestions?

I am using a Mac G3 Blue & White with a 6GB Quantum EX HD and 512MB of PC100 RAM.  Not sure what to do next.  I have also posted over in the Installation section.

Thanks.

---

### Post by stream303 on 2008-05-12
Are you using CD-R's or CD-RW's?  some system balk at using cd-rw's.

Wonder which version you are downloading, although it shouldn't be a problem with the md5sums..
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Is there another machine you can download and burn on?

---

### Post by Gondor81 on 2008-05-12
> **stream303 said:**
> Are you using CD-R's or CD-RW's?  some system balk at using cd-rw's.

Wonder which version you are downloading, although it shouldn't be a problem with the md5sums..
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Is there another machine you can download and burn on?

I am downloading "Mac (PowerPC) and IBM-PPC (POWER5) alternate install CD".  I am using CD-RWs.  I will try a CD-R.  I am a step ahead of you.  I am downloading at work and will burn using DeepBurner.

---

### Post by Gondor81 on 2008-05-12
Ok, the iso I have md5 checksum came out the same so I will try to burn to a CD-R and install from that.  Next step would be to try replacing the CDROM with a different Drive I think.

---

### Post by Gondor81 on 2008-05-13
Yeah for forum help.  Burning Ubuntu to a CD-R fixed my problem.  I hope that this helps someone else in the future.

---

