---
title: "Awesome News!!!!!!  Confirmed 3D Acceleration in 2.6.20 Kernel."
date: 2007-03-26
forum: Apple Intel Users
---

### Post by Gen2ly on 2007-03-26
Maybe everybody knows this but I just compiled the 2.6.20 kernel and now it runs.  I'm stoked!  I put the config in the Gentoo Guide for Macbook.

[MacBook Configuration Files]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files#Kernel_.config")

Now I think Ill try some VDrift!

---

### Post by oskarloko on 2007-03-26
What macbook tye do you have ?

and more important

How about touchpad ?

( as other users says there isn't working ok  )




   Thks !!

---

### Post by Gen2ly on 2007-03-26
I stole everything from the Debian Wiki.
> 
If you want the touchpad being usable with synaptics add these lines to a file in /etc/modprobe.d/

install usbhid /sbin/modprobe appletouch; /sbin/modprobe --ignore-install usbhid $CMDLINE_OPTS

Then add  appletouch  to /etc/initramfs-tools/modules and then don't forget to run  update-initramfs  

Then install gsynaptics gotit?  Worked for me until I did my kernel build.

---

### Post by Azathoth_ on 2007-03-26
> **Dirk.R.Gently said:**
> I stole everything from the Debian Wiki.


Then install gsynaptics gotit?  Worked for me until I did my kernel build.

I did not understand it. Can you give me the link of this debian wiki? Thanks

---

### Post by Gen2ly on 2007-03-26
Sure, no problem.  Really isn't more detail there though.

[Debian Wiki#MacBook]("http://wiki.debian.org/MacBook")

---

### Post by russellc on 2007-03-27
I'm using the 2.6.18.6 kernel here right now. 3D acceleration is fine using the ATI proprietary (fglrx) drivers. Sound works fine, as does my touchpad (with Synaptics driver) so I don't see what improvements are to be offered by the 2.6.20 kernel. Do enlighten me :D

I'm saying this because I could not get it to boot. It stops at a step after loading the Apple USB HID's (keyboard, etc) for some reason. I'm using a Macbook Pro. If anyone can help me out with this, confirm that this is fixed, or tell me that it's just me (and pass me their kernel config) then that would be great :p

---

### Post by Azathoth_ on 2007-03-27
> **Dirk.R.Gently said:**
> Sure, no problem.  Really isn't more detail there though.

[Debian Wiki#MacBook]("http://wiki.debian.org/MacBook")

Thanks, i will check it now

---

### Post by oskarloko on 2007-03-28
(If i'm wrong, please tell me )

Well, I ve seen a lot of info on Gentoo wiki

[http://gentoo-wiki.com/Macbook]("http://gentoo-wiki.com/Macbook")

The config files seems to be done to a MacBook Core2Duo ( not pro )

[http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files")

for a 2.6.20 kernel ( I don't know if it fit to any 2.6.20.*  kernel version )
with Mactel patches.

Did you configure your GCC with the options on the wiki ? 
( I don't renember just know how can it be done on Ubuntu... )

---

### Post by Gen2ly on 2007-03-28
> **oskarloko said:**
> (If i'm wrong, please tell me )

Well, I ve seen a lot of info on Gentoo wiki

[http://gentoo-wiki.com/Macbook]("http://gentoo-wiki.com/Macbook")

The config files seems to be done to a MacBook Core2Duo ( not pro )

It is

> [http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files")

for a 2.6.20 kernel ( I don't know if it fit to any 2.6.20.*  kernel version )

run 
```
make old.config 
```

before applying any config to the kernel and it will be just fine. 

> ... with Mactel patches.

Won't be a big deal.  The wiki has info on using subversion to apply kernel patches.  Though you may want to see if subversion runs on Ubuntu first.
> Did you configure your GCC with the options on the wiki ? 
( I don't renember just know how can it be done on Ubuntu... )

Actually thats my make.conf and is only necessary if you use gentoo.  Ubuntu uses pre-compiled applications while gentoo uses gcc to make them from scratch.

---

### Post by oskarloko on 2007-03-28
I confused a gcc 'config' file with apt-build.conf file......

---

### Post by corefile on 2007-03-29
as was posted earlier, the gcc stuff only applies to gentoo as they compile everything from scratch, on Ubuntu its .debs

---

### Post by Gen2ly on 2007-03-29
I just recently mustered enough gal to use the mactel patches on the kernel, and now I'm able to use gsynaptics again and got my touchpad to turn off!  It was not tough at all.  I used subversion, the 2.6.20.4 kernel, and mactel-patches 2.6.20.  One patch "0003-applesmc_joydev.patch" wouldn't apply properly.  I just rm'd it.

---

### Post by oskarloko on 2007-04-01
Well, two questions 

Onto kernel thread, [http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel]("http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel") there's a great guide to compile on your own.

Should the kernel patch applied (after/before) the mactel patches or not ?
( points 4 and 5)

Onto point 6, let's apply the kernel config on [gentoo wiki]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files"))

Can some lines on make.conf files applied to Ubuntu/Debian ?

I think writing these on */etc/enviorement*
```

[ [ /etc/environment ] ]
CHOST="i686-pc-linux-gnu"
CFLAGS="-O2 -march=nocona -fomit-frame-pointer -pipe"
CXXFLAGS="${CFLAGS}"
MAKEOPTS="-j3"
LDFLAGS="-Wl,-O1"

```

. . .or not ?

(seeking for apt-build.conf info... )

---

### Post by Gen2ly on 2007-04-01
> **oskarloko said:**
> Well, two questions 

Onto kernel thread, [http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel]("http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel") there's a great guide to compile on your own.

Yes thats the one I used.  I like it allot.  xXx 0wn3d xXx knows what he's talking about.  Follow that guide, after you have downloaded the kernel, unpacked it, and added the symbolic link (ln -s)  Apply the patches:
> Should the kernel patch applied (after/before) the mactel patches or not ?
( points 4 and 5)

The mactel patches are kernel patches and they're pretty simple to add to the kernel.  I'm not using Ubuntu at the moment i think its this:
```
apt-get install subversion
cd /usr/src
svn co https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-(version) mactel-patches-(version)
cd mactel-patches-(version)
./apply /usr/src/linux
```

> Onto point 6, let's apply the kernel config on [gentoo wiki]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files"))

Can some lines on make.conf files applied to Ubuntu/Debian ?

I think writing these on */etc/enviorement*
```

[ [ /etc/environment ] ]
CHOST="i686-pc-linux-gnu"
CFLAGS="-O2 -march=nocona -fomit-frame-pointer -pipe"
CXXFLAGS="${CFLAGS}"
MAKEOPTS="-j3"
LDFLAGS="-Wl,-O1"

```

. . .or not ?

(seeking for apt-build.conf info... )

NOT.  Thats for compiling in gentoo, it won't help at all in Ubuntu.  If you have a MacBook, MacBook Pro (you'll have to add ATI driver) , use the [Kernel .config]("http://www.archive.org/download/ToddPartridgeMacBookKernelConfigurationFilefor2.6.20/config2.6.20macbookcore2duo")

```
cd /usr/src/linux
su
cp /home/user/Desktop/config-2.6.20-macbook-core2duo .config
make oldconfig
make menuconfig
make-kpkg -initrd kernel_image kernel_headers modules_image
```

this will make a deb, install it
```

sudo dpkg -i (deb-name)
```

Hope that helps.

---

### Post by oskarloko on 2007-04-02
Ok, I'll try compiling it adding kernel pach *(patch-2.6.20.4.bz2) *and then the mactel patches on snv

Let's see how it works onto Edgy before trying Feisty ( but I think Feisty will be better on hardware detection and use... )

Thanks !!

---

### Post by oskarloko on 2007-04-19
Well, here I am 

I've recompiled and build a new kernel  2.6.20 with mactel  patches 2.6.20 ( I think they are the correct one to these kernel version )

I've not used the  patch-2.6.20.7.bz2 nor the last kernel  2.6.20.7 from kernel.org 
I'll try  2.6.20.7   ¿ anybody has been succesfull / failture ?

It goes ok, faster and cleaner.

Happy now \\:D/ 


I'm on Egdy now,,, but just to use Fesity.

---

### Post by oskarloko on 2007-04-28
Well, 've installed Feisty and recompiled kernel as above, on MacBook C2Duo

I used 2.6.20.7 kernel version with mactel patches 2.6.20

Three error messages are shown at boot time:

```

intelfb: Video mode must be programmed at boot time
ata-piix 0000:00:1F invalid map value 0
i8042.c not controller found

```

Althougth I keep searching, any guess will be wellcome

Ah! My grub is like
```

title		Ubuntu, kernel 2.6.20.7oba20070428mactel-mactelpatches-macbook-core2duo
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20.7oba20070428mactel-mactelpatches-macbook-core2duo root=/dev/sda3 ro quiet splash video=vesafb:mtrr:3,ywrap,1280x800-24@60 lpj=8000000
initrd		/boot/initrd.img-2.6.20.7oba20070428mactel-mactelpatches-macbook-core2duo
quiet
savedefault

```

I used root=UUID=eba4bc7f-ce73-4381-8bc3-790f9b9290bc on boot, but it doesn't find partition..

---

### Post by Gen2ly on 2007-04-29
Strange, I had the same exact problem.   Hmmm.  This has me befuddled as i had compiled the same kernel in another linux and didn't have a problem.

```
intelfb: Video mode must be programmed at boot time
ata-piix 0000:00:1F invalid map value 0
i8042.c not controller found
```

I've never seen this before.

**[COLOR="Red"]NOTE: Do not use "grub-install"**
as it completely bjorked my partition table.  If you have to update grub do it manually instead:[/COLOR]

```
grub
find /boot/grub/stage1
root (printed value from above) likely (hd0,2)
setup (hd0,2)
```

Dam, I though this was fixed.

---

