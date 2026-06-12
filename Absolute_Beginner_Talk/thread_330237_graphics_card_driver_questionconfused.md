---
title: "graphics card driver question:confused:"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by MkfIbK7a on 2007-01-02
i have an elsa tnt2 vanta graphics card and was wondering whether i need a driver for it,
 right now it is running on the generic nv driver should it be set to something else? do i have to get a new driver? plz help:confused:

---

### Post by MkfIbK7a on 2007-01-02
.bump.

---

### Post by MkfIbK7a on 2007-01-02
i need help!:confused: :confused: :confused: :confused: :confused: :confused: ](*,) ](*,)

---

### Post by WMC on 2007-01-03
I've just done my very first Ubuntu installation, and the PC happened to have a TNT2 video card.  I got it going like this:

[LIST]
[*]download the **_[COLOR="Blue"][nvidia-glx-legacy drivers]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.15%2Fnvidia-glx-legacy_1.0.7174%2B2.6.15.12-1_i386.deb&md5sum=055b0320696d8b528ba718bd7b964e42&arch=i386&type=security")[/COLOR]_** to the desktop (the link is for the Dapper / 6.06 drivers - no idea if you need something different for Edgy / 6.10)
[*]doubleclick the .deb package and install the drivers
[*]open a terminal, type [FONT="Courier New"]**sudo nano /etc/X11/xorg.conf**[/FONT], press enter, then enter your password
[*]scroll down to the 'Device' section (it's a fair way down the page) and change the Driver line from 'nv' to 'nvidia'
[*]Press Ctrl+x
[*]Press Enter to keep the same filename
[*]Press 'y' to save
[*]Exit the terminal
[*]Log out, then log in
[/LIST]

If you get dumped to a terminal with an error upon restarting, just type 'sudo nano /etc/X11/xorg.conf' again, change the 'nvidia' back to 'nv', Ctrl+x to save, enter, y, then restart.

---

### Post by WMC on 2007-01-03
Actually, I forgot a step:  after you've installed the driver by clicking on the .deb file, you'll get a message about a command to type at the terminal to actiavte the driver (I think it's 'sudo nvidia-xconfig').  Try that before editing xorg.conf - I only had to do that because I'd already been mucking about with the file, and the setup script could tell I'd changed it.

---

### Post by MkfIbK7a on 2007-01-03
im doind what you said im just wondering whether this segnifgantly help your video or not

---

### Post by Sammi on 2007-01-03
You should be able to find the nvidia legacy drivers in Synaptis. Don't know if you need to enable extra repositories though.

Instructions on enabling extra repositories can be found in the unofficial Ubuntu guide: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Addtional_Software](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Addtional_Software)

---

### Post by MkfIbK7a on 2007-01-03
no its alright ive been using ubuntu for over a year but anyway yes i got it in synaptic and it really did speed up my video

---

### Post by MkfIbK7a on 2007-01-03
i have however been on the forum for only a month
its awesome!!!:D

---

### Post by CowzRule on 2007-01-03
> **WMC said:**
> I've just done my very first Ubuntu installation, and the PC happened to have a TNT2 video card.  I got it going like this:

[LIST]
[*]download the **_[COLOR="Blue"][nvidia-glx-legacy drivers]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.15%2Fnvidia-glx-legacy_1.0.7174%2B2.6.15.12-1_i386.deb&md5sum=055b0320696d8b528ba718bd7b964e42&arch=i386&type=security")[/COLOR]_** to the desktop (the link is for the Dapper / 6.06 drivers - no idea if you need something different for Edgy / 6.10)
[*]doubleclick the .deb package and install the drivers
[*]open a terminal, type [FONT="Courier New"]**sudo nano /etc/X11/xorg.conf**[/FONT], press enter, then enter your password
[*]scroll down to the 'Device' section (it's a fair way down the page) and change the Driver line from 'nv' to 'nvidia'
[*]Press Ctrl+x
[*]Press Enter to keep the same filename
[*]Press 'y' to save
[*]Exit the terminal
[*]Log out, then log in
[/LIST]

If you get dumped to a terminal with an error upon restarting, just type 'sudo nano /etc/X11/xorg.conf' again, change the 'nvidia' back to 'nv', Ctrl+x to save, enter, y, then restart.Great instructions :) The only thing I'd had is after "Log Out", I'd do a "Ctrl+Alt+Backspace" to restart the xserver. That way you know for sure you've loaded the "nvidia" driver.

---

### Post by MkfIbK7a on 2007-01-03
yes i did Ctrl+Alt+Backspace after i loaded it earlier and started a XFCE4 sessions instead of gnome (for extra speed) it then showed the nvidia starup screen and continued with doubled video speed 

thx for the help WMC!

---

