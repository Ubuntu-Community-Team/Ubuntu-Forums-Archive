---
title: "Easy Peasy on Asus 900"
date: 2012-10-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by zyzzyx01 on 2012-10-03
Hi,
 I have an Asus 900 with easy peasy installed. Suddenly, the  minimum, maximum and close buttons, including the home logo have  disappeared. I have however got the 'File, Edit etc.etc.' tool bar, but  cannot minimise, close or shutdown the pc. Please help.
Memory 1Gb   Extended/expanded second drive has 16GB. 
I cannot download all the new updates as it says "not enough memory". Have tried to use sudo delete, but asks me for my password which I have never, repeat put in. I hope this info is sufficient
Thanks for all the support.

---

### Post by snowpine on 2012-10-03
Welcome to the forums!

Running out of space on your hard drive/SSD can cause all sorts of problems.

Your first problem is your password. Here are easy instructions to reset a forgotten password:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

While you are in Recovery Mode (explained in the link above), here is a harmless command that will hopefully free up a little bit of space, if you haven't run it in a while:

```
apt-get clean
```

Hopefully that will allow you to at least boot the system to a working desktop so you can start going through your /home folder and clearing out some of the documents, photos, files you don't need any more (be sure to empty the trash to actually free the space).

---

### Post by snowpine on 2012-10-03
Also: Easy Peasy is based on Ubuntu, but it is not the same as Ubuntu. There may be subtle differences I am not aware of. They have their own site where you can get help here: [https://getsatisfaction.com/easypeasy](https://getsatisfaction.com/easypeasy) (but the site doesn't seem very active)

---

### Post by zyzzyx01 on 2012-10-03
Will try again, but have tried the apt-get clean  and that was when it kept asking me for passwords. Will get back on forum and inform of the out-come.
Thanks

---

### Post by zyzzyx01 on 2012-10-03
Thanks snowpine, 
Checked all the websites and also did google search, but didn't get anywhere. Will try your solution and see what happens.

---

### Post by zyzzyx01 on 2012-10-04
Hi again, 
I have tried as suggested. Gone into 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode), but still no joy.I pressed enter, and the screen writes until it gets to..... [ 2.886205] Console: switching to colour frame buffer device 128x37. Then below it is the cursor, but cannot type anything.
One more piece of info; on my recovery mode, it says GNU GRUB version 1.98-1ubuntu5. If that helps.
Thank you

---

### Post by snowpine on 2012-10-04
Here's another suggestion: If you make an Ubuntu Live USB (described [here]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows") or [here]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu")) then you can boot from the USB in Live mode (try without installing), navigate to your Asus hard drive, rescue any files you need to back up (copy them to a thumb drive or external hard drive), and then try deleting some files to create some free space on the drive. Be sure to use Shift+Del to delete the files, rather than moving them to the trash. If you get permission denied then you can run the file manager as root with Alt+F2, type 'gksu nautilus' (without the quotes and be VERY CAREFUL if running file manager as root).

Again I am not an Easy Peasy user so I don't have much experience to help you.

---

### Post by zyzzyx01 on 2012-10-04
Okay, looked up my 3.8GB (first hard drive), checked the tmp file. 8 files there; 1) orbit-root  2) orbit-ubantu  3) keyring-93kcXX  4)libgksu-EzoPjv  5)pulse-ieblkqOTH2qn 6)pulse-PKdhtXMmr18n  7) ssh-qbfjsQ1977 and lastly 8] webvaf. Also looked up the properties on the 3.8 GB file and out of 3.8GB, free space is 197.3MB. However, I have no information stored in any file anywhere and can delete anything and everything to free up space. I do not keep any info on the pc. Please advise. Thank you.

---

### Post by snowpine on 2012-10-04
[Recommended minimum]("https://help.ubuntu.com/community/Installation/SystemRequirements/") hard drive space is 5gb. Not sure if Easy Peasy has lower requirement, check their documentation?

Now that the drive has 197.3mb free space, are you able to boot and log in and use the system? Or are you still having problems with the interface/icons? I don't think I'll be able to help you with Easy-Peasy-specific stuff.

If you have no info stored on the EEE then maybe you'll consider replacing Easy Peasy with a more actively-supported lightweight distro like Lubuntu or Xubuntu (supported here) or CrunchBang, SliTaz, or Antix (separate distros with their own support forums). Easy Peasy doesn't seem that actively supported any more from what I can see.

With only 3.8gb storage you are going to have to be very selective with what you install and update I'm afraid. Hard drives are very cheap and large these days (most people have a terabyte or more) so most Linux distros (I named a few exceptions above) don't make the extra effort to conserve every last megabyte. Your EEE also has a 16gb secondary drive, but from what I've read, this drive is much slower than the 4gb and therefore not recommended to install the OS to. Some users put the / (root) partition on the 4gb and the /home partition on the 16gb. My EEE is a little different than yours (with a 160gb conventional spinning HDD) so I can't vouch for this technique personally. Alternately you could install to an 8 or 16gb SD card but again there will be a performance hit.

---

### Post by zyzzyx01 on 2012-10-04
2) things; Firstly tried the first instance to delete all files in tmp .....Shift+Del  but only 3 files there and they were locked. So went into root as suggested and found files mentioned in last post. Under File System, there are 23 files, namely: bin, boot, cdrom, dev, etc, home, isodevice, lib, media, mnt, opt, proc, rofs, root, sbin, selinux, srv, sys, tmp, usr, var, initrd.img, and vmlinuz. 
3 files are locked; cdrom (which my asus does not have), rofs, and vmlinuz.

---

### Post by snowpine on 2012-10-04
> **zyzzyx01 said:**
> 2) things; Firstly tried the first instance to delete all files in tmp .....Shift+Del  but only 3 files there and they were locked. So went into root as suggested and found files mentioned in last post. Under File System, there are 23 files, namely: bin, boot, cdrom, dev, etc, home, isodevice, lib, media, mnt, opt, proc, rofs, root, sbin, selinux, srv, sys, tmp, usr, var, initrd.img, and vmlinuz. 
3 files are locked; cdrom (which my asus does not have), rofs, and vmlinuz.

In Linux it is not normally recommended to go around deleting files outside your /home folder.

If you type 

```
df -h
```

you will get a report of disk usage, if you are running from the Live USB and have your EEE's drive mounted then the right-hand "Mounted on" column will show something like /media/123-456. You mentioned above that you have almost 200mb free, correct?

---

### Post by zyzzyx01 on 2012-10-04
Hi snowpine,
Thanks for the info. Now that you know all the info, which distro is lightweight for this machine and ease of operation? I think the original OS on it was Xandros which was extremely good as ease of operation. Use for this is to web browse, download some films onto sd card  and usb stick instead of hard drive (so Utorrents compatible), open office and of course 'skype'.
Would be much obliged if you could help out.

---

### Post by zyzzyx01 on 2012-10-04
Where do I type  Code:
df -h

Arrow on 1st disk says; /media/6418cefc-aa24-44de-86e4-8275c3a75be9
2nd disk   /media/69c3cbef-d7e8-488e-915a-831671257596

---

### Post by zyzzyx01 on 2012-10-04
1st disk has; 22 items, 197.3 MB free space.
2nd disk has; 16 items, Free space; 8.9GB

---

### Post by snowpine on 2012-10-04
> **zyzzyx01 said:**
> Hi snowpine,
Thanks for the info. Now that you know all the info, which distro is lightweight for this machine and ease of operation? I think the original OS on it was Xandros which was extremely good as ease of operation. Use for this is to web browse, download some films onto sd card  and usb stick instead of hard drive (so Utorrents compatible), open office and of course 'skype'.
Would be much obliged if you could help out.

Tough call. If you want to stay within the Ubuntu family then I recommend you test drive Lubuntu and/or Xubuntu. But even they are [recommending]("https://help.ubuntu.com/community/Installation/SystemRequirements/#Lightweight_GUI_alternative_.28Xubuntu_and_Lubuntu.29") minimum 5gb these days.
I use Fuduntu on my EEE but again [they recommend]("http://fuduntu.sourceforge.net/sysreq.html") 5gb minimum.
I do not own any computers with 4gb HDD's but if I did I might consider [AntiX]("http://antix.mepis.org/index.php?title=Main_Page") or [CrunchBang]("http://crunchbanglinux.org/").

I also recommend you check the Easy Peasy site/forums to see what they say, I just do not have any info about that distro.

---

### Post by fuduntu on 2012-10-04
> **snowpine said:**
> Tough call. If you want to stay within the Ubuntu family then I recommend you test drive Lubuntu and/or Xubuntu. But even they are [recommending]("https://help.ubuntu.com/community/Installation/SystemRequirements/#Lightweight_GUI_alternative_.28Xubuntu_and_Lubuntu.29") minimum 5gb these days.
I use Fuduntu on my EEE but again [they recommend]("http://fuduntu.sourceforge.net/sysreq.html") 5gb minimum.
I do not own any computers with 4gb HDD's but if I did I might consider [AntiX]("http://antix.mepis.org/index.php?title=Main_Page") or [CrunchBang]("http://crunchbanglinux.org/").

I also recommend you check the Easy Peasy site/forums to see what they say, I just do not have any info about that distro.

I spun a variant of Fuduntu 2012.4 for a couple of Eee 900 users last night so they could install on their 4GB Eee PCs.  If there is enough demand for it, we could consider introducing an Eee focused variant of Fuduntu that would be better optimized for the 900.

---

### Post by mikewhatever on 2012-10-04
> **fuduntu said:**
> I spun a variant of Fuduntu 2012.4 for a couple of Eee 900 users last night so they could install on their 4GB Eee PCs.  If there is enough demand for it, we could consider introducing an Eee focused variant of Fuduntu that would be better optimized for the 900.

I think something like Fuduntu might become very interesting for all netbook users. With netbooks falling out of mainstream and out of distributions' focus, and Unity being a bit too heavy, especially for the older Atoms N270 and Poulsbo based machines, the alternative is probably KDE's netbook UI, but then, KDE is even heavier then Unity. I've briefly tested the latest version on a Dell Mini 10, and it seems to have run very well. Fuduntu seems to be as lightwight as Xubuntu, but is more feature reach and visually apealing. It has the stock desktop UI, and perhaps replicating something like the Ubuntu Netbook Edition would be too much to ask, but a netbook oriented respin - something that defaults to Metacity to increase compitibility + no Office to reduce space requirements - would be very interesting. I don't know if we really need yet another eeePC optimized distro though.

---

### Post by snowpine on 2012-10-04
Fuduntu runs great on my EEE 900ha. I think that would be a worthy project Fewt! Not necessarily as an EEE-specific distro, but maybe market it as a "lite" or "base" install of Fuduntu. :)

---

### Post by Plumtreed on 2012-10-05
I was a dedicated user of Fuduntu on my 4GB eeePC701 but constant growth and kernel changes left me behind. When I lost wireless connection on the eee and also on a laptop I locked into Peppermint. Everything works and is very stable on my eeePC......suggest you have look....it fits on the 4GB drive.

---

### Post by fuduntu on 2012-10-05
> **snowpine said:**
> Fuduntu runs great on my EEE 900ha. I think that would be a worthy project Fewt! Not necessarily as an EEE-specific distro, but maybe market it as a "lite" or "base" install of Fuduntu. :)

Just a Fuduntu "lite" sort of install.  I'll mention it to the team.

---

### Post by zyzzyx01 on 2012-10-05
Looked up Peppermint and seems like a lite sys. Could be what I need. Don't want anything too complicated nor sys/memory heavy, although I do not store any info on my asus 900. All I use it for is web browse, emails, Utorrents, skype, and streaming music/spotify. All downloaded info (pics, office etc.etc.) will be stored on memory stick or SD card. Asus 900 has SD card slot, so I use that instead of USB most times. 
Will also check into Fuduntu but would be very happy to install if there is a lite version.

---

### Post by newairly on 2012-10-28
I have Easy Peasy, current version, _not_ 2.0alpha, on my eeepc900. It uses about 3.8GB on the 4GB disk. I have put /home on the 16GB disk. 
I have the same problem about updates in that it says that there is insufficient space to install them so I have only updated a few items such as Firefox, Thunderbird and Skype from those on the distribution.
My main complaint is that the touchpad is very sensitive to tapping and I can find nothing which seems to change that. I have tried a few different touchpad apps. Is there an update to the touchpad driver which might help? It drives me mad when dragging so often invokes an involuntary button press. I now often use an external USB mouse.
The eeepc900 is a great little unit to take traveling because it is so small and light and resistant to crushing in a suitcase.
I recently replaced the keyboard because many keys were becoming unreliable. A really easy thing to do and only $17 for the keyboard!

Phil

---

