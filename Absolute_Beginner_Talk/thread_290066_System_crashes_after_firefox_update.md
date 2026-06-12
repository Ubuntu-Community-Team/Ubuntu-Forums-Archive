---
title: "System crashes after firefox update"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Sereoph on 2006-10-31
Hi Everyone

Sorry about the long thread but I've got myself into a serious problem with my Ubuntu 6.06 system.

I've had some problems with Firefox closing unexpectedly, they were getting worse so I tried upgrading (I'm not sure which version I had before and after the upgrade).  After I upgraded I started having problems with the main system.  After restarting the computer the gnome crashes unexpectedly and then has problems reloading and logging in.  I tried opening Synaptic to try using a different version of Firefox though when opening Synaptic I found I had more than 70 broken packages.  Unfortunately Synaptic crashed before I was able to repair the packages.

I tried restarting the computer into the console and running apt check to find out the broken packages, I then tried to repair a package but encountered a problem :
apt-extract templates error loading shared libraries libgcc_s,so.1 Parse error - 'var/lib/dpkg/status' near line 31 
package libgtkspel10. depends Field. invalid package name 'li'fontconfig1'

I've been through the status file and renamed all the references to li'fontconfig1 to libfontconfig1.  This seems to have resolved the issue with the broken packages.  Unfortunately I'm still having problems with my system closing unexpectedly then not being able to log in.  I can boot into the console (usually) or go to console from the Gnome but I have no internet access from this system due to these problems.  While in Gnome I can load applications such as Evolution and File System and have backed up my important files to another partition, although both applications tended to close unexpectedly - when the File System crashed it did the same as explorer crashing on XP, i.e. restart of desktop, but this didn't always happen and I ended up logged out and not being able to log back in.

When logging in one of three things generally happens, 1. I can log in (not usually), 2. It just takes me to another log in
screen, 3. I get the message :
Greeter application failed to start, switching to a new one.
This leads me back to the start of the paragraph.

I have tried to boot onto the Live CD (for both 6.06 and 5.1) but it doesn't load, it just comes up with the error :
Init: ID (1-6) respawning too fast: disabled for 5 mins
It then repeats this every few mins and does nothing else.

I also get some other intermittent errors that I did not get before, these are :-

When loading the Gnome :
The panel encountered a problem while loading "OAF11D:GNOME_Mixer Appplet"

When shutting down :
Unmounting local file system -Fail
(in the console)  /etc/rc0.d/s40umountfs: Line 19: 12194 segmentation fault umount -r -d $DIS
Shuttingdown LVM Volume groups  /etc/rc0.d/s50LVM: Line 40: 12230 segmentation fault /sbin/vgchange --ignore 
locking failure -a n7/dev/null 2>&1

Other error messages :
Enterprise Volume Management System
/etc/rc5.d/s27evms: Line 23: 3386 segmentation fault evms_activate 7/dev/null 2>&1

You are missing a dpkg - start override on /var/run/hplip Fix it otherwise you risk silent breakage on upgrades

/etc/rc2.d/s18hplip: Line 81: 4199 segmentation fault start-stop-daemon ${start} 7/dev/null 2>&1

LibClamAVError: can't load /var/lib/clamav/main.cvd: MD5 verification error  Error: MD5 verification error
eth1: error fetching interface info.dev

Starting HPLinux Printing and Imaging System.
Unrecognized character \X08at /usr/share/perl/s-8/Exporter/Heavy.pm Line 20
Compilation failed in require at /usr/share/perl/s-8/Exporter.pm Line 17
BEGIN failed - compilation aborted at /usr/sbin/spkg - stat override line 4

The Grub version I'm using is 0.97
The Ubuntu kernel versions I'm using are
		2.6.15-27-386
		2.6.15-26-386
		2.6.15-23-386

I know that this is a long post but I've tried to include all the different things that are going on with my system.  I've tried going through this and other forums and have found very little that has helped me.  I did try using a post about the greeter application failed to start, the post talked about problems with gtk+2.0 but due to the problems with my internet connection I couldn't update it.  Also the post was dated 1st march 06 and the problem was supposed to have been fixed so the version I have should be the updated version as I have been keeping my system up to date.  I'm relatively new to Ubuntu and any help would be greatly appreaciated.

---

