---
title: "Grub fails to start"
date: 2011-11-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by r_avital on 2011-11-14
[FONT=Tahoma][SIZE=2]Hey all, here's a thorny problem, and it's never happened to me except with this brand new ASUS motherboard:

Motherboard:
ASUS Sabertooth X58 LGA 1366 Intel X58 SATA 6Gb/s USB 3.0 ATX Intel Motherboard[/SIZE][/FONT][SIZE=2][FONT=Tahoma]

Lucid 10.04 fresh install.
Memory: 12Gb

Installs correctly, no issues (yet).  Installed update from update-manager to 2.6.32-35-generic.

At this point, if I restart, and hold down the left Shift key, Grub 2 should start, correct?

Well, I hold down the left Shift key as soon as the Bios screen comes up (which has choices like F8 for boot sequence, Del for Setup etc), and when the screen blanks, I get:

Grub starting

Which disappears immediately, then X launches and starts ubuntu.  I never get the Grub screen.

Any assistance?  Any ideas?

I've read somewhere that sometimes holding the Esc key also works, but it did not in my case.

When the Bios screen comes up, if I press F8 for instance, I do get the boot menu, so I know the keyboard is recognized.  It's just that Grub won't start, even though the message "Starting Grub" shows up.

I need to be able to start grub to troubleshoot issues between X and the nvidia driver.  My only recourse is to start the system from the Ubuntu DVD and go to a root console from there, which will not give me the root privileges to edit the xorg.conf file on the hard drive.

Please help.  Can't run ubuntu if I can't boot into Grub.

Thanks in advance.
[/FONT][/SIZE]

---

### Post by raja.genupula on 2011-11-17
i think forum staff will take care of the 2nd post . 
Hi op , look at my signature for grub recovery method and you can get the grub from there . 
after installing grub , install grub customizer(in my signature) also , from this you can easily manage your grub settings.

---

### Post by r_avital on 2011-11-17
Many thanks, Raja,

It turns out I had to pick the right moment to hit left-shift in order to get GRUB - it's hit and miss, but I can get it.

Much more interesting, I installed the grub-customizer you mentioned, and ran it as root (sudo grub-customizer) - got a segmentation fault error.  Output below.  If you can think of any solution for this, that would be great.  Thanks again.

```
Xlib:  extension "RANDR" missing on display ":0.0".
 *** initializing (w/o specified bootloader type)…
   * reading partition info…
   * Loading Framebuffer resolutions (background process)
   * Finding out if this is a live CD
     [running on an installed system]
     [checking the burg-mkconfig command… ]
     [found at: ]
     [checking the grub-mkconfig command… ]
     [found at: /usr/sbin/grub-mkconfig]
     [checking the update-grub command… ]
     [found at: /usr/sbin/update-grub]
     [checking the grub-install command… ]
     [found at: /usr/sbin/grub-install]
 *** initializing (w/ specified bootloader type)…
     [checking the grub-mkconfig command… ]
     [found at: /usr/sbin/grub-mkconfig]
     [checking the update-grub command… ]
     [found at: /usr/sbin/update-grub]
     [checking the grub-install command… ]
     [found at: /usr/sbin/grub-install]
   * Checking if the config directory is clean
 *** loading configuration
 *** loading - preserveConfig: no
   * unsetting saved config
 *** loading settings
 *** loading grub list
   * loading scripts…
   * loading proxies…
   * creating proxifiedScript links & chmodding other files…
   * running grub-mkconfig
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
Segmentation fault

```

---

### Post by raja.genupula on 2011-11-17
i am honestly dont have idea about this issue but have you tried to launch it from normally , i mean not from terminal.you can launch this application as GUI .from preference tab you can change the boot time to 10sec.

or do this 

```
sudo dpkg-reconfigure grub-pc
```

then install the grub to Ubuntu sda and then do 



then at the grub.cfg file in /boot/grub location , set the time out to 10sec. it will fix the problem.

```
sudo update-grub
```

all the best.

---

