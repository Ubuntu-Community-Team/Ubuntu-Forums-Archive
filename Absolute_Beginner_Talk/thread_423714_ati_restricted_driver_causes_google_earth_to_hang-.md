---
title: "ati restricted driver causes google earth to hang-up"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by swoop_ubu on 2007-04-26
hello there,

i'm the fresh guy. i installed ubuntu 2 days ago on my notebook.
yesterday i enabled restricted driver ati because google earth
was working (drawing) very slow.
however after enabling ati driver it just hangs up.

any known remedy? tkank you in advance.

cheers
swoop

---

### Post by vanadium on 2007-04-26
You better post full details about your system for such kind of issues. I installed the restricted drivers on a Dell Latitude 800 with an ATI Radeon mobile card, and google earth works perfectly. I followed the instructions on [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) for installing the driver. I had to proceed into the first item of "Troubleshooting" before it would work.

"These two commands might fix your installation, try this, reboot, and run fglrxinfo again:

mkdir -p /usr/X11R6/lib/modules/dri  
ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri"

---

### Post by swoop_ubu on 2007-04-26
right, i'll rehearse.

i installed ubuntu 7.04, automatix2. using automatix i installed
google earth. i'm not sure if it is default option or i selected it in
automatix to install , but anyway i have this menu item
"restricted driver install" or so. i selected to enable ati and rebooted.
gnome started up fine just google earth hangs up. maybe other applications
are affected as well but i didn't try.

i have gateway amd64 notebook. ubuntu 64bit 7.04.
given the fact i'm new to this i always use the menus or GUI based tools.
(i do not have problems with console though)

i hope this is enough information. if not, let me know.

cheers
swoop

---

### Post by vanadium on 2007-04-26
I am a newbee myself, so the only advice I can give is: try the instructions that worked for me. However, i see you have a 64 bit processor, and this probably will imply that you will need 64 bit drivers as well.

---

