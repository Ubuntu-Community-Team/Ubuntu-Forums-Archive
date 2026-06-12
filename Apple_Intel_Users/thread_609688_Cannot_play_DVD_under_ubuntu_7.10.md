---
title: "Cannot play DVD under ubuntu 7.10"
date: 2007-11-11
forum: Apple Intel Users
---

### Post by Hargo on 2007-11-11
Hi,

I've got an Intel core duo mac Mini under Ubuntu 7.10 with a Matshita DVD-R UJ-85J dvd drive.

I've installed libdvdcss2 but dvds won't read. I get the following message (with kaffeine):

************
The source seems encrypted, and can't be read. 
Your DVD is probably crypted. According to your country laws, you can or can't use libdvdcss to be able to read this disc. (Media stream scrambled/encrypted)
************

Any idea what's wrong?

Thanks
Hargo

---

### Post by shad0w_walker on 2007-11-11
Try opening a terminal and running this

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by Rog-Mahal on 2007-11-11
I am having problems with playing DVDs as well. I think I have all the right libraries and programs installed. When I start VLC from terminal and try to play the disc, I get the following errors:

```
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: HOUSE
libdvdnav: DVD Serial Number: 32d503cd
libdvdnav: DVD Title (Alternative): S1_D1SA_R0
libdvdnav: Unable to find map file '/home/roger/.dvdnav/HOUSE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000134
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000a32d
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x0000a32d)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000a6e2
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0000a6e2)!!
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00371e7b
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x00371e7b)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00371e7f
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x00371e7f)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0037c37d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0037c381
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x0037c381)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0037e580
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x0037e580)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0037e584
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x0037e584)!!
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 5
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)

```

Is this a problem with my DVD drive? Or is there something missing?

---

### Post by Hargo on 2007-11-11
I've tried this... to no avail :(

---

### Post by Hargo on 2007-11-11
My problem looks to be pretty much the same!

---

### Post by shad0w_walker on 2007-11-11
Have you tried playing the DVD in an alternative player? VLC should play it.

---

### Post by Rog-Mahal on 2007-11-11
I've tried mplayer, gxine, totem-gstreamer, totem-xine, ogle and Xfmedia. None of them work, and they all give similar error messages. Have other people running 64bit gutsy had similar problems?

---

### Post by Levo75 on 2007-11-11
DVD's work for me.

In both Mplayer and VLC.

It worked out of the box.

---

### Post by wolfen69 on 2007-11-12
> **Levo75 said:**
> DVD's work for me.

In both Mplayer and VLC.

It worked out of the box.

do you have a special version of ubuntu? i think it's called linuxmint.

---

### Post by Hargo on 2007-11-14
I've tried with VLC, Mplayer and xine, but it won't play.

---

### Post by RS3York on 2007-11-26
Hargo,

I had the same problem until about 10 minutes ago with drive by the same manufacturer on my Asus.  It would play DVD's in a virtualized WinXP ontop of linux but not directly in openSUSE or Kubuntu!

Anyway to This is how I got it to work:
1) install the xine engine
2) Configure xine's config

You can do that 2 ways, either in an app or just using a text editor.  I'll show both but you only need to do one.

A) Apps/GUI:

In Kaffeine 
Go to to Settings->xine Engine Parameters 
Select "Media" section 
Select the "Expert Options"  tab
Find an option labelled "CSS decryption method" 
Change setting from "key" to "title".

In Xine (package xine-ui) 
Go to Settings->Setup
Change your experience level to "Expert"
Select "Media" tab
Find an option labelled "CSS decryption method" 
Change setting from "key" to "title".


B) Config File
1) Open ~/.xine/config with your editor of choice [kate/gedit/etc] 
- there's no need to use root/sudo [the full path is /home/*your-user-name-here*/.xine/config]
2) Find the line "media.dvd.css_decryption_method"
3) Change from "key" to "title"
4) Save changes

If you are using gStreamer unfortunately I'm not sure what settings you will have to change to make things work.  But at the least you can install the xine engine and use that to play your dvds (I'm pretty sure Totem supports the xine engine and if not you can use the xine-ui)

Let me know if this works for you.

---

### Post by jfank on 2007-11-29
> **shad0w_walker said:**
> Try opening a terminal and running this

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

I ran this code in my terminal, and it worked perfectly.  I can now view DVD's on VLC.  I get the full sound, and full video without any problems.  It was a little scratchy at first, but then since I had my computer turned on for 2 weeks straight I restarted it, and there is no scratchyness in the DVD playback at all.  Thank you for posting this code on here.  

Although I have the problem with Totem where I have to install the "libdvdcss".  When I installed it for VLC it didn't work with Totem.  So you have any ideas on how to get it to work for Totem or what to do to get it to work correctly?  Thank you for the help.

Now to those that are going to just use VLC the code up above should work perfectly for you.  If there is any other problems where it doesn't work, just look around, and you whould be able to find the answer.

---

### Post by madmaxo on 2008-06-24
I had this problem and found the cause was my DVD player didn't have a region set. So run:

sudo apt-get install regionset

Then run regionset. If your region is set to 'mask=0xFF' it means no region is set. It then prompts you to change your region if you want. Region codes are here: [http://en.wikipedia.org/wiki/DVD_region_codes#Region_codes_and_countries]("http://en.wikipedia.org/wiki/DVD_region_codes#Region_codes_and_countries")

---

