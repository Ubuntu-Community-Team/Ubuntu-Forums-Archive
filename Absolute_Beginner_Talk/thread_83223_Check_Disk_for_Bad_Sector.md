---
title: "Check Disk for Bad Sector?"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by jeffreyvergara.NET on 2005-10-28
Hello, since I installed Ubuntu, I think I did a clean installtion for I think more than 20x, thus erasing my HD several times in just a month.

Is there any tool to check for Bad Sectors of my HD like Scandisk in Window$?

---

### Post by zerhacke on 2005-10-28
I believe the command is "fsck -pc -l somefilename" or something similar to that.  

man fsck

---

### Post by poptones on 2005-10-28
Are you having problems wiht the computer? Or are you just worried that "erasing" the hard drive (you don't) might cause trouble?

If you have reinstalled 20x because you HAD to - because the machine is acting up - you should do a proper hard drive test. If you have a maxtor , WD or Seagate drive then go to their website and download their disk diagnostic tool. You can get a version of the maxtor tool (works with seagate and WD) as a bootable ISO image that you can burn to a CD. Y9ou boot directly from the CD and it will perform comprehensive low level tests of your drive (and fix it, if possible).

---

### Post by jeffreyvergara.NET on 2005-10-28
I just encountered problems with inode (<y> to fix )something like that on boot (just reboot the Pc normally) so I think that my HD has a problem because I erased my HD too many times trying to install Ubuntu (failed on the last part of the installation, after the first Ubuntu Bootup)

Im going to check the maxtor tool, im using WD.

edited:

I found a diagnostic tool for WD so I think that's will I use, it's only 1 diskette unlike tools for Maxtor(64mb++)

---

### Post by patrick295767 on 2005-10-28
[QUOTE=zerhacke]I believe the command is "fsck -pc -l somefilename" or something similar to that.  

man fsck[/QUOTE]
  
Is effectively that fsck can look sector per sector the full harddisk ?
Is there a way with qtparteed to exclude the bad sectors from the used free space ? (to fix)
  
I mean sthg similar as :
chkdsk c: /f /r

thanks a lot

patr'

---

### Post by poptones on 2005-10-28
To rempa bad clusters on an ata drive you have to perform a write to *exactly* that cluster. When it fails it will then remap the cluster automatically and, thus, fix the problem.

In order to do this with linux you have to go cluster by cluster performing dd writes addressed by sector numbers. I've done this when I had a drive that was going bad and it was largely ineffectual because the drive WAS failing and tools like fsck and qtparted can't tell you this. 

You can run those diagnostic tools without wiping out your data. It's much easier (and much more effective) to run the manufacturer's tool and let it do its job than it is to try to pick apart your hard drive by hand. 

jefferey, you don't "erase" your hard drive when you reinstall ubuntu or any other operating system. You only "erase" a small part of the disc that contains information about the rest of the disc (called the partition table). Believe it or not, *erasing* it might be *exactly* what you need to do; when you erase the drive you force it to write zeroes across the entire platter, When it does this it will automatically remap any bad clusters and (often) fix the problem completely.

What I suggest you do is exactly this: use that tool you downloaded to "write zeroes to drive." It will take some time (at least an hour, possibly even several) and you will absolutely lose *everything* on the drive, so make copies of anything valuable on the drive. When it is done the drive *should* perform like new. If, in a few days, it reports lost clusters again, then you can be dead certain you have a failing hard drive that simply must be replaced.

---

### Post by KiwiNZ on 2005-10-28
Good advise poptones.

Zeroing the drive is the safest way to return it to a known state. The recheck.

Please dont be tempted to do a low level format as some may suggest. this will probably render your drive unuseable.

---

### Post by jeffreyvergara.NET on 2005-10-28
thanks everyone! Im just aliitle bit curious on what have I done with my HD. when I was installing Window$ Os before, there's an option if you want to format your HD  Full format(slowest) and the quick format, someone told me that it's alright to format your HD several times when using quick format, and Full format your HD several times will cause your HD to have bad sectors.

On what I have experienced in installting Ubuntu, it seems it uses Quick Format??? so I think my HD is still in good shape eventhough I reinstalled it several times???

I dont know what's wrong with my installers but all of them does not succeed in doing a clean install of Ubuntu for the first time (have existing OS) like with my clean installtion of Breezy preview to Breezy Final, it took me 4 trial to finish the installtion, it always have error on the last part of the installation (after the first boot), I don't know what to do back then so my only choice to reinstall again. but now i think "sudo apt-get -f install" will do?

---

### Post by poptones on 2005-10-28
Whoever told you that bit about windows and the "full format" is dead wrong. The way you FIX the drive is to make it write to every single writeable location. If ti still fails after that it is simply dead and nothing will ever fix it.

Do what I suggested. If you do not let the drive remap those bad clusters you will never get anywhere.

---

