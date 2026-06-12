---
title: "[SOLVED] Edubuntu Flight CD 4"
date: 2006-02-21
forum: Announcements &amp; News
---

### Post by Jane Weideman on 2006-02-21
Hello Edubuntu community, 

The Edubuntu team is happy to announce Edubuntu Flight 4, the 4th
milestone CD image in the Ubuntu 6.04 "Dapper Drake" development cycle.

You can download Edubuntu Flight 4 from the following mirrors: 

   * Europe: 
[http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/edubuntu/releases/dapper/flight-4/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/edubuntu/releases/dapper/flight-4/) 

   * United Kingdom, and the rest of the world: 
[http://cdimage.ubuntu.com/edubuntu/releases/dapper/flight-4/](http://cdimage.ubuntu.com/edubuntu/releases/dapper/flight-4/) 

A list of other mirrors are also available at:
[http://wiki.ubuntu.com/Archive](http://wiki.ubuntu.com/Archive). 

To save on bandwidth, we recommend downloading the images using
BitTorrent. 

Apart from the notable changes in this release that apply to all Ubuntu
flavours, which are listed at:

[https://lists.ubuntu.com/archives/ubuntu-announce/2006-February/000050.html](https://lists.ubuntu.com/archives/ubuntu-announce/2006-February/000050.html) and 
[https://wiki.ubuntu.com/DapperFlight4](https://wiki.ubuntu.com/DapperFlight4) 

the following additional Edubuntu-specific enhancements have gone into
this milestone release: 

LTSP Flight 4 Featurelist: 

Multiarch Support 
        
      * PowerPC support was added. Please note however that there is
        still a small bug in the chroot handling in the client chroot
        builder of the installer, please run sudo ltsp-update-kernels
        manually after installation. 
                
      * The multiarch code saw plenty of other improvements and fixes. 
                

Less Memory consumption 
        
      * LTSP now finally supports the X_COLOR_DEPTH variable to force
        the usage of 16Bit on the clients through lts.conf. 
        
      * By default we now install only the linux-image package in the
        client chroot, the excessive memory usage of the restricted
        modules package is gone 
        
      * A special netboot mode was added to initramfs so only network
        device drivers are loaded, this reduces the size to two thirds
        of a normal initramfs 
                
        
Serial Mouse Support 
        
      * LTSP now understands the X_MOUSE_DEVICE and X_MOUSE_PROTOCOL
        lts.conf options and adds support for various serial devices
        from ipaq touchscreens and over plenty of mouse protocols up to
        some serial tablets. 
        
      * 3 button emulation of 2 button mice is now supported as well. 
                
        
Bootprocess 
        
      * The bootprocess has seen further speed improvements, lts.conf
        values process code only if they carry a value during startup
        now. 
        
      * As mentioned in a previous section, netboot mode speeds up the
        loading of the initramfs through the size reduction. 
        
      * Startup links in rcS.d and rc2.d are now started based on
        whitelists (RC2_WHITELIST RCS_WHITELIST), only the bare minimum
        of processes is started on the thin clients - this results in a
        shorter boottime. 
        
      * Usplash was included and enabled by default, got better default
        values to prevent it from timing out on very low level clients,
        you will have bootsplash love all over now :)
                

General Improvements 

      * Many patches were merged from the debian team to make the
        packages work on debian as well. 
        
      * Sound support saw some smaller changes and bugfixes 
        
      * The ltsp-build-client script now has options to manually enable
        extra and security mirrors during chroot creation. 
        
      * The default mirror of ltsp-build-client points to
        archive.ubuntu.com now. 
                
        
We have working LiveCDs for all arches! Enjoy ! 

The new artwork infrastructure is in place, you will be able to easily
select your theme by age once we have the artwork in place. 


Current known issues and bugs in this alpha release include: 

      * PowerPC LTSP support is still experimental, see the features
        section for more information. 
        
      * As previously mentioned there is a bug in the chroot handling in
        the client chroot builder of the installer, please run sudo
        ltsp-update-kernels manually after installation 
        

If you are interested in following changes as we continue to develop
Dapper, have a look at the dapper-changes list: 

[http://lists.ubuntu.com/mailman/listinfo/dapper-changes](http://lists.ubuntu.com/mailman/listinfo/dapper-changes) 
        

Edubuntu Specific Development and News is listed on: 

[http://lists.ubuntu.com/mailman/listinfo/edubuntu-devel](http://lists.ubuntu.com/mailman/listinfo/edubuntu-devel) 
        

We also suggest that you subscribe to the ubuntu-devel-announce list if
you are interested in following Ubuntu development. This is a
low-traffic list (a few posts a week) carrying announcements of approved
specifications, policy changes, alpha releases, and other interesting
events. 

[http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce) 
        

Please take a look at the testing area of the wiki, which suggests
various tests that can be performed on the Flight CD releases to help us
to catch any remaining bugs, thus allowing us to fix them well before
for the final release: 

[http://wiki.ubuntu.com/Testing/CurrentEdubuntu](http://wiki.ubuntu.com/Testing/CurrentEdubuntu) 
        

Bug reports should go to our Launchpad bug tracking facility called
Malone: 

[https://launchpad.net/malone](https://launchpad.net/malone) 
        

Have fun with testing and bugfiling! 

Oliver Grawert 


-- 
JaneW
_____________
Jane Weideman
mobile: +27 83 779 7800
Canonical Ltd.



-- 
ubuntu-announce mailing list
[email]ubuntu-announce (AT) lists (DOT) ubuntu.com[/email]
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-announce)

---

