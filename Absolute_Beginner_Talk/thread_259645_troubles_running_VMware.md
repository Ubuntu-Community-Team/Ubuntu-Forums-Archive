---
title: "troubles running VMware"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by dbonline on 2006-09-17
I have been using Ubuntu and VMware for well over a month now. I recently clicked the 'update' icon in Ubuntu, did the update and for some reason since I updated Ubuntu my VMware has stopped running. I click to run VMware and it thinks for about 30 seconds or so, my mouse pointer goes back to original state but VMware doesn't open.

If anyone here has any idea why this could be, or how I could go about fixing it w/out having to reinstall my secondary OS I would really appreciate any help I can get. Thanks in advance!!

---

### Post by bulldog on 2006-09-17
Yes you have to reconfigure it.

type vmware in your terminal and you get the messages how to do it.

/usr/bin/vmware-config.pl

if I'm not mistaken.

You have to do this after each kernel-update.
Your virtual machine are not affected by this.

---

### Post by dbonline on 2006-09-17
thanks for the reply bulldog. I tried that, and got the following error msg's

ERROR: ld.so: object '/usr/lib/libdbus-1.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libdbus-1.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libdbus-1.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libdbus-1.so.3' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Unable to alloc client: Cannot open file "/home/darryl/.vmware/preferences": Permission denied.



VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: Cannot open file "/home/darryl/.vmware/preferences": Permission denied.

---

### Post by x64Jimbo on 2006-09-17
sudo vmware-config.pl

---

### Post by bulldog on 2006-09-17
> **x64Jimbo said:**
> sudo vmware-config.pl

Yep it should be 

sudo /usr/bin/vmware-config.pl

You must have had that warning.

If it fails just reinstall vmware,it will uninstall first,but I'm not sure if it affects your virtual machines.

---

### Post by dbonline on 2006-09-17
thanks for the support guys, I typed

sudo /usr/bin/vmware-config.pl

in the terminal, went through all the steps and when it completed said it was successful, yet strangely enough when I clicked to run VMware same thing happened, no error msg or anything, simply nothing would open.

I even tried rebooting, but that did not do the trick either. any other suggestions or do you think I'll need to re-install? I prefer not to have to reinstall because I fear losing all the information on my secondary OS partitioned drive.

---

### Post by -deadcats on 2006-09-17
First, download the latest VMWare build if you haven't already. I believe the latest is 5.5.2.29772. Your 5.x key works with all 5.x versions, so it's free if you already own a 5.x copy.

Second, you should probably uninstall VMWare and then reinstall, then run the configuration script again. It seems VMWare's just one of those applications that does better when you do so--anyway, lots of posts confirm that. The instructions on how to uninstall it are included in the expanded .tar.gz you installed it from initially. It should have no effect on any of your already-created .vmx's etc.

Third, get used to having to rerun the vmware-config.pl whenever you do any major system alterations, like upgrading kernels or installing nVidia drivers. It's not always the case, but it tends to be.

regards,
-dc

---

### Post by dbonline on 2006-09-18
I completely reinstalled VMWare server from scratch now and this is what I ge t when I try t run it

desktop:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Unable to alloc client: Cannot open file "/home/darryl/.vmware/preferences": Permission denied.



VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: Cannot open file "/home/darryl/.vmware/preferences": Permission denied.

BUT

$ sudo vmware starts the VMware server

---

### Post by andb on 2006-09-18
does the file /home/darryl/.vmware/preferences exist? If so, who is set to be the owner and what are the read/write permissions? The first answer would seem to be something that can be fixed with chmod or chown. Assuming it does exist and you wanted to just start fresh, you could also rename the .vmware directory to .vmware_old or something, and let vmware make a new directory. By reinstalling / renaming you'll probably lose any custom setup that you had, like additional hardware to emulate but of course your disk images should be fine.

---

### Post by x64Jimbo on 2006-09-18
sudo chown -R darryl /home/darryl
When you run vmware as root it takes ownership of the files and makes them non-accessible by non-root users. This command will re-take ownership of your home folder.

---

### Post by BLTicklemonster on 2006-11-26
Thank you! This has bugged the hell out of me for a while now.

---

### Post by BLTicklemonster on 2006-11-26
icewm themes [http://www.skinbase.org/mskins.php](http://www.skinbase.org/mskins.php)

extract them to /usr/share/icewm/themes and have at it.

---

