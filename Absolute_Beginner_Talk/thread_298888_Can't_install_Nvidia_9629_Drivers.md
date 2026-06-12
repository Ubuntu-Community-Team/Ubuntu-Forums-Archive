---
title: "Can't install Nvidia 9629 Drivers"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2006-11-13
I have a Nvidia 5500 graphics card.  I d/l'd the 9629 drivers.  Nvidia says to type in sh NVIDIA-Linux-x86-1.0-9629-pkg1.run.  When I do this it says it has to be run as root. 

Ok so I type in sudo sh NVIDIA blah blah and it comes back with this

  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

I'm a newbie so all of this is quite overwhelming. I really don't feel comfortable manually editing any file.  Besides to edit the file I need some sort of permissions.

Oh, my HP system has a built in graphic chip. When I disable this in the system setup and choose pci instead of onboard Edgy won't even boot. So I had to go back out, turn the onboard back on so I could get the system to boot.

Also how do I get permissions to delete/edit files?

---

### Post by Bachstelze on 2006-11-13
Just do what it says : exit your X server before installing the driver (Ctrl+Alt+F1 and enjoy the full command-line ;)).

But is there a reason why you don't want to use the one from the Ubuntu repos ?

---

### Post by joshsherman on 2006-11-13
you also need to kill gdm

sudo /etc/init.d/gdm stop

---

### Post by Bachstelze on 2006-11-13
Yep, forgot about that. Though I'm a damned brute and I do *killall gdm* :p

---

### Post by joshsherman on 2006-11-13
I've actually had to do that when it kept saying it was running (after doing the stop).  Was weirdness but I saved a reboot!

-j

---

### Post by po0f on 2006-11-13
jbumgar,

[This guide](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated) is how I got my box to boot with a PCI FX5500.

---

### Post by Suzan on 2006-11-13
Or try envy for this:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

But if you are a newbee I have to warn you... be sure you can reset your X, if something goes wrong!
If you don't know how to do this, don't use the new driver.

Just an advice! ;-)

---

### Post by ReaderRat on 2006-11-13
Susan,
Thank you for the link to the nVIDIA script. If it works, it will help a lot of frustrated posters....ReaderRat

---

### Post by Xer0 Ph0kus on 2006-11-13
I literally just installed my nvidia drivers. I would suggest getting the drivers from the Ubuntu Repos. They are up to date and will give you what you need. 

Go to Synaptic Package Manager and search for nvidia. Since you're using Edgy you'll want to install just nvidia-glx.

After that run ```
sudo nvidia-glx-config enable
```

If you get an error like I did, you might have to manually config your X server which only takes a couple minutes. To do that use this; ```
sudo dpkg-reconfigure xserver-xorg
```

I'm a total n00b too so I feel your pain on the confusion. I read the Commonly Asked questions thoroughly and learned a ton, you should check it out.

To restart your X server press Ctrl+Alt+Backspace. If you see a Nvidia splash screen before the login, you win.

---

### Post by samwyse on 2006-11-14
> **Xer0 Ph0kus said:**
> I literally just installed my nvidia drivers. I would suggest getting the drivers from the Ubuntu Repos. They are up to date and will give you what you need.
The repo driver version is 8776, which is ok unless you need the fixes in 9629.

---

### Post by TorenC on 2006-11-14
> **samwyse said:**
> The repo driver version is 8776, which is ok unless you need the fixes in 9629.
here:
[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

The same guy that does envy has a repo for 9629 drivers. Just follow the instructions and your all set, with no annoying nvidia installer. Worked great for me, I was able to get AIGLX/Beryl running on my Dell D820 beatifully.

---

