---
title: "Failed to start X server Please help me );"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Vamp381 on 2007-11-12
I can`t enter my ubuntu i tried :confused: i always goth error failed to start x server (your graphica interuptedl)it is likely that is not set correctly,,,,,,,,,,,
and that blue screen of errors.
I tried:
```

sudo cp /etc/x11/xorg.conf (as root) don`t work

nano /etc/x11/xorg.con didn`t help

sudo dpkd-reconfigure xserver-xorg (i entered all valid informations and didn`t help) )-;

apt-get --reinstall install xserver-xorg (still nothing)

sudo /etc/init.d/gdm.stup (nothing)



```

Please i don`t know what to do and enter anymore...

---

### Post by mikewhatever on 2007-11-12
How about **sudo /etc/init.d/gdm start**.

---

### Post by Vamp381 on 2007-11-12
When i entered that error again appeared.There is a error in nvidia kernel. I tried to install new version on older  ;\

---

### Post by Vamp381 on 2007-11-12
Anyone ?? :(

---

### Post by KentS on 2007-11-12
Do you have a working backup of your xorg.conf?
If so, can you do
```
cp /etc/X11/xorg.conf_WORKINGBACKUP /etc/X11/xorg.conf
```

Can you uninstall your new nvidia driver, and install the original one?

Maybe replacing nvidia with vesa in xorg.conf will get your x up and running so it will be easier to install the proper driver?

---

### Post by trak87 on 2007-11-12
The other day I completely renamed xorg.conf to something else and rebooted my system without xorg.conf AT ALL. I was able to start the gui server. I looked in /etc/X11 and saw that Gutsy recreated a file for me.

I'm sticking with the nv driver for now since I've had nothing but problems with the nvidia driver. It works fine now for the most part -- I don't get the speed of the full nvidia driver -- but at least it works. I'm not interested in eye candy anyway. Proprietary software is a real problem here.

---

### Post by Vamp381 on 2007-11-12
I will trie that command. I i deleted xorg and then i maked another (i was thinking that will solve my problem ^,^) but still problem.

---

### Post by KentS on 2007-11-12
If you try 
```
cp /etc/X11/xorg.conf_WORKINGBACKUP /etc/X11/xorg.conf
```
be aware that you should not use _WORKINGBACKUP, but replace it with the name of the working backup file.

---

### Post by Vamp381 on 2007-11-13
I didn`t solve problem yet,and i get error nvidia kernel module has version mismatch with nvidia xorg module,My nvidia kernel is 1.0-9631 and installed version is 1.9-9339.(Befire this i tried to install new drivers via synaptic) how can i fix this ?

---

### Post by Vamp381 on 2007-11-13
Can someone help me...............................?

---

### Post by KentS on 2007-11-13
A suggestion, don't know if it will work, though. But I guess it can't get any worse.

Do you remember the name of the package you installed? Uninstall it:
```
sudo apt-get remove [insert name of package]
```

Download the correct driver from nvidia homepage:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9631/NVIDIA-Linux-x86-1.0-9631-pkg1.run
```

Now, install:
```
sh NVIDIA-Linux-x86-1.0-9631-pkg1.run
```
May have to do this one as root (sudo).

---

### Post by Vamp381 on 2007-11-13
Didn`t help i forget the name of package ;\.But i downloaded drivers and when i try to install i get unable to load module nvidia.ko.
Can i somehow remove this unvanted version of drivers ? (or nvidia kernel and install new)

---

### Post by KentS on 2007-11-13
First do
```
less /var/lib/dpkg/status | grep nvidia
```

Do you get a line saying something like 
> Package: ["packagename"]
That is probably the package you want to remove

Do 
```
apt-cache showpkg "packagename"
```
and check that it actually is the version you want to remove.

If it is, do
```
sudo apt-get remove "packagename"
```

If that doesn't give any usable output, try
```
apt-cache pkgnames | grep nvidia
```
Then do
```
apt-cache showpkg [something]
```
for the packages that shows up from the previous command. Find out which one you have installed, and 
```
sudo at-get remove [something]
```
the unwanted package.

---

### Post by Vamp381 on 2007-11-13
Now i get error Failed to load module "nvidia" no drivers available.

When i try to install drivers 1.0-9746 i get

ERROR: Unable to load the kernel module 'nvidia.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.

---

### Post by bapoumba on 2007-11-13
Please read my sig, last line.

---

### Post by Vamp381 on 2007-11-13
I don`t wont to uninstall system.
Is there a way to reinstall ubuntu but not to delete my files (movies,games ) ;\

---

### Post by KentS on 2007-11-14
> **bapoumba said:**
> Please read my sig, last line.

What do you mean? I just told him to remove a driver that isn't working with his hw. I did more or less the same myself a while back. I installed the wrong driver from synaptic, crashed my x, booted up again using the nv-driver, uninstalled the wrong driver and installed the right one from nvidia using synaptic. After having set my resolution, everything works perfectly.

Besides, can't he 
```
sudo apt-get install nvidia-kernel-1.0[. or -]9746
```
and then install the driver from nvidia?

---

### Post by KentS on 2007-11-14
And shouldn't 
```
sudo apt-get install [whatever package he just removed]
```
get him back into the exact same mess that's the reason he got here in the first place?

---

### Post by bapoumba on 2007-11-14
> **KentS said:**
> What do you mean? I just told him to remove a driver that isn't working with his hw.
There was a spammer last night, posting dangerous commands that could wipe the entire system. We were deleting the posts and banning as fast as we could, and posting warnings in threads such as this one . This was not at all regarding your own posts, thanks for your help ;)

---

### Post by Vamp381 on 2007-11-14
I entered that and now i get
E: Couldn`t find package nvidia-kernel
;-/

---

### Post by mark. on 2007-11-14
dont worry, i have this same exactt problem :/, but it has to do with resolutions

---

### Post by KentS on 2007-11-14
> **Vamp381 said:**
> I entered that and now i get
E: Couldn`t find package nvidia-kernel
;-/

Sorry, I wrote the wrong kernel name.
Try
```
sudo apt-get install nvidia-kernel-1.0.9631
```
If that doesn't work, try
```
sudo apt-get install nvidia-kernel-1.0-9631
```

---

### Post by KentS on 2007-11-14
Before you do anything else, try
```
sudo apt-get install nvidia-glx
```

---

### Post by Vamp381 on 2007-11-14
When i entered
```
Sudo apt-get install nvidia-kernel1.0.9631
```
It`s show me the list of kernel and there was only versions like 2.6.20-15,2.6.20-15
I tried then
```
sudo apt-get install nvidia-glx nvidia-kernel common
```
After dowload version 2.6.20-15 installed and didn`t work ;\.

---

### Post by KentS on 2007-11-14
> **Vamp381 said:**
> I tried then
```
sudo apt-get install nvidia-glx nvidia-kernel common
```
After dowload version 2.6.20-15 installed and didn`t work ;\.

Exactly what happened? What doesn't work? Did you try 
```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

If it doesn't work:
```
dpkg --get-selections > ubuntu-files
less ubuntu-files
```

Check in the list that you have something like the following installed:
linux-restricted-modules
nvidia-glx
nvidia-kernel

If something is missing, what is missing? How many versions of nvidia-glx are installed?

Does
```
aptitude show nvidia-glx
```
tell you that it's installed?

Does
```
aptitude show linux-restricted-modules-SOMETHING
aptitude show nvidia-kernel-SOMETHINGELSE
```
tell you that they are installed? (You need to check with the file ubuntu-files to find out what you should replace SOMETHING and SOMETHINGELSE with.

What graphics card do you use?

Do you have xserver-xorg-video-nv installed? If this shows up on the list of installed packages (ubuntu-files), you can try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Choose nv (NOT nvidia)
Choose some standard (not widescreen or similar) resolution.
```
startx
```
This should get you a GUI.

---

### Post by ruibernardo on 2007-11-14
If "startx" doesn't work, try
```
sudo /etc/init.d/gdm restart
```

---

### Post by Vamp381 on 2007-11-15
Hey thanks for replyes i will try later. (must go) 
Card is geforce4 mx460

---

### Post by Vamp381 on 2007-11-15
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Helped me (-; when choosed nv instead nvidia.
Now i don`t have drivers,how to install them on proper way.
Btw thanks KentS :guitar:

---

### Post by ruibernardo on 2007-11-15
They should be installed. If they aren't, try 
```
sudo apt-get install nvidia-glx
```(more stable, but some newer graphic cards don't like it) or 
```
sudo apt-get install nvidia-glx-new
```(for newest drivers).

Then you should enable the nvidia driver in the menu System > Administration > Restricted controlers manager.

---

### Post by Vamp381 on 2007-11-15
I entered that now i goth message when i want to enter restricted drivers manager:  Your hardware does not need any restricted drivers.

---

### Post by tibellus on 2007-11-15
This thing happens to many old Nvidia video cards. I have a "grandma", and I also get the same message, I think you shouldn't worry about that. My computer works just fine, without any restricted drivers.

---

### Post by Vamp381 on 2007-11-15
When i don`t haved this problem with x server,restricted manager worked.
Now i can`t play any games with wine or native,,,(counter strike i can`t t0)

---

### Post by KentS on 2007-11-15
You now have a (more or less) working GUI? Do
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

I checked this Howto:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Then I checked your graphics card in this list:
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

Apparently we should have checked your graphics card earlier. It seems your card is not supported by nvidia-glx or nvidia-glx-new. You need to install nvidia-glx-legacy. You can either install it using Synaptic, or by doing
```
sudo apt-get install nvidia-glx-legacy
```

You might want to check that you are using the nv-driver (and make a backup of your xorg.conf using the nv-driver if you haven't already done it). Then uninstall nvidia-glx (IF IT IS NOT WORKING) before you install the correct driver. You should also check the above mentioned links, just in case I misread something.

---

### Post by KentS on 2007-11-15
When you have installed the driver:
```
sudo nvidia-xconfig
```
and restart x.

You may also want to look on the first link I mentioned in my previous post, under "Common Problems".

---

### Post by Vamp381 on 2007-11-15
I was uninstalled all nvidia drivers that don`t worked,and then i downloaded envy
and i think he downloaded right drivers.Now Open gl works. 
Now when i entered synatpic Package manager there is one broken package nvidia-glx.
And i still can`t enter restricted drivers manager i get:

You need to install the package linux-restricted-modules-2.6.20-16 generic for this program to work.

Is this necessary to install or to leave it (-;

---

### Post by KentS on 2007-11-15
```
uname -r
```

If the output is 2.6.20-16-something, then you should install it, yes.

---

### Post by Vamp381 on 2007-11-15
I downloaded version that came out from that command and now works (-; Thanks KentS and all .

---

