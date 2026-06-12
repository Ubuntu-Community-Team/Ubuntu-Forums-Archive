---
title: "How to download .deb files from repositories"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by manojvekaria on 2006-09-04
How do i download the .deb files from the repositories. I wana install some files on all of my three computers and two laptops.

I don t wana download all the program files again. Can  i download the .deb files of programs such as Wine ntfs -3g and others so i can distibute them from Lan to all the computers?

Please help me!! It would be quite a trick if anyone could do this

---

### Post by ciscosurfer on 2006-09-04
You can issue the following inside a terminal```
sudo aptitude install wine
```To have the latest Wine installed, you need to add this repo to your sources.list file```
## Bleeding edge wine packages (packages, sources)
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main
```Then simply issue the following in a terminal to grab packages you want (for example, after you've modified your sources.list to include the new wine repositories)```
sudo aptitude update && sudo aptitude install wine
```For NTFS-3g, [you should read this page]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g") (you'll need to add the repositories listed their as well to be able to download/install them.  As for other programs, [just make sure your list has the necessary lines enabled]("https://help.ubuntu.com/community/SoftwareManagement").

You can then distribute your files over your LAN anyway you like that works for you ;).

---

### Post by pufuwozu on 2006-09-04
If you look in "/var/cache/apt/archives" you'll see that some .deb files get stored there when you use Synaptic or apt.

If you really just want to download them from a website then you can go [http://packages.ubuntu.com/dapper/]("http://packages.ubuntu.com/dapper/").

---

### Post by Abhi Kalyan on 2006-10-30
Thanks pufuwozu,
just the thing i was looking for, Thank you all once again

---

### Post by Archmage on 2006-10-30
Another idea would be to use the program apt-proxy.

But that isn't easy to set up.

---

