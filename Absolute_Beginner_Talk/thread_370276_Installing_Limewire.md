---
title: "Installing Limewire"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by wbusch on 2007-02-25
I am trying to install limewire.  I am new at the Linux.  I found a site explaining how to use the terminal and I type in :  sudo alien LimewireLinux.rpm and it says file not found.  I have downloaded the RPM twice to the desk top.  Any ideas?

Wally

---

### Post by Maestro23 on 2007-02-25
> **wbusch said:**
> I am trying to install limewire.  I am new at the Linux.  I found a site explaining how to use the terminal and I type in :  sudo alien LimewireLinux.rpm and it says file not found.  I have downloaded the RPM twice to the desk top.  Any ideas?

Wally

You have to install the alien command first, and then be in the directory to which you download the .rpm.

Read section on Manual Installation of an .rpm

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Ex:

> cd Desktop

ls (should see your .rpm)

then

sudo alien -i package name.rpm


Good luck.

---

### Post by wbusch on 2007-02-25
I installed alien.  I type  sudo aptitude install limewirelinux.rpm and I either get a no destination error or sudo alien LimewireLinux.rpm and it says limewirelinux.rpm not found.

---

### Post by picpak on 2007-02-25
Is there anything wrong with Frostwire?

```
wget http://www.frostwire.com/download.php?file=http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.5-1.i586.deb
sudo dpkg -i frostwire-4.13.1.5-1.i586.deb
```

---

### Post by Maestro23 on 2007-02-25
> **wbusch said:**
> I installed alien.  I type  sudo aptitude install limewirelinux.rpm and I either get a no destination error or sudo alien LimewireLinux.rpm and it says limewirelinux.rpm not found.

You don't use apt-get/aptitude to install a .rpm package.  Look at my first post and the link I gave you.

Are you in the directory that you downloaded the .rpm?  Your desktop right? 
> 
cd /home/username/Desktop

ls 


If your .rpm is on your Desktop, then your should see it when you run the "ls" command.  

After that, run the sudo alien.... command.

---

### Post by wbusch on 2007-02-25
this is what I get.

wally@wally-laptop:~$ cd/home/wally/desktop
bash: cd/home/wally/desktop: No such file or directory

---

### Post by picpak on 2007-02-25
Put a space between cd and /home/wally/Desktop.

oh -- and make sure "desktop" is capitalized!

---

### Post by Maestro23 on 2007-02-25
> **picpak said:**
> Put a space between cd and /home/wally/Desktop.

oh -- and make sure "desktop" is capitalized!

Yes, and in linux things are CASE-SENSITIVE (Desktop not desktop).:)

---

### Post by xpod on 2007-02-25
> Is there anything wrong with Frostwire?

I was thinking the same myself.Probably easier than rpm`s for a newcomer too me thinks?
It`s basically just a free version of limewire wbusch and is just as good as the pro version of limewire and no annoying add`s telling you to upgrade either

Much easier to install too either as previously mentioned, or by visiting their site and clicking the relevant download link.....Turbo connection in no time without all that rpm fiddling.:) 
[http://www.frostwire.com/](http://www.frostwire.com/)

I use gtk-gnutella and azureus now for such stuff and theres a few others too but frostwire was one of the better ones.

---

### Post by wbusch on 2007-02-25
I took your advice and downloaded frostwire.  I now have the icon under my internet application but when I click on it I get nothing.

Wally

Thanks for all your help

---

### Post by picpak on 2007-02-25
Do you have Java installed?

Go to a terminal and type

```
frostwire
```

, what does it say?

---

### Post by vitalstatistix on 2007-03-07
Yeah……..installed limewire finally. OK here’s the low down
 1) Go to Synaptic and install Sun Java 5.0 Runtime if you already haven’t done that (you might install the plugins too as they’ll come in handy while browsing).
 2) Download the latest version of limewire in “.rpm” format into your home folder.
 3) OK fire up a terminal and run “sudo alien -c LimeWireLinux.rpm”. In case you dont have alien just run “sudo apt-get install alien”.
 4)  Now run “sudo dpkg-reconfigure dash” and select “No” when prompted to install dash.
 5) Great we’re almost done……..just go to your home folder, find a “.deb” file containing limewire like “limewire-free_4.12.11-1_i386.deb” and just double click> Install Package.
 6) Go to Applications>Internet>LimeWire………….and voila you’ve got it running!

---

