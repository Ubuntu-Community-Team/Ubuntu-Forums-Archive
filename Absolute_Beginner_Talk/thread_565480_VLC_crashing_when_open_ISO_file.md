---
title: "VLC crashing when open ISO file:"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-10-02
Hi, I am trying to play a dvd movie with VLC, from a ISO file. It works fine in VLC on Windows, but when trying to open it on Linux it only crashes instantly. So I opened VLC in the terminal to see what it reported, but I don't understand it(other ISO files works fine). 

Perhaps you do?

This is from the terminal: 
> VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: BECK_23
libdvdnav: DVD Serial Number: 46E915640000003D
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/sam/.dvdnav/BECK_23.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

*** libdvdread: CHECK_VALUE failed in ifo_read.c:663 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:664 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:665 ***
*** for pgc->cell_position_offset == 0 ***

libdvdnav: ifoRead_PGCI_UT failed - CRASHING!!!
vlc: vm.c:210: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)


---

### Post by Curtiss on 2007-10-02
Try burning the iso file first. I use gnomebaker if its not installed go add/remove and install gnomebaker.

---

