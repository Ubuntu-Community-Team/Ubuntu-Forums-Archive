---
title: "ubuntu and arch dual boot"
date: 2013-04-06
forum: Any Other OS
---

### Post by terry_gardener on 2013-04-06
I currently have ubuntu 12.10 installed with seperate home partition, and i would like to install arch linux. 

would it be best to load the ubuntu livecd and then use gparted to shrink the home partition and make 2 new partitions and then install arch it.

last time i tried to install arch i got confused the text based partition manager and installing and somehow managed to put the home partition in the main partition so it was one drive not seperate home partition. i also couldn't get my lirc remote to work with systemd

---

### Post by mips on 2013-04-06
> **terry_gardener said:**
> 
would it be best to load the ubuntu livecd and then use gparted to shrink the home partition and make 2 new partitions and then install arch it.


Yes, that is what I would do. You might have to create a logical partition as you are only allowed 4 primary partition on a drive using the old dos partitioning scheme.
Besides Arch you could also have a look at Manjaro which is based on Arch and my current OS of choice, they are very close to releasing v0.8.5 and the RC versions can be found here [http://sourceforge.net/projects/manjarodev/files/testbuild/0.8.5-rc2/](http://sourceforge.net/projects/manjarodev/files/testbuild/0.8.5-rc2/)

---

### Post by terry_gardener on 2013-04-06
> **mips said:**
> Yes, that is what I would do. You might have to create a logical partition as you are only allowed 4 primary partition on a drive using the old dos partitioning scheme.
Besides Arch you could also have a look at Manjaro which is based on Arch and my current OS of choice, they are very close to releasing v0.8.5 and the RC versions can be found here [http://sourceforge.net/projects/manjarodev/files/testbuild/0.8.5-rc2/](http://sourceforge.net/projects/manjarodev/files/testbuild/0.8.5-rc2/)

what is the difference between manjaro and arch linux.

i like the arch thing of being a rolling release and having the latest software.

---

### Post by mips on 2013-04-06
> **terry_gardener said:**
> what is the difference between manjaro and arch linux.

i like the arch thing of being a rolling release and having the latest software.

Manjaro is based on Arch but they have their own repos. What they do is take the Arch stable repos and move them to Manjaro testing repos, test them and when satisfied as really stable and no issues move them to Manjaro stable repos. So you will find the Manjaro stable repos to lag behind Arch stable repos. The Manjaro updates are not as frequent & furious as with Arch due to this. The manjaro updates could be like 2 weeks behind Arch (unless it's security related) which in the greater scheme of things is not that much. It's still a rolling release distro. You can pick any of their flavours, xfce, cinnamon, kde, openbox or you can use the netinstall image and build your own system like you would with Arch.

---

### Post by terry_gardener on 2013-04-07
> **mips said:**
>  You can pick any of their flavours, xfce, cinnamon, kde, openbox or you can use the netinstall image and build your own system like you would with Arch.

do they do a gnome version

---

### Post by mips on 2013-04-07
> **terry_gardener said:**
> do they do a gnome version

Not that I know of but there is talk of it. Gnome 3.7 is in the repos if you wanna install it. 3.8 has not made it to stable for arch or manjaro yet as far as i'm aware.

---

### Post by terry_gardener on 2013-04-07
i have installed the majaro net iso and installed gnome (comes with 3.6.2) it installs abit like arch to be honest i just have to try and get the remote control working (lirc)

---

### Post by terry_gardener on 2013-04-07
i have got the lirc remote working

---

### Post by mips on 2013-04-07
> **terry_gardener said:**
> i have installed the majaro net iso and installed gnome (comes with 3.6.2) it installs abit like arch to be honest...

That's because it's basically Arch, the ncurses installer is slightly modified from the Arch one though.

Did you use the 0.8.4 version or 0.8.5 RC?

If you want Gnome 3.8 I think it's available via the unstable repos but I'm not sure about that and could be wrong, either way it should arrive soon.

---

### Post by terry_gardener on 2013-04-07
i installed using the 0.8.4 and then did the standard update.
i will wait for the gnome 3.8 
i even got the lirc remote to work with systemd which is more than last time i tried arch.

---

### Post by malspa on 2013-04-07
Haven't ever installed Arch. I figured the closest I could get to it was Bridge Linux, so I installed that instead -- on a multi-boot set-up that includes Ubuntu 12.04. Fairly easy installation; so far so good after about a month and a half. I went with the Xfce spin -- very nice.

---

### Post by mips on 2013-04-14
0.8.5 is out and Gnome 3.8 should be available in about two weeks time or so if I'm not mistaken unless you wanna enable the unstable repos.
The net & openbox versions have the text installer while the other versions have GUI installers similar to that of Mint.

---

