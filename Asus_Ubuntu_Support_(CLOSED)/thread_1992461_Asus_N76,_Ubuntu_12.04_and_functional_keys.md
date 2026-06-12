---
title: "Asus N76, Ubuntu 12.04 and functional keys"
date: 2012-05-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ilian iliev on 2012-05-31
Hi,

I have a new Asus N76VZ laptop and I have several issues but the major for the moment is with the functional keys. I am linux beginner but here is what I've tried already, after reading other forums/thread.
1) Run xev - the fn + fX combinations are not detected
2) Run acpi_listen - when I type i see the output, for most of the combinations I get the same output "PNP0C14:01 000000ff 00000000" some of them(sleep/turn off monitor) are working so I can not see the result.

Any ideas how I can proceed from here?

Thanks in advance.

---

### Post by xomix on 2012-07-20
Hi,
I've got a n76vm and acpi_listen shows nothing for multiple hotkeys (keyboard light, backlight), so I can't figure out what happens when I press these keys...
Moreover the touchpad is not working ok (can't get right button working, grrr) and the subwoofer or LFE outlput is not working neither...

Do you have these problems too? Have you found a solution already?

If you already get codes with acpi_listen, there should be some scripts in /etc/acpi and /etc/acpi/events to handle them. Look at [http://www.howtoforge.com/manage-your-laptop-hotkeys-on-fedora](http://www.howtoforge.com/manage-your-laptop-hotkeys-on-fedora) to get an idea...

Thanks!

---

### Post by ilian iliev on 2012-07-21
Yes, I have the same problems. I found acpi4asus mentioned in several articles but I was not able to install it in 12.04

If you succeed with the install please share how you did it.

---

### Post by KPhoen on 2012-07-21
I configured my touchpad as explained here : [https://wiki.archlinux.org/index.php/Touchpad_Synaptics](https://wiki.archlinux.org/index.php/Touchpad_Synaptics)

I stil have problems with the subwoofer, the hotkeys and the keayboard backlight. I heard that these problems were related to a bug in the kernel module in charge of the acpi for asus, but I don't know if a solution has been found. Even installing the acpi4asus package did not fix the problems.

---

### Post by xomix on 2012-07-24
Hi! Found the info! Now Fn Keys are all working but screen backlight.
You have to install bumblebee to get the hybrid nvidia/intel graphics card working OK. This will update your xorg packages with the x-swat updates.

Then you need to install an assus-wmi DKMS module.

Once done (most) Fn keys work and there is even better support for the touchpad (1,2,3 and 4 finger tap !)

It seems that all these things are included since kernel 3.4.2 and some version of xorg... Ready in quantal alpha...

Useful information from zenbook users, hw must be somehow similar...

Now I want the LFE working, I'm going to search!

Bumblebee: [https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")

Asus-wmi Kernel module: [http://ubuntuforums.org/showthread.php?t=2005756&page=3]("http://ubuntuforums.org/showthread.php?t=2005756&page=3")   (post #30)

---

### Post by Alasiac on 2012-08-06
> **xomix said:**
> Hi! Found the info! Now Fn Keys are all working but screen backlight.
You have to install bumblebee to get the hybrid nvidia/intel graphics card working OK. This will update your xorg packages with the x-swat updates.

Then you need to install an assus-wmi DKMS module.

Once done (most) Fn keys work and there is even better support for the touchpad (1,2,3 and 4 finger tap !)

It seems that all these things are included since kernel 3.4.2 and some version of xorg... Ready in quantal alpha...

Useful information from zenbook users, hw must be somehow similar...

Now I want the LFE working, I'm going to search!

Bumblebee: [https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")

Asus-wmi Kernel module: [http://ubuntuforums.org/showthread.php?t=2005756&page=3]("http://ubuntuforums.org/showthread.php?t=2005756&page=3")   (post #30)

Is your keyboard lighting also working with the fn keys? I kinda did your setup with bumblebee and the asus-wmi module, but aside from the backlight buttons, the keyboard lighting buttons are still not working.

I'm not sure, but I guess with LFE you refer to the subwoofer part? Which is also not yet working on my setup...

---

### Post by broken plastic on 2012-08-29
not sure what ive done, but everything works for me now. i have the aasus_wmi and bumblebee installed.  the keyboard backlighting isnt perfect, as sometimes i have to hit the brightness down button in order for the light to activate.

i started out with ubuntu studio which uses xfce but have also added gnome

---

### Post by JustNoobin on 2012-08-30
I have the N56 and my function keys 2nd key (whatever they're called) don't work either. So for instance if I want to turn up my volume (I press fn and a function key that has a volume icon on it), they won't work. However if I do that with the wireless internet icon and function key, it works.

---

### Post by blinduck on 2012-08-30
Hello,

Do any of you with the N76VZ have problems with the wireless card as well? My wireless drops every couple minutes...

I posted in the Wireless and Networking Forum as well..
[http://ubuntuforums.org/showthread.php?t=2050475](http://ubuntuforums.org/showthread.php?t=2050475)

---

### Post by wb8nbs on 2012-11-30
I have an N56VJ with 12.10 loaded.  The latest kernel update to 3.7.0.4 now has the screen backlight function keys working.  They only work within the top 10% of range though.

---

### Post by sirwhistler on 2012-12-22
Hey,

I have a N76 VZ as well but I can not get Ubuntu or any other linux running. The problem is that the live cd only shows the grub menu, then when I try to boot ubuntu it shows only a black screen. I have tried nomodeset and acpi=off but no success. 

How did you install on your N67? Thanks for you help.

Tom

---

### Post by broken plastic on 2013-01-01
> **sirwhistler said:**
> Hey,

I have a N76 VZ as well but I can not get Ubuntu or any other linux running. The problem is that the live cd only shows the grub menu, then when I try to boot ubuntu it shows only a black screen. I have tried nomodeset and acpi=off but no success. 

How did you install on your N67? Thanks for you help.

Tom

ive succesfully installed ubuntu, ubuntu-studio, and dreamstudio 12.04 and 12.10 usb sticks using unetbootin.  no mods, standard worked.

---

### Post by sirwhistler on 2013-01-03
Dear broken plastic,

thanks for the reply. It is good to know that I can be done using standard ways. I am currently running Mint in a Virtual Box on Win 8 what is quite convenient but not the same as a real install. 

I will have another shot at it soon. Again thanks.

---

### Post by fabian.g on 2013-02-24
Hey guys,

I'm thinking about buying an Ausus N76. Since I use Ubuntu 90% of the time I would like to know if you managed to get get everything running in the end? I would really appreciate if you could share your experience.

Is there anything that's still not working? E.g. Keyboard backlight, Webcam, Instant-On function ...

Thank you very much,
Fabian

---

### Post by p0l0us on 2013-02-27
Maybe this will work for subwoofer: [https://wiki.archlinux.org/index.php/ASUS_N55SF#Audio](https://wiki.archlinux.org/index.php/ASUS_N55SF#Audio)

When I run alsamixer, I see "bass speaker" bar which controls external woofer volume. However, I'm using one year old ubuntu 12.04 instalation moved from my old N55SF notebook and I don't remember all steps I did. So, sombody must verify it ...

---

### Post by thomi_ch on 2013-04-10
Hey all

Just got my ASUS N76VZ with 256GB SSD and 750GB HDD ([http://ch.asus.com/de/Notebooks/Multimedia_Entertainment/N76VZ/#specifications](http://ch.asus.com/de/Notebooks/Multimedia_Entertainment/N76VZ/#specifications)) and searched for solution about just installing Kubuntu 12.10..
How to get it work:
. go into bios: Start Notebook, press ESC until boot menu appears and then choose "Enter Setup"
. disable Secure Boot: Bios / Security / Secure Boot Control (at bottom)
. enable CSM: Bios / Boot / Launch CSM
. switch to IDE instead of AHCI mode: Bios / Advanced / SATA Configuration / SATA Mode Selection

Now boot from LiveUSB Kubuntu 12.10 and choose "Try Ubuntu".
Now you need to rewrite partition table on SSD and HDD with partitionmanager
. start konsole and run: sudo partitionmanager
. right click the SDD 256GB and select "new partition table"
. do same on the 750GB HD

Now you can install kubuntu and choose the 256GB SSD as installation destination... I do so, cause i use the 750GB for all data...

If all above is done.. after 5-10min, kubuntu main installation done ;) YES..

Checkout this Help too, if there are boot problems: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Thats all ;) Yeah!

cheers
thomi

---

### Post by avdheiden on 2013-04-23
I've got a brand new Asus N76VZ running Ubuntu 12.10. Everything worked out of the box, except the (cable) NIC, brightness keys and the subwoofer.

The NIC can be added manually since it's in development and not yet included in the kernel. I tried some suggestions for the subwoofer but can live without it. But the brightness is just annoying. As far as I know, there is no solution at the moment but fortunatelly, there is a work around.

Just install the brightness icon as described here

[http://www.omgubuntu.co.uk/2013/04/brightness-control-ubuntu](http://www.omgubuntu.co.uk/2013/04/brightness-control-ubuntu)

---

### Post by p0l0us on 2013-05-15
Brightness keys are working in 13.04.

---

### Post by Dr. McKay on 2014-01-14
I can buy the N76vb new for a really interesting price (successor is the n750) but would like to know whether the backlight keyboard problems and all the rest has been solved now with Ubuntu 13.10 (I will be running Linux Mint 16 which is based on Ubuntu 13.10) ?

---

### Post by Re4mRpR on 2014-01-18
> **Dr. McKay said:**
> I can buy the N76vb new for a really interesting price (successor is the n750) but would like to know whether the backlight keyboard problems and all the rest has been solved now with Ubuntu 13.10 (I will be running Linux Mint 16 which is based on Ubuntu 13.10) ?

the f3/f4 problems are solved.  my biggest gripe is that it is still a mess to install the nvidia drivers, although i have not tried the newest driver.  im personally using 12.04 lts as my main os because i somehow managed to get the then nvidia driver working and cuda installed so i could use the gpu as a cad renderer.  havent tried to see whether the subwoofer, hdmi, or vga work.  card reader works.

---

