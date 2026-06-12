---
title: "Ubuntu Linux 7.10 Image for Parallels"
date: 2007-11-25
forum: Apple Intel Users
---

### Post by LotzaPhunn on 2007-11-25
I had trouble installing Ubuntu Linux 7.10 (Gutsy Gibbon) through Parallels running on the latest version of Leopard (10.5.1). About 35% into the installation, I kept getting an I/O error for the CD-ROM. Although I found some tips online regarding possible solutions, I was unable to get it to work. So I decided to try installing 7.04 (Feisty Fawn) first and then upgrading to 7.10 -- and it worked!

I figured it would be helpful to post the Parallels Virtual OS config file (.PVS) and the .HDD image online for those attempting to use the same setup.

This installation also addresses an issue regarding the X11 server crashing in Parallels.

The torrent is available on MacNBits (registration required): [http://www.macnbits.com/tracker_details.php?hash=bd77b5dc1e9645580ff6fe031347f31faaca7b62]("http://www.macnbits.com/tracker_details.php?hash=bd77b5dc1e9645580ff6fe031347f31faaca7b62")

---

### Post by sprocket12 on 2008-01-11
The image is unavailable to new registered users.  Anywhere else we might find this image?

---

### Post by LotzaPhunn on 2008-01-11
Alrighyy, I'm re-seeding it. Try again.

---

### Post by cyberdork33 on 2008-01-11
This may be more useful in the virtualization forum.

---

### Post by LotzaPhunn on 2008-01-11
Makes sense. How do you move or mirror a thread?

---

### Post by southpaw32 on 2008-01-16
I'm not able to find the seed.
macnbits says I don't have sufficient privileges.
A little help?

---

### Post by cyberdork33 on 2008-01-16
> **southpaw32 said:**
> I'm not able to find the seed.
macnbits says I don't have sufficient privileges.
A little help?note the registration required. That usually means that you have to be logged into something for it to work.

---

### Post by southpaw32 on 2008-01-16
> **cyberdork33 said:**
> note the registration required. That usually means that you have to be logged into something for it to work.

REALLY? *rolls eyes*
I registered and when I try to go to the link, despite my registration it tells me I don't have "sufficient privileges"

---

### Post by Mua'dib on 2008-01-16
Me either..

---

### Post by cyberdork33 on 2008-01-16
> **southpaw32 said:**
> REALLY? *rolls eyes*
I registered and when I try to go to the link, despite my registration it tells me I don't have "sufficient privileges"
I was trying to imply that the tracker is likely locked down, which seems to be correct if you try looking at the rules on the site. :roll:

---

### Post by jeh_ponce on 2008-01-17
Try this [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) i hope it would help..

---

### Post by jeh_ponce on 2008-01-17
Just a suggestion: Why don't you just try to repeat your installation. May I ask are you logged in as administrator?

---

### Post by cyberdork33 on 2008-01-17
> **jeh_ponce said:**
> Just a suggestion: Why don't you just try to repeat your installation. May I ask are you logged in as administrator?
I think you are confused at what is going on here. This is a parallels image of the installed OS. parallels is a Virtual Machine for Macs, and there is some oddities that make it difficult to install Ubuntu directly.

---

### Post by swhit on 2008-01-17
I had no problems at all installing Ubuntu 7.10 on Parallels Desktop. I downloaded the alternate cd image, rather than the live cd, and performed a text-based install (which isn't as difficult as it sounds --> very easy). Also, I didn't burn the image to cd, just told Parallels where the cd image was located on the computer. Remember to go to setup preferences in Parallels AFTER the install and change your CD-ROM back to the actual drive in order to use your super drive from Ubuntu. Lastly, I read somewhere that specifying more than 512 MB of RAM for your Ubuntu install will mess things up. Not sure if this is true or not, but to be safe, I set the RAM to 512.

This type of install was very quick and easy for me, and ubuntu has worked flawlessly on my mac.

ps. I haven't tried installing parallels tools. I transfer files between linux and mac by turning on the ftp server on my mac and opening a nautilus window that is networked by ftp to the mac. Since it's the same machine, the file transfers are very fast.

---

