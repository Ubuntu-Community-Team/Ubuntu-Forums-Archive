---
title: "Some software questions"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by barbecued_ribs on 2007-08-04
1.I need a good CD ripper, like itunes or something, that doesnt create 10 MB per minute songs.
2. MSN messenger? it came up in a package search, but nobody can figure it out.
3. Do we need to disk defrag? If we do i can't find it.
4. A simple paint program, maybe like MS paint?
5. Firefox likes shutting down for no reason
6. GIMP doesnt have the help files installed, so i can't figure out how to erase to background or get rid of the white part when i move a clip to another
7. How do I get a little message/signature at the bottom liek evryone else?
More to come later

---

### Post by be4truth on 2007-08-04
Install GIMP help files with Synaptic.
Try gnu paint.
No disk frag.
For your signature goto Forum Help at the top of this page.
msn --> AMSN (I never used it). You could use automatix to install it. Be aware that some people don't use Automatix, others do. I never had any problems with it. Have a look here :

[http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

---

### Post by atomkarinca on 2007-08-04
1. applications > add/remove. type "cd rip" and you will see a list of softwares. i think your best bet (since you don't want soundjuicer) is kaudiocreator.
2. msn messenger has no native client for linux (duh) but you can try amsn (again you can find it via add/remove) or pidgin.
3. no
4. there is kolourpaint. that's pretty simple.
7. on top of the page user cp > edit profile

---

### Post by sad_iq on 2007-08-04
1. Try to see what settings you have in Sound Juicer. Open it...go to Edit->Preferences And see what's in the Output Format. I have mine set to Cd Quality, Mp3. Just click Edit Profiles and play with what you have there, experiment!!!
2. Gaim??? Applications->Internet->Gaim !!!
3. No! Disk defrag is only needed in Windows, linux does a much better job at keeping the disk in a good shape!
4. Try tuxpaint: ```
sudo aptitude install tuxpaint
```
5. Give us more details on this one!!!
6. Has been answered!!!
7. There is a **User Cp** link here in the forum, click it and choose what you need to edit!!!

---

### Post by Brunellus on 2007-08-04
> **barbecued_ribs said:**
> 1.I need a good CD ripper, like itunes or something, that doesnt create 10 MB per minute songs.
2. MSN messenger? it came up in a package search, but nobody can figure it out.
3. Do we need to disk defrag? If we do i can't find it.
4. A simple paint program, maybe like MS paint?
5. Firefox likes shutting down for no reason
6. GIMP doesnt have the help files installed, so i can't figure out how to erase to background or get rid of the white part when i move a clip to another
7. How do I get a little message/signature at the bottom liek evryone else?
More to come later
1.  Your CD ripper is Soundjuicer.  If you are *really* reporting 10 MB per minute, then you've set Soundjuicer to "lossless" (FLAC).  Try using "CD Quality" which is Ogg Vorbis -q 4.  I have found that, for the same quality, Ogg Vorbis files are considerably smaller than MP3s.    If you want even more fine-grained control over the ripping process, use a CD ripper like Grip.

2.  MSN Messenger is a supported (mostly) protocol in GAIM/Pidgin and Kopete.  Simply add your account there.  Some users prefer aMSN for this, but I have never used aMSN, since I have only one MSN contact.

3.  Disk fragmentation is NOT a problem on *nix filesystems.  For a good explanation on how filesystems work and why some filesystems fragment more than other, read this:

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

As that article notes, filesystems like ext3 and reiser3 will start to suffer when mostly (~ 80%-90%) full, though.  In practice, filesystem fragmentation is not something you're going to have to worry about.


4.
```
 sudo aptitude install tuxpaint
```

5.  Don't have enough information to be of service here.  What were you doing when Firefox died?  

6.  ```
 sudo aptitude install gimp-help-common gimp-help-en
```

Also, for more in-depth help try Grokking the GIMP:

[http://gimp-savvy.com/BOOK/](http://gimp-savvy.com/BOOK/)

7.  Your forum user options are under the USER CP tab.

---

### Post by barbecued_ribs on 2007-08-06
I need good quality MP3 files, maybe WMA, but i dont think I can get those with ubuntu. 
our **_MP3_** players don't know what a oggflac is, and can't read the 10 MB per minute soundjuicer files. So is there a good Cd ripper, like itunes/WMP was, that make good, small, readable MP3 files, or am I SOL?

---

### Post by jpkotta on 2007-08-06
I like abcde, but you probably won't.  I like LAME for mp3 encoding, with the "standard" preset.  It's kind of big (>200kpbs), but transparent, which is more important.

[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

---

### Post by mevets on 2007-08-06
There sure are a whole bunch. K3b is a burning tool, but it does well with occasional cd rips. CD ripping is under 'Furthur Actions'. You can plenty of other ones under Add/Remove though.

---

### Post by barbecued_ribs on 2007-08-06
so which one's the best one for MP3?
soundjuicer and kaudiocreator suck.

---

### Post by OoooMatron on 2007-08-06
grip is really great. allows you to encode to lame.

i've got rockbox on my sandisk player so i use OGG.

---

### Post by barbecued_ribs on 2007-08-06
> **OoooMatron said:**
> grip is really great. allows you to encode to lame.

i've got rockbox on my sandisk player so i use OGG.

What's that mean?

---

### Post by Hallvor on 2007-08-06
Soundjuicer works perfectly for me and a lot of others, and it will make good quality mp3 files that play perfectly on mp3-players.

Just adjust the bitrate to something like 192 or 256 kbps and make sure the output is mp3. Some mp3 players can`t handle high bitrates. The problem isn`t Soundjuicer. In fact, every ripper will "fail" if you are trying to push a file with an unsupported bitrate to your player. Stop looking for other rippers and learn how to use Soundjuicer.

Anyway, I think you`ll find what you are looking for here:
[http://gentoo-wiki.com/HOWTO_rip_mp3s](http://gentoo-wiki.com/HOWTO_rip_mp3s)

---

### Post by OoooMatron on 2007-08-06
> **barbecued_ribs said:**
> What's that mean?

Grip is a cdripper/encoder available in the repo's

Rockbox is a firmware for mp3 players that provides music/video/plugin support for your player through its own software, far superior to the software that came with the player.

Of course, this stuff don't work on cheapo 1gb players, you need a better one.

[www.rockbox.org](www.rockbox.org)

---

### Post by coolen on 2007-08-09
> **barbecued_ribs said:**
> 1.I need a good CD ripper, like itunes or something, that doesnt create 10 MB per minute songs.
2. MSN messenger? it came up in a package search, but nobody can figure it out.
3. Do we need to disk defrag? If we do i can't find it.
4. A simple paint program, maybe like MS paint?
5. Firefox likes shutting down for no reason
6. GIMP doesnt have the help files installed, so i can't figure out how to erase to background or get rid of the white part when i move a clip to another
7. How do I get a little message/signature at the bottom liek evryone else?
More to come later

SoundJuicer always works for me, although I use OGG Vorbis.
Once you get mp3 support, it can use Lame as the backend. In short, it's not likely SoundJuicer that sucks, but the settings it passes to Lame.
2. I use aMSN from Trevino's repository. Chameleon plugin, anti-aliased fonts, and about as many features as the official client. I've also heard good things about Mercury for a multi-protocol client, but it never did work for me.
3. No need.
4. I use KolorPaint. Very similar to MS Paint.
5. I keep leaving the house for bread.

---

### Post by niceguy123 on 2008-01-14
I'm looking for a CRM Customer Relationship Management  tool. I had been using something on windows based on access which I understand would work on linux with out wine. and am not looking into working with wine. I'd like to find something that works "naturally" here.

Any ideas?

---

