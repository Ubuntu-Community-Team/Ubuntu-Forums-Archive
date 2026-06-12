---
title: "Trouble updating"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by sleepytom on 2006-12-21
I've been trying to update my system to rip CDs into mp3 format by following directions on this site and others, but now my Sound Juicer will not open. If I try to start it I see a task open that reads "Starting Sound Juicer" but the item in the task bar disappears and Sound Juicer never stars. Same with "CD Player"

Also, I cannot seem to update my system anymore due to the following errors:

Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libdivxdecore0 libdivxencore0
The following packages have been kept back:
  wpasupplicant
The following packages will be upgraded:
  mencoder mozilla-mplayer mplayer xserver-xorg-input-synaptics
4 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 12.2MB of archives.
After unpacking 16.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper/3v1n0 libdivxdecore0 1:5.0.1-1
  The HTTP server sent an invalid reply header
Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper/3v1n0 libdivxencore0 1:5.0.1-1
  Bad header line
Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper/3v1n0 mplayer 2:0.99+1.0-pre8-0ubuntu4
  The HTTP server sent an invalid reply header
Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper/3v1n0 mozilla-mplayer 3.31-3v1ubuntu2
  Bad header line
Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper/3v1n0 xserver-xorg-input-synaptics 0.14.6-3v1ubuntu0
  The HTTP server sent an invalid reply header
Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper/3v1n0 mencoder 2:0.99+1.0-pre8-0ubuntu4
  Bad header line
Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxdecore0_1:5.0.1-1_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxdecore0_1:5.0.1-1_i386.deb)  The HTTP server sent an invalid reply header
Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxencore0_1:5.0.1-1_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxencore0_1:5.0.1-1_i386.deb)  Bad header line
Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mplayer_0.99+1.0-pre8-0ubuntu4_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mplayer_0.99+1.0-pre8-0ubuntu4_i386.deb)  The HTTP server sent an invalid reply header
Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mozilla-mplayer_3.31-3v1ubuntu2_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mozilla-mplayer_3.31-3v1ubuntu2_i386.deb)  Bad header line
Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/xserver-xorg-input-synaptics_0.14.6-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/xserver-xorg-input-synaptics_0.14.6-3v1ubuntu0_i386.deb)  The HTTP server sent an invalid reply header
Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mencoder_0.99+1.0-pre8-0ubuntu4_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mencoder_0.99+1.0-pre8-0ubuntu4_i386.deb)  Bad header line

I can indeed connect to those URLs in a web browser, and I read [http://www.ubuntuforums.org/showthread.php?t=266590&highlight=can%27t+ping+repositories](http://www.ubuntuforums.org/showthread.php?t=266590&highlight=can%27t+ping+repositories) but don't have the offending line in my own config file. 

Can somebody help with these two issues?

Thanks

---

### Post by d3v1ant_0n3 on 2006-12-21
Looks like a problem with Tr3vinos repos...if you can connect to the repos manually, you could try downloading the debs you need and installing them with gDebi or something?

---

