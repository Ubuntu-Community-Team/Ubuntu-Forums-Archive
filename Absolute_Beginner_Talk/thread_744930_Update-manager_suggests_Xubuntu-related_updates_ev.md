---
title: "Update-manager suggests Xubuntu-related updates even when i'm now on Ubuntu-desktop."
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by hanzj on 2008-04-04
I installed Xubuntu. Xubuntu recommended installing 237 updates, but I just ignored updating computer. Then I installed Ubuntu-desktop. What should i do with the Xubuntu-related updates?

 How do i know which updates i should NOT install?
 I can tell that I don't want to install XUBUNTU, because the package name is obvious, but what about others that I am not aware of? (I'm aware that Thunar is a Xubuntu program, but what about other packages)?

 it's not as simple as "sudo aptitude remove xubuntu-desktop", is it?

---

### Post by FreewareFan on 2008-04-04
One approach to the issue would be to remove all the sources that have xubuntu in the address, that are in your sources list..

---

### Post by mikeyphi on 2008-04-04
> **hanzj said:**
> I installed Xubuntu. Xubuntu recommended installing 237 updates, but I just ignored updating computer. Then I installed Ubuntu-desktop. What should i do with the Xubuntu-related updates?

 How do i know which updates i should NOT install?
 I can tell that I don't want to install XUBUNTU, because the package name is obvious, but what about others that I am not aware of? (I'm aware that Thunar is a Xubuntu program, but what about other packages)?

 it's not as simple as "sudo aptitude remove xubuntu-desktop", is it?

xubuntu and ubuntu have a lot of differences, you have an xubuntu OS with an ubuntu desktop overlay. If you want your present system to operate correctly you should install all the suggested updates.
Your other option, if you no longer want xubuntu, is to do a clean install of ubuntu.

---

### Post by kpkeerthi on 2008-04-04
> **hanzj said:**
> I installed Xubuntu. Xubuntu recommended installing 237 updates, but I just ignored updating computer. Then I installed Ubuntu-desktop. What should i do with the Xubuntu-related updates?

 How do i know which updates i should NOT install?
 I can tell that I don't want to install XUBUNTU, because the package name is obvious, but what about others that I am not aware of? (I'm aware that Thunar is a Xubuntu program, but what about other packages)?

 it's not as simple as "sudo aptitude remove xubuntu-desktop", is it?

Update Manager finds updates for the 'packages installed on your system'. It does not care what environment you are currently using (how can it be?). If you no longer need xubuntu desktop environment consider [removing it]("http://www.psychocats.net/ubuntu/puregnome") and xubuntu updates will be ignored.

---

### Post by hanzj on 2008-04-04
kpkeerthi,
RE: that link you gave (to psychocats)
I tried that "Remove Xubuntu" command in terminal
> 
sudo apt-get remove abiword abiword-common abiword-plugins brasero dbus-x11 gnumeric-common gnumeric-gtk gqview gtk2-engines-murrine gtk2-engines-xfce libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-common libgoffice-gtk-0-4 libgsf-gnome-1-114 libgtkmathview0c2a libjpeg-progs liblink-grammar4 libmodplug0c2 libmpcdec3 libots0 libpulse0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxine1 libxvmc1 link-grammar-dictionaries-en mousepad mozilla-thunderbird orage python-exo tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman thunderbird totem-xine vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop


but after it uninstalled everything, and when it was trying to install ubuntu-desktop, I couldn't connect to the internet anymore.
(using ndiswrapper).

---

### Post by wolfen69 on 2008-04-04
perhaps a clean install of ubuntu is in order at this point.

---

### Post by hanzj on 2008-04-04
one more cd to use?
8-)

---

