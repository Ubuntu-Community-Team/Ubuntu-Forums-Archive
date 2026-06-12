---
title: "Linux Mint md5sum"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by SusieK on 2007-12-17
I wonder if anybody can help? While waiting for nearly two weeks for a CD to arrive,I have been trying to download Linux Mint 4. It doesn't work with Bit Torrent, and I've used the Softpedia link. After four downloads, the CD that I burn still doesn't work properly. The graphics display strangely - huge headings, and there are some error messages. 

I know that the download should be checked with MD5SUM before burning to the CD, and I have downloaded that program. However, the Softpedia download page doesn't say what the string should be. Is the MD5SUM the same wherever the download comes from, or is it unique to that particular download source?  :confused:

Thanks for any help to a complete newbie.

---

### Post by 5-HT on 2007-12-17
> **SusieK said:**
> Is the MD5SUM the same wherever the download comes...? Yup, it's file-dependent. Here's a link: [http://linuxmint.com/mirrors.php?id=15](http://linuxmint.com/mirrors.php?id=15)
cheers,

---

### Post by SusieK on 2007-12-17
Oh dear, thank you for the reply, but that's a nuisance, because I can't find it anywhere on the Softpedia site, nor does their forum give any response.:frown:

The download takes nearly six hours, too. :(

The torrent downloads don't work at all. ](*,)

I hope it isn't an omen. :)

---

### Post by 5-HT on 2007-12-17
> **SusieK said:**
> Oh dear, thank you for the reply, but that's a nuisance, because I can't find it anywhere on the Softpedia site, nor does their forum give any response.:frown:

The download takes nearly six hours, too. :(

The torrent downloads don't work at all. ](*,)

I hope it isn't an omen. :)

Can't find the checksum? T'was on the link I posted but here it is for the 4.0 Daryna iso (main edition):
572a56ec165ef6ad8f785cc7f13a5a14

If the image checks out, you can always check to see if the disk itself is corrupted ('md5sum /dev/cdrom' or similar depending on your device).

cheers,

---

### Post by SusieK on 2007-12-17
Sorry, I didn't realise that was the checksum I needed. I thought it was a different one as I had downloaded it laboriously from Softpedia, and not via a torrent. So that checksum is for the download either through a torrent or from any of the mirror sites?

---

### Post by Sef on 2007-12-17
> So that checksum is for the download either through a torrent or from any of the mirror sites?

Torrents automatically md5sum, so there is no need for you to do so.

---

### Post by 5-HT on 2007-12-17
> **SusieK said:**
> Sorry, I didn't realise that was the checksum I needed. I thought it was a different one as I had downloaded it laboriously from Softpedia, and not via a torrent. So that checksum is for the download either through a torrent or from any of the mirror sites?

Yup, exactly.  :)
As Sef mentioned, bittorent checks file integrity automatically, but the resultant (non-corrupted) iso will have have the same checksum regardless of which server you downloaded it from or whether it was from a torrent.

---

### Post by SusieK on 2007-12-17
Thank you all very much. I have now verified the checksum. Hope I can burn a good live CD this time. :)

---

### Post by tgalati4 on 2007-12-17
Burn extra slow (4X).

---

### Post by SusieK on 2007-12-17
Thanks, I have burned it at 4X.

---

### Post by SusieK on 2007-12-17
Unfortunately still the same result. While loading the Linux kernel lots of little dots appear on the upper part of the screen, which obviously shouldn't be there.

Then an error message appears, which disappears before I can read it, but something to do with missing code.

The CD seems to struggle very hard to load, and takes nearly five minutes to get there. When it does, any application I click on appears with very large letters across the top of the panel. I've now downloaded five times, and burned the CD with Infra Recorder, ISORecorder and BurnCDCC and am getting the same result every time. 

Also on my last attempt a new message appeared which said panel encountered a problem while loading OAFIID GNOME_Mixer Applet. I deleted the applet, but still the same problems. :confused::(

---

### Post by lespaul_rentals on 2007-12-17
Is there an option to "verify CD integrity" or something like that?  It's also possible Linux Mint doesn't work with your hardware.

---

### Post by SusieK on 2007-12-17
I can't find anything in any programs I have to check the integrity of the CD. Ubuntu worked fine on this computer (except for wireless connection). I thought Linux Mint was very similar.

---

### Post by Sef on 2007-12-17
> I can't find anything in any programs I have to check the integrity of the CD. Ubuntu worked fine on this computer (except for wireless connection). I thought Linux Mint was very similar.

It is very similar, but not the same.   You could try downloading and reburning the new iso.

---

### Post by SusieK on 2007-12-17
I've downloaded the ISO five times now and have had the same result each time. It takes 6 hours on our connection. Maybe the CD I paid for will eventually arrive, and if that doesn't work, then I guess it's time to give up trying Mint. :(

---

### Post by floke on 2007-12-17
Try burning it from the terminal - 

navigate to the directory with the iso image (lets say its in /home/susie ...

cd /home/susie

then ...

wodim whatevernamefomint.iso

- this worked for me when I kept getting corrupt copies

---

### Post by SusieK on 2007-12-17
Does that mean the Linux terminal? Because I haven't got a Linux installation on the computer at the moment until or unless I can get Linux Mint installed.

---

### Post by floke on 2007-12-17
Well that might be a small problem in that case :(
You could always try a different version of *nix. Mint is not by any means the be-all-and-end-all?

You can find loads here

[http://distrowatch.com/](http://distrowatch.com/)

Happy hunting!

---

### Post by SusieK on 2007-12-17
Yes, a whole wonderful world of exploration lies ahead. =D>

---

