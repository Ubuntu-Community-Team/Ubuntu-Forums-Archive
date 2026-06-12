---
title: "Installing extra Programs"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by vinodis on 2006-06-28
Hi,
I have downloaded the Ubuntu DVD ubuntu-6.06-dvd-i386.iso(textonly) from the internet(2.72GB).
Now I hope i will have some extra programs in it to try.

But the problem is that I have no DVD-Burner. So Planning to mount this .ISO image using sudo mount -o loop -t iso9660 /wherever/iso/image/is/image.iso /media/iso/.

Now How can add this mounted directory to Synaptic?

Please help.

Thanks,
Vinod

---

### Post by SkyNet2029 on 2006-06-28
Like this:

```
$ sudo apt-cdrom
```

as its the proper way to add cd-dvd media as a repository.

---

### Post by vinodis on 2006-06-28
Will this command add the mounted .iso image directory to Synaptic?

---

### Post by SkyNet2029 on 2006-06-28
Oops. I misunderstood what you were trying to do. As for adding the mounted .iso file to your sources i dunno. I already tried here by giving the full path to an iso in my sources.list and it did not work. Sorry. I need to read slower or something. ](*,)

Why are you trying to add the .iso to your repos in the first place? Anything on the .iso would be listed in the main/restricted repositories 
when you do an apt-get update as long as those are enabled in your sources.list

---

### Post by vinodis on 2006-06-28
I downloaded the DVD at office. Now I will take it home on my external usb harddrive to copy to my home Ubuntu PC. I have no internet connection at home :(

---

### Post by bikeboy on 2006-06-28
I came across this the other day [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)
In there it says that to add an iso to your sources.list you do the following:
Mount the ISO to /cdrom:```
sudo mount -t iso9660 ubuntu-6.06-alternative-i386.iso /cdrom -o -loop
```Using the full path and proper name for the ISO image
Add the cdrom image to apt:
```
sudo apt-cdrom -m add
```

---

### Post by SkyNet2029 on 2006-06-28
Yeah , I just came across same thing at this page for debian
[http://www.debian.org/releases/woody/i386/release-notes/ch-upgrading.en.html]("http://www.debian.org/releases/woody/i386/release-notes/ch-upgrading.en.html")

it works here so I guess you have two ways.

---

### Post by vinodis on 2006-06-28
Thank you BikeBoy and Skynet. I hope this would succeed in my case too. :)

---

