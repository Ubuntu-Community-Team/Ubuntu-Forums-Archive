---
title: "Ubuntu ISO not mounted by OSX (Mountain Lion)"
date: 2012-12-12
forum: Apple Hardware Users
---

### Post by dmuos on 2012-12-12
Hello

I have  downloaded ubuntu-12.04.1-desktop-i386.iso and burnt that on DVD with a Mac (Mountain Lion). I have used the disks successfully on other computers so I think both the download and burnings are healthy.

By chance (to check the contents of the DVD), I inserted in the Mac and it gave me "the disk you inserted was not readable in this computer". Well, of course I thought that the disk had gone bad; but then I tried the downloaded ISO and it said "couldn't be opened", reason "no mountable file systems".

I do not have another computer here right now, so I cannot check that DVD.

Is this the normal behaviour on Macs? It is only that I cannot even read the DVD label, Diskutil gives as name/label only disk1s1.

Might it be pssible that by sheer coincidence both the iso file and the DVD has gone bad, and thus I have to do a new burning?

If someone knows about this behaviour, I would appreciate your comments.

Thanks in advance

D

---

### Post by dmuos on 2012-12-15
I reply to myself as I have found what appears to the same issue  happening to an earlier version of Ubuntu in earlier OSX, just in case,  others find the same issue and are not searching a particular Ubuntu  version.

It seems that this is due to a "clever" way to package the ISO so that  it can be deployed in a easier manner with other systems. This is  discussed at some length in thread
[http://ubuntuforums.org/showthread.php?t=1870261](http://ubuntuforums.org/showthread.php?t=1870261)  (ubuntu-11.10-desktop-i386.iso has 'no mountable file systems'?). In  #29 (by daviddryderuk) it is explained that the issue may be caused by  the iso being a "hybrid CD/USB image" (and therefore is happening in  11.10 and above).

I must say that, in my case, a direct Terminal 'dd' of the downloaded  ISO (ubuntu-12.04.1-desktop-amd64.iso) produced a Ubuntu Live DVD for  non-Macintosh boxes (though I have read that method might be "broken in a  very large number of BIOSes" as per [http://www.syslinux.org/wiki/index.php/Doc/isolinux#BOOTING_DOS_.28OR_OTHER_SIMILAR_OPERATING_SYSTEMS.29](http://www.syslinux.org/wiki/index.php/Doc/isolinux#BOOTING_DOS_.28OR_OTHER_SIMILAR_OPERATING_SYSTEMS.29)).


To get a working Ubuntu Live on my 2012 Macbook, I had to follow the  advise of mypalmike in same thread 1870261 as presented in #43.  Essentially

1-Use Disk Utility to discover the "real" iso partition: double-click on  the image, Disk Utility will say that it is a "non mountable file  systems", you say OK; on the disks section there will be displayed  a (faded) diskname, diskNs1 (where N is a number depending on how many  disks are mounted).

1.5-To make sure, in Terminal, you can run "diskutil list" where you will  see that Disk Utility has indeed done the thing right (remember it is  only "s1" part what is needed). 

 2-Run in Terminal "dd if=/disk/rdiskNs1 of=./ubuntu-reg_iso.iso bs=1m"
[with the usual caveats for dd  in bs and the r in 'rdisk' and the  proper value for N; iso file in (Terminal's) current directory, nb: './'  after 'of=' and sudo permissions]

3-File ubuntu-reg_iso.iso is a regular iso file which can be burnt and used in Macs
(or indeed the file can be mounted by OSX in the hard drive as usual).

I have not tried yet, but I expect that this regular iso can be used to create a  bootable USB key with Ubuntu Live with the instructions supplied  in ubuntu.com advise on installation with Macs. (Did not work for me  trying with the downloaded file either.)

I would suggest including a little note in the OSX section of the  installation, as I burnt unnecesarily an extra DVD and downloaded more  than once because this mount error is also given for corrupted  downloaded images, it took me also some time locating the right info.

---

