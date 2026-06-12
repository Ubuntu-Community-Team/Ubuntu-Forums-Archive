---
title: "Sharing Torrent Downloads Between XP and Ubuntu"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by jfxr1 on 2007-03-21
Hi,
I sometimes use XP and sometimes use ubuntu on my dual boot laptop.  If I started downloading a torrent while on XP is there any way to keep the same torrent downloading when I boot into Ubuntu?

---

### Post by Kobalt on 2007-03-21
I think your downloaded files would need to be on a shared partition between Ubuntu and win, then you would need to use the same torrent client on both OS, that is to say µTorrent (running with Wine in Ubuntu)... and I guess I'm forgetting something.
Sounds like a tricky affair to me.

---

### Post by belikralj on 2007-03-21
I don't think it's possible because bittorrent in windows can't restart the download when you remove it's reference but not the data and then if you try to resume from data it fails and starts from begining. But I may be wrong, I hope so because it is a very handy thing :)

---

### Post by bigee1212 on 2007-03-21
well, as long as you have the actual torrent file saved (the .torrent), you can do it on both computers. If you set up ubuntu to be able to read/write to your ntfs windows partition, you can just open up the torrent in linux, and set the download location to the same exact location. Most programs will just detect what files you already have and continue the download...

---

### Post by rodrigo666 on 2007-03-23
I used to do that with uTorrent in Ubuntu and Windows. But now I'm searching for a linux-native client for torrents and don't want to download in Windows.

But, the bottom line is, yes, it's possible. I bet there's a million ways to do that, with uTorrent in both OS is just one of they.

---

### Post by garybrlow on 2007-04-04
HOWTO Share Torrent Downloads Between XP and Ubuntu on an NFS partition:

It can be done, I do it all time. :P

Here's what you do
1)Currently I use uTorrent on Windows and uTorrent wine in LInux. You can can also use  
    Azureus for Windows and Linux you can even interchange uTorrent and Azureus as long as 
    they point to a common download location. I use a dual boot environment and I can not vouch   
    for virtualized environments but theoretically they would be the same somewhat.

2)Normally I separate all my downloads in both for Linux and Windows on another but 
   commonly used partition namely Drive D:\,  name it DOWNLOADS and create a folder named 
   BITTORENT (D:\BITTORENT). Both Azureus and uTorrent customized download locations and 
   supports moving downloaded files to another location when done so I organize my Bittorent 
   folder with subfolder like the ones below.
  
   WINDOWS dowvload paths setting for uTorrent and Azureus:
   D:\BITTORENT\FINISHED\
   D:\BITTORENT\UNFINISHED\
   D:\BITTORENT\TORRENTS\

   LINUX(whatever buntu :p) download paths setting for uTorrent and Azureus:
   /media/hda6/BITTORENT/FINISHED/
   /media/hda6/BITTORENT/UNFINISHED/
   /media/hda6BITTORENT/TORRENTS/

   note: replace hda6 with what ever drive/partition you use as for me D:\ = /media/hda6

   You don't have to follow my set paths above. Your current setting should be fine. Its just to give 
   you an idea between the similarities and differences of Windows/Linux mount point/path 
   settings and customize them to your own needs.
   
3)If you already haven't done so, you need to enable reading and writing from and to an NTFS 
    partition. You need to use ntfs-3g and ntfs-config  packages to achieve this. Read about it and 
    get them here [www.ntfs-3g.org](www.ntfs-3g.org). Ntfs-config makes the configuration easier by using 2 
    clicks and thats it only so it is very recommended for everyone. You may need to reboot 
    afterwards.

4)After rebooting ubuntu, open uTorrent or Azureus and open the torrent file of the unfinished  
   download you had in Windows. Now as long as uTorrent and/or Azureus is pointing to the 
   same download paths as with the Windows versions, they will just check the integrity of the 
   partially downloaded file and then resume it until its done. If it dosen't check automatically, 
   you must Force Check the torrent to ensure that it registers and takes into account the data 
   chunks that were downloaded in the other OS. I suggest doing this on every OS switch upon 
   using uTorrent to prevent overwriting of already saved data which may cause inconsistencies
   that may lead to data corruption and eventual loss of data.

5)You can do this back and forth across Windows and Linux as long as ntfs-3g is functioning 
    properly everything works fine. Once in a while uTorrent  or Azureus may complain that it can't 
    write or save data, this is a sign that the NTFS has errors in it which usually brought about by 
    data corruption, power outages, defragmentation etc. If this happens you have to reboot into 
    Windows and run chkdsk /f on that drive. Ntfs-tools doesn't have a chkdsk equivalent yet so 
    you really have to reboot into Windows. Once the errors are fixed, reboot to Ubuntu and you're 
    good to go.

6)Improper unmounting of NTFS drives in Windows will cause you NTFS-3G drive partitions to 
    be unaccessible in Linux. If this happens you have to reboot back to Windows, do a chkdsk to fix
    errors if any, and shutdown Windows properly. Always remember to shutdown Windows properly
    else the NTFS-3G drives will not be registered in the fstab due to inconsistencies.


Well I certainly hope this helps the lot of you. Enjoy your torrents!!! He he :p


Cheers!!!


GaryBrlow :biggrin:

---

### Post by szaka on 2007-04-04
Could you please tell more to us, developers, that what kind of NTFS errors uTorrent or Azureus complain about? There was indeed some problems in older ntfs-3g drivers but we are definitely not aware of any since the stable releases (verison 1.0 and up). 

Thank you in advance,  

Szaka

---

### Post by garybrlow on 2007-04-08
Its not really as dire an error as to what was experienced before in ntfs-3g prior to 1.0 and up.  Azureus keeps on crashing on my machine due to resource limitations so I can't really give much input on it. But with uTorrent since I use it all the time I could probably give one or two. 

Recently after a series of updates in feisty, out of the blue ntfs-3g suddenly spit out operation not supported errors. Even uTorrent  says it is unable to write, retry/cancel. After reading change logs and announcements over at [www.ntfs-3g.org](www.ntfs-3g.org), ver 1.328 was available. Compiling and installing it seemed to solve my write problems.

The unable to write error in uTorrent occurs once in a while. I noticed it is mostly caused by corrupted written blocks in the destination file. Since there is no equivalent of the chkdsk utility in ntfstools. A reboot to windows is needed and chkdsk /f needs to be performed to fix the error. There are times when chkdsk /f results in no error to be fixed at all. Going back to Linux you still get the unable to write error. A reinstall of uTorrent usually solves this problem. In case all else fails a reinstall of ntfs-3g usually does the trick. Am not really sure what causes this but in uTorrent's case its not fully functional in the sense that is quite usable but sometimes it has quirks in Wine

---

### Post by szaka on 2007-04-09
Thank you for the explanations.

> Recently after a series of updates in feisty, out of the blue ntfs-3g
> suddenly spit out operation not supported errors. Even uTorrent says it
> is unable to write, retry/cancel. After reading change logs and
> announcements over at [www.ntfs-3g.org](www.ntfs-3g.org), ver 1.328 was available. Compiling
> and installing it seemed to solve my write problems.

File creation can be denied still in certain rare cases (without the risk
of any kind of data corruption). If you're interested then you can find
more information on this at [http://ntfs-3g.org/support.html#filecreate](http://ntfs-3g.org/support.html#filecreate)

Version 1.328 should indeed improve the situation because it tries hard to
minimize fragmentation. But work is still ongoing in this area.

> The unable to write error in uTorrent occurs once in a while. I noticed
> it is mostly caused by corrupted written blocks in the destination file.

What kind of corruption do you mean? Failed file checksum is reported 
by uTorrent? Torrent clients typically check file integrity after downloads
and nobody is reporting corrupted files unless they have a hardware 
problem (typically disk or RAM).

> Since there is no equivalent of the chkdsk utility in ntfstools.

ntfsresize --info <device> is equivalent to a one-pass chkdsk. This was one
of the very first NTFS utilities I wrote 5 years ago and still used very
intensively to day for checking NTFS consistency during development.
However it still can't fully replace chkdsk.

> A reboot to windows is needed and chkdsk /f needs to be performed to fix
> the error.

Could you please send all these errors? They are saved and can be found
following these steps: [http://en.wikipedia.org/wiki/CHKDSK#Viewing_results](http://en.wikipedia.org/wiki/CHKDSK#Viewing_results)

> There are times when chkdsk /f results in no error to be fixed
> at all. Going back to Linux you still get the unable to write error.

Chkdsk can't solve the "operation not permitted" file creation errors, only
an appropriate defragmenter, until we can implement the needed support.

> A reinstall of uTorrent usually solves this problem. In case all else
> fails a reinstall of ntfs-3g usually does the trick. Am not really sure
> what causes this but in uTorrent's case its not fully functional in the
> sense that is quite usable but sometimes it has quirks in Wine

Yes, I also think some WINE bugs are probably involved here, if they are
not hardware related.

Could you please also send the outputs of
grep -ie 'ntfs\|dma' /var/log/messages /var/log/messages.log /var/log/daemon.log

The files my have been rotated and compressed, in that case please use
zgrep -ie 'ntfs\|fuse' /var/log/messages*gz /var/log/daemon.log*gz

Thank you again,  Szaka

---

### Post by garybrlow on 2007-04-11
Szaka,

Here are the logs you asked for. Hope this helps you. Most of the data error/corruption I got resulted from non-properly exited and interrupted write process. They are brought about by power interruptions, a desktop/application freeze  resulting to a sudden hard reboot. I also had uTorrent  complaining of a Disk Overload when more than one application is writing on an ntfs-3g partition. So I usually keep only one application writing on it at an instance. I wonder if there is a speed penalty for reading and writing on the same ntfs-3g partition it tends to be a little bit slower or something. Well am not really sure its actually an ntfs-3g problem but it might be a process scheduling  and memory allocation thing with wine and utorrent in conjunction with other applications accessing the partition at the same time.

My NTFS-3G is shared on Dual Boot with windows and xubuntu. on windows its assigned as Drive F: and labeled as MYFILES. on LInux its mounted by ntfs-3g on /media/hda6.

I can't seem to attach files so here is A link to the zipped logs [http://creativepitstop.3000mb.com/temp/GaryBrlow_logs.zip](http://creativepitstop.3000mb.com/temp/GaryBrlow_logs.zip). Contained in the archive are NTFS CHKDSK ERROR/REPAIR logs and NTFS-3G logs.


Cheers!!!


GaryBrlow :biggrin:

---

### Post by david_kt on 2007-04-12
> **garybrlow said:**
> 

4)After rebooting ubuntu, open uTorrent or Azureus and open the torrent file of the unfinished  
   download you had in Windows. Now as long as uTorrent and/or Azureus is pointing to the 
   same download paths as with the Windows versions, they will just check the integrity of the 
   partially downloaded file and then resume it until its done.

I thought we must do "force recheck" when switching to another OS. Because I notice that if I have downloaded 40% in XP, and then continue to download in ubuntu and reach 55%, it will show only 40% if I switch back to XP (unless I do force recheck).

Another thing is that everytime you switch, you will lose uncompleted pieces (a few MB, depend on the size of the pieces). So, sometime I download from beginning in XP, and from end in ubuntu, to avoid force recheck and not losing any uncomplete pieces.

DK

---

### Post by szaka on 2007-04-12
Hi GaryBrlow,

> Here are the logs you asked for. Hope this helps you.

Thanks. At the moment I can't resolve and contant the reativepitstop.3000mb.com
address. I've tried it from all over the world, from several places, still no go. I can only 
see that the domain registrar is Go Daddy. I'll keep trying but you might need to 
put it somewhere else if it remains "invisible".

> Most of the data error/corruption I got resulted from non-properly exited
> and interrupted write process. They are brought about by power
> interruptions, a desktop/application freeze resulting to a sudden hard
> reboot.

Hard reboots, without cleanly unmounting the filesystem, always leave
behind inconsistencies for any file system.

The data flow in the computer is like pouring water from the high (RAM) to
a dish (disk). The clean unmount is like pouring all the water to the dish.
The unclean one (power outage, hard reboot, reset) is like if you're pushed
and some water going outside of the dish. They are lost. Exactly the same
happens during hard reboot. The flow of bits are going around in the computer 
is lost, not written permanently to the disk because no power, no electric
fields which could store these information anymore during the saving
process.

> I also had uTorrent complaining of a Disk Overload when more than
> one application is writing on an ntfs-3g partition. So I usually keep
> only one application writing on it at an instance. I wonder if there is a
> speed penalty for reading and writing on the same ntfs-3g partition it
> tends to be a little bit slower or something. Well am not really sure its
> actually an ntfs-3g problem but it might be a process scheduling and
> memory allocation thing with wine and utorrent in conjunction with other
> applications accessing the partition at the same time.

Could be. Also ntfs-3g 1.328 must keep up with the read/write speed the
best. If still not, then try to make some adjustments in the uTorrent Disk
Cache.

The uTorrent FAQ document also states that if Disk Overload happens when
adding a torrent, then it's normal, and is a design limitation in µTorrent, which 
will be fixed in the future. The problem is not due to the disk is actually being 
overloaded. The warnings should disappear after a few minutes.

Cheers,   Szaka

---

### Post by garybrlow on 2007-04-13
Szaka,

Hmm they probably are down for maintenance again. Rapidshare is not really user friendly and have limited slots for Asian IPs so I can't upload there. Anyone have better suggestions for file sharing hosts? If you can PM me your email address I'll send the logs directly to your email.

---------------------------------------------------------------------------------------------------------------------------------------
david_kt,

Thanks for reminding me. Yes it is true that you have to do a Force Recheck when switching OSes because the torrent clients won't know the more data chunks were downloaded since the last time it accessed the torrent. You don't necessarily loose data on OS switching, bittorrent is not exactly perfect and tend to loose some of its data on normal operations. There are times when it says its already 100% but if you Force Check it is not, some chunks fail the check and have to be re-downloaded. I normally Force Check a finished torrent twice or even thrice to ensure its completion. This happens irregardless of OS. That is why I prefer ABC Torrents double and/or triple checking feature. Azureus also executes a Force Check on 100% completion while its seeding. uTorrent does not have these features, you have to manually Force Check torrents after completion.


Cheers!!! :)


GaryBrlow :biggrin:

---

### Post by szaka on 2007-04-13
> **garybrlow said:**
> Hmm they probably are down for maintenance again. Rapidshare is not really user friendly and have limited slots for Asian IPs so I can't upload there. Anyone have better suggestions for file sharing hosts? If you can PM me your email address I'll send the logs directly to your email.

Still no luck with the download. My email is [email]szaka@sienet.hu[/email]. Thanks!

Szaka

---

### Post by garybrlow on 2007-04-16
Szaka,

The 3000mb web host is like dead now. Your email host rejects anything from yahoo (I got a Mailer Daemon error regarding not being allowed to send mail to your host from your host server). I finally found a site I could upload to. Its not exactly firefox friendly but hey, at least it works. :)

Linky to logs is found here: [http://www.snapdrive.net/files/400894/public/GaryBrlow_logs.zip](http://www.snapdrive.net/files/400894/public/GaryBrlow_logs.zip).


Cheers!!!


GaryBrlow :biggrin:

---

### Post by szaka on 2007-04-19
Thank you, got them. Quite a lot of info, it will take a few days to analyze. I'll let you know when it's ready.

Cheers,   Szaka

---

### Post by szaka on 2007-04-23
Hi,

Here are the findings:

NTFS-3G log:
- apparently you're not using yet at least version 1.328
- once you run out of disk space (Apr 10)
- file creation was denied several times because of
  [http://ntfs-3g.org/support.html#filecreate](http://ntfs-3g.org/support.html#filecreate)
- no signs of hardware error
- strangely ntfs-3g versions aren't in the log but they should be

chkdsk log:
- old errors are fixed in later versions of ntfs-3g
- other documented problems:
  [http://ntfs-3g.org/support.html#cleaningup](http://ntfs-3g.org/support.html#cleaningup)
  [http://ntfs-3g.org/support.html#minorinconsistency](http://ntfs-3g.org/support.html#minorinconsistency)
  [http://ntfs-3g.org/support.html#indexo](http://ntfs-3g.org/support.html#indexo) 
- When there is a chkdsk message like "Chkdsk cannot run because
  the volume is in use by another process. ..." then it's not safe
  to use it and inconsistencies are expected to be found ususally. 
  Most of the checks were done this way. The safe way is to run 
  chkdsk /f and then reboot.

I've also added more details to NTFS-3G logging in many places, 
so similar analyses can be done easier in the future.

Thank you for the logs and if you find new, not yet documented 
ones then please let me know!

Cheers,  Szaka

---

### Post by garybrlow on 2007-04-28
Szaka,

No probs. Am using ver. 1.328 now but most of my errors happened before this version as you noticed that my logs go way back  2006.

If you need more info just ask. :P


Cheers!!! :)

GaryBrlow :biggrin:

---

### Post by shafin on 2007-07-10
Thanks For the help,just got it Working :)

---

