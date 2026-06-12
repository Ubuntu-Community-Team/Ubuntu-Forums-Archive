---
title: "Install Ubuntu-desktop edition on ATI graphics card notebook- need boot parameters"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2008-03-20
Hi I am not unfamiliar with the workings of linux and ubuntu especially, but I am slo not an expert. My notebook has an ati card that installer exspecially live cd, do not like at all. So I download the -alternate version, and use etxt install rather.

I read somewhere that there are boot parameters to bypass the installer to use restricted drivers, and just use VESA at 1024x768 resoultion. Once I can do this and install desktop edition, I can then install the restricted drivers manually and get going.

The reason I ask for the boot parameters to help me install esktop edition of ubuntu is because my local mirror only has desktop edition and no alternate edition.

Can someone help me with the boot parameters?

Thanks in advance

S

---

### Post by bumanie on 2008-03-20
As far as i remember, the alternate cd has a number of lists that appear at various times during install. I have only used the alternate cd once or may be twice, however, my recollection is that when it gets up to the graphics card stage, by default, it offers vesa. To choose something else, you have to scroll through a list. I think it will be self-evident when you get to that point.

---

### Post by forrestcupp on 2008-03-20
If the installer doesn't let you configure your video, just install it, boot to the recovery mode option in grub, and type this:
```
dpkg-reconfigure xserver-xorg
```
You can choose all of the default and simple options, but choose the vesa drivers and 1028x768 in the resolution section.  Then type:
```
exit
```
And it will reboot to the desktop with vesa drivers where you can install the restricted drivers.

---

### Post by shuttleworthwannabe on 2008-03-20
> **bumanie said:**
> As far as i remember, the alternate cd has a number of lists that appear at various times during install. I have only used the alternate cd once or may be twice, however, my recollection is that when it gets up to the graphics card stage, by default, it offers vesa. To choose something else, you have to scroll through a list. I think it will be self-evident when you get to that point.

Sorry, bumanie. I was asking about using the desktop edition to boot from. At the opening boot menu, what boot parameters to use. I vaguely remember something like
vga=791 noacpi nlacpi etc

F6 for additional boot menu...does this offer what graphics setting to choose like VESA etc?

thanks again

---

### Post by bumanie on 2008-03-20
I see what you mean, sorry I misread. Unfortunately I'm no expert on that.

---

### Post by forrestcupp on 2008-03-20
> **shuttleworthwannabe said:**
> Sorry, bumanie. I was asking about using the desktop edition to boot from. At the opening boot menu, what boot parameters to use. I vaguely remember something like
vga=791 noacpi nlacpi etc

F6 for additional boot menu...does this offer what graphics setting to choose like VESA etc?

thanks again

Well, there is xforcevesa.  But when I tried to force vesa with a boot option, it didn't work.  I still ended up with other drivers being used.  

You may just have to install with the alternate CD, and do what I said earlier.

---

### Post by shuttleworthwannabe on 2008-03-20
thnaks guys. As I said, I am comfortable with alternate cd install--I have been doing this all along; current gutsy has a bulletproofX that allows one to visualize the GUI at GDM level....but because the restricted drivers are not properly installed the screen in wavy and shacky;

With the destkop install, one can't even see the GUI windows to proceed with the installation. What you are describing is only after one has installed the entire disc and then rebooted into the installed system.

S

---

