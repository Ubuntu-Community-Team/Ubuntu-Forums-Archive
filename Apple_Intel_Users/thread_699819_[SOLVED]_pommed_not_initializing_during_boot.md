---
title: "[SOLVED] pommed not initializing during boot"
date: 2008-02-17
forum: Apple Intel Users
---

### Post by deb on 2008-02-17
sorry, this is my third post regarding pommed...
pommed is working perfectly if i issue "sudo pomed" after logging in. but not during boot up. 
I have pommed in /etc/init.d/ and i have a softlink as  S20pommed in /etc/rcn.d, where n=2,3,4 and 5.
which i think should start the script at boot time. any clues...

---

### Post by david_edmundson on 2008-02-17
when it 's booted up, check if the pommed is actually running
'pgrep pommed' is a good way to do this.

What is probably happening is you also have mouseemu installed. They both fight over the low level keyboard connection, if mouseemu comes up afterwards it takes the input away from Pommed. apt-get remove mouseemu fixes this.

---

### Post by deb on 2008-02-21
David, though I had mouseemu installed, removal of the same didnot change matters...
:~$ pgrep mouseemu
:~$ pgrep pommed
:~$ ls /etc/init.d/ |pommed
:~$ ls /etc/init.d/ |grep pommed
pommed     
:~$ ls /etc/rc5.d/ |grep pommed
S20pommed
_______________________________________
here is my /etc/moules file:-
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
ath_pci
fuse
lp
sbp2
#appletouch should load before usbhid
applesmc
appletouch
usbhid
____________________________________________
and here is my /etc/rc5.d
 ls /etc/rc5.d/ 
K20mouseemu                  S20apport             S24avahi-daemon
README                       S20atop               S24dhcdbd
S05vbesave                   S20hddtemp            S25bluetooth
S10acpid                     S20hotkey-setup       S30gdm
S10sysklogd                  S20makedev            S89anacron
S10xserver-xorg-input-wacom  S20nfs-common         S89atd
S11klogd                     S20nfs-kernel-server  S89cron
S12dbus                      S20nvidia-kernel      S90tempmon.sh
S12hal                       S20pommed             S98usplash
S16ssh                       S20powernowd          S99acpi-support
S17portmap                   S20rsync              S99laptop-mode
S19cupsys                    S20samba              S99rc.local
S20apmd                      S22consolekit         S99rmnologin
___________________________________________

is it any other daemon rather than mouseemu?

---

### Post by cyberdork33 on 2008-02-21
Just for extra help, here is a resource:
[http://www.mactel-linux.org/wiki/Fedora8OnMacBookSantaRosa#Fix_the_function_keys](http://www.mactel-linux.org/wiki/Fedora8OnMacBookSantaRosa#Fix_the_function_keys)

---

### Post by deb on 2008-02-21
cyberdork33, thanks for the link. that is a nice wiki there. but i would stick to ubuntu as the Apple intel forum is awesome here. I am running fedora8 on my desktop- no problems there.:)

---

### Post by cyberdork33 on 2008-02-21
> **deb said:**
> cyberdork33, thanks for the link. that is a nice wiki there. but i would stick to ubuntu as the Apple intel forum is awesome here. I am running fedora8 on my desktop- no problems there.:)I am not saying to use Fedora... the instructions might be helpful. It is still Linux.

---

### Post by deb on 2008-02-22
> **cyberdork33 said:**
> I am not saying to use Fedora... the instructions might be helpful. It is still Linux.

I know it is linux... anyways should have read the script earlier... In the pommed INSTALL file the instruction was to copy the daemon in /usr/bin but in the script it calls pommed from /usr/sbin. So the problem can be solved if i make a soft link of the daemon in /usr/sbin or correct the /etc/init.d/pommed script to  call the daemon from /usr/bin instead of /usr/sbin.

---

