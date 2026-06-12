---
title: "[SOLVED] Fn Keys on MBP 4,1 and Ubuntu Intrepid"
date: 2008-12-11
forum: Apple Hardware Users
---

### Post by hoarycripple on 2008-12-11
I was happily using Ubuntu 8.04 with the mactel patches and latest              
pommed for quite some time without any issues.  The keyboard backlight          
was working as expected, as was the LCD backlight and volume keys.  In          
short, all the Fn keys were working as expected.  My setup at that time         
was using a patched 2.6.25 kernel using a fix as noted here:                    
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/207127/comments/26](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/207127/comments/26)    
                                                                                
I now had to install Ubuntu 8.10 (Intrepid) because of a hard drive             
failure and new hardware and have been struggling to get everything             
working again.                                                                  
                                                                                
With the default installation of Ubuntu 8.10, booting into GNOME,               
everything works!  But, I personally don't use GNOME, and rather have           
used svn Enlightenment DR17 windowmanager and Entrance as the login             
manager.  I don't use GNOME at all, but keep everything installed               
because there are so many packages that are dependent on it.                    
                                                                                
Apparently, to get everything working I need to have gnome-power-manager        
and gnome-settings-daemon loaded.  I also need to have the applesmc and         
mbp_nvidia_bl modules loaded.                                                   
                                                                                
Having the modules load at boot is not a big deal, but I would rather           
not have to be tied to gnome-appearance-daemon or gnome-power-manager if        
at all possible.  Therefore, I tried to install pommed (latest).  This          
causes the automatic backlight to work properly, but the Fn keys don't          
do anything at all.  xev gives me keysyms for all the function keys, but        
pommed/gpomme does not recognize it.                                            
                                                                                
Is there any way to have keyboard backlight, LCD backlight, volume and          
eject keys working without having to load gnome-power-manager (controls         
the backlights) or gnome-settings-daemon (controls the volume and               
eject)?                                                                         
                                                                                
Thank you.

---

### Post by _mario_ on 2008-12-11
> **hoarycripple said:**
>                                                     
Is there any way to have keyboard backlight, LCD backlight, volume and eject keys working without having to load gnome-power-manager (controls the backlights) or gnome-settings-daemon (controls the volume and eject)?
besides i see no reason for abandoning GNOME daemons, i believe, your problem is as follows: since you reinstalled Ubuntu, you got a newer Xorg that relies on Hal to recognize all devices (there shouldn't even exist an /etc/X11/Xorg.conf anymore). Pommed uses the kernel's evdev interface to poll the input devices. so does the new Xorg. that's why pommed doesn't receive any events anymore. after switching to a text console pommed works again, doesn't it?

if that's all true, you can revert back to the old behaviour by creating a suitable /etc/X11/Xorg.conf and adding:
```
Section "ServerFlags"
# If this option is disabled, then no devices will be added from HAL events.

    Option      "AutoAddDevices"        "off"

# If this option is disabled, then the devices will be added (and the
# DevicePresenceNotify event sent), but not enabled, thus leaving the
# policy up to the client.

#    Option     "AutoEnableDevices"     "off"

EndSection
```
now pommed should work within X as well.

if there are missing keysyms in xev, you'll have to redefine them. if i'm remembering correctly, at least the volume keys. that's necessary because evdev also emits other keycodes and the newer keymaps have been adapted accordingly.

ciao,
Mario

---

### Post by hoarycripple on 2008-12-11
This worked perfectly.  Thank you.  

Marking as solved.

---

### Post by devnater on 2008-12-15
whew thanks mario.  this is exactly what I've needed for over two weeks - none of the other solutions I found on this forum have worked for me, an 7.10->8.04->8.10 upgradee.

---

