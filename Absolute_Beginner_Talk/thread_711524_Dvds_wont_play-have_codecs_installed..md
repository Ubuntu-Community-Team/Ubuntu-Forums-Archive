---
title: "Dvds wont play-have codecs installed."
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by fullmetalgerbil on 2008-02-29
Trying to get DVD playback after a reinstall of Ubuntu 7.10. I have used the following commands to get codecs and everything, but the system will still not recognize DVDs.
I've tried:
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2 
sudo apt-get install w32codecs
sudo apt-get install gxine
sudo apt-get install totem-xine
sudo apt-get install xine-ui
sudo apt-get install libdmx1
sudo apt-get install libxine1
sudo apt-get install libxine1-ffmpeg
sudo apt-get install libxinerama1
sudo apt-get install totem
sudo apt-get install vlc
and still no joy.
I've used the same procedure on previous installs of Gutsy and it worked fabuluosly. Am I missing something? (note: I also have ubuntu-restricted-extras installed)

---

### Post by Aquaman420 on 2008-02-29
Have you installed the gstreamer files??  I used to have alot  of troubles playing movies with the xine libraries, so I quit using it and installed totem-gstreamer and used the gstreamer files and have had success since then.  Hope that helps.

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mpegdemux gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-tools gstreamer0.10-x gstreamer-tools totem-gstreamer libdvdread3 libdvdnav4
```

Totem-gstreamer will replace totem-xine.

---

### Post by fullmetalgerbil on 2008-02-29
Nope, nothing. I tried gstreamer and it still wont read DVDs.
 The especially aggravating thing is that I've got DVD playback working on like four previous installs (I'm a bit promiscuous when it comes to distros, but I always seem to come back to Ubuntu).

---

### Post by mc4man on 2008-03-01
I see you have installed vlc - all it needs otherwise is libdvdcss2 . Ck. in synaptic that libdvdcss2 is installed (1.29 is best). Then open vlc thru terminal and try to open disc - terminal log should be helpful

---

### Post by fullmetalgerbil on 2008-03-01
libdvdcss2 was already installed. Unsure as how exactly to open vlc via terminal-tried run vlc , no joy, got bash: command: not found. 
Thing is, I have both vlc and totem installed and have tried both as default with nothing even approaching succes eventhough I've installed all the codecs I usually do to get things working. I'm doubting its hardware related as the disc drive, and Ubuntu, read data DVDs perfectly well.

---

### Post by mc4man on 2008-03-01
> Unsure as how exactly to open vlc via terminal
just type vlc

---

### Post by jan quark on 2008-03-01
rn this in terminal and then open with gxine

```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by miwaypet on 2008-03-01
Try this: [http://ubuntuforums.org/showthread.php?t=661833]("http://ubuntuforums.org/showthread.php?t=661833")

Hope this helps.

---

### Post by fractl on 2008-03-02
I'm in the same boat with my DVD playback.  I've been following forum threads and installing/uninstalling/reinstalling codecs for weeks now with no joy.  When I use VLC to play a regular rental DVD's in my DVD-RW drive on 7.10, I get the following:
```
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/hda with libdvdcss.
libdvdread: Can't open /dev/hda for reading
libdvdnav: vm: faild to open/read the DVD
[00000410] dvdread demuxer error: DVDRead cannot open source: /dev/hda
[00000412] vcd access error: could not read TOCHDR
[00000412] vcd access error: no movie tracks found
[00000412] access_file access error: file /dev/hda is empty, aborting
[00000412] cdda access error: could not read TOCHDR
[00000412] cdda access error: no audio tracks found
[00000409] main input error: no suitable access module for `dvd:///dev/hda'
[00000288] main playlist: nothing to play
```
:confused:

I've tried ALL the players and none of them will come up with anything.  Thoggen DVD ripper will occasionally come up with the DVD's name but no tracks.

I've since been using an old 2001 DVD to test and I thought to try its Extras disc.  It worked.  This is the read-out:
```
VLC media player 0.8.6c Janus
libdvdnav: Using [COLOR="Red"]dvdnav version 0.1.10[/COLOR] from http://dvd.sf.net
libdvdread: Using [COLOR="Red"]libdvdcss version 1.2.9[/COLOR] for DVD access
libdvdnav: DVD Title: TERMINATOR_DISK_2
libdvdnav: DVD Serial Number: 2a316104
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/julie/.dvdnav/TERMINATOR_DISK_2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000139
libdvdread: Elapsed time 0
<snip>
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x001d31fc
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
[00000405] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:256000
No accelerated IMDCT transform found

```

lshw reports this for the drive:
```
  *-cdrom
       description: DVD writer
       product: HL-DT-STDVDRRW GCA-4166B
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 1.08
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2 status=nodisc
```

I have run regionset on the drive and set it to zone 2.

The drive came with my new HP desktop machine, 12 - 18 months ago.  Any stabs as to why it might work in this way?  

Could it be that it doesn't read dual-layer discs??  	:rolleyes:

---

### Post by mc4man on 2008-03-02
The first question would be are the dvds actually mounting,  ie. is an icon with titles name showing up on desktop? The error message suggests they're not.

edit:try a new or very clean disk (other than extras one)

edit: rerun lshw with a non functioning disk inserted -   status=nodisc - if you see that try above or maybe a dvd drive cleaning disk

---

### Post by ubuntu-freak on 2008-03-02
You only need VLC, libdvdcss2, libdvdread3, libdvdnav4, fakeroot, debhelper and build-essential. Then after that you run the install-css.sh command, as mentioned previously and in my [how-to](http://ubuntuforums.org/showthread.php?t=661833). If you still have problems, it could be a loose or faulty lead. Totem-xine is not needed.
 
Nathan 
 
P.S. You can also make VLC launch by default when you insert a movie if follow my how-to.

---

### Post by fractl on 2008-03-03
Nathan: Thanks for the tips, I had visited your post before and found it very thorough.  But it was all stuff I'd tried already.  When I ran the install, all I got back was a pile of notifications telling me that I already had the latest version of "x" installed and nothing was going to be updated.   Xine was something I added later to see if it would help (it didn't).  I accept that it can probably be removed but I don't think it's part of my current problem.

And yes, VLC does already run by default - I set that up quite early on - but it doesn't make a blind bit of difference because nothing launches at all for these non-functioning discs.

mc4: To answer your questions, no nothing mounts as such for these discs.  I'd been assuming it was a CSS/installation problem all along, but now I'm thinking that maybe it's the drive...? 

Question: Would you expect **all** DVDs to mount regardless of whether the software can crack their codes?

Re-run of lshw with a "broken" disc (most of the ones I've tried) gives the nodisc status.

I've had one other disc work - an all-region kiddies DVD with about 45 minutes of video on it.  It doesn't say on it, but I suspect it could also be single layer...

Do you think dirt on the lenses, or a loose / faulty lead, would be as selective to play single layer video DVD but not double? CD's and home-made data DVDs also work fine.  I haven't got a cleaning disc but I'll try track one down if there's a chance it'll make my DVD headaches go away!

---

### Post by ubuntu-freak on 2008-03-03
When you ran the install-css.sh command it wouldn't do it? It's supposed to modify and downgrade it, then Ubuntu updates it again and keeps the modification. Strange problem you're having there. Sure it's not hardware related? 
 
Nathan

---

### Post by mc4man on 2008-03-03
> Would you expect all DVDs to mount regardless of whether the software can crack their codes?  Absolutely.   Everything points to either a dirty /dying drive or damaged discs (or combination of all) Your extras disk probably was in excellent condition
More than likely it's the drive - oem drives are by nature cheap

---

### Post by fractl on 2008-03-03
> **mc4man said:**
> Absolutely.   Everything points to either a dirty /dying drive or damaged discs (or combination of all) Your extras disk probably was in excellent condition
More than likely it's the drive - oem drives are by nature cheap
Great - just knowing for a fact that I should be seeing a mount is very helpful.  Thanks.  I have just thought of another drive to try (another OEM but well, beggars and all that...) so will test that tonight.

---

### Post by fractl on 2008-03-04
Well, it doesn't say much for the OEM drives that HP put into their desktops, but my problem is solved - yay!! :-D  I nicked a 5-year-old DVD-R drive from our server box, and she worked straight off.  
(Kinda wondering what to do about the semi-working RW drive now, since its never going to get its sheen of reliability back... :()

Anyway, thanks for the help.  I guess I was a little blinded by all the codecs and players into thinking that it was somehow my install that was at fault.  And, to be fair, we were dealing with a fairly new, working-in-lots-of-other-ways drive.   But there really are a lot of good tips going on the forums for the installation side of things, and no real reason why anyone shouldn't be able to get any DVD's playing -- if they start with a working DVD drive!

Julie

---

