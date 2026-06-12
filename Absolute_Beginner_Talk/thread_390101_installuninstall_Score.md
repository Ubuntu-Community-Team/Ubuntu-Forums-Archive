---
title: "install/uninstall Score ?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by tshirtz1013 on 2007-03-21
Ok, so here's what is happening, I had removed all signs of gnome from within the terminal. 
>  sudo apt-get remove gnome* 

I then installed xfce4, as I had tried it and enjoyed the increased speed. I have however come to conclusion that at this time I enjoy the menu system and general well finished feel I get from ubuntu's gnome desktop. 

SO, on to my question now that you know how I feel. I am reinstalling gnome through the terminal by using the command
>  sudo aptitude install  ubuntu-desktop  

This command however gives me something I have noticed from other installs and un-installs for applications from the terminal.
> Score is -301


what is this score ? and should I be concerned ? I dont want to do this if i am being told its not a good decision . what is being graded :confused:

Thanks in advance for any help.

---

### Post by Kobalt on 2007-03-21
Do you want to keep both XFCE and Gnome or do you want to get rid of XFCE and keep Gnome only ?
Actually, aptitude gives you what will be updated, what will be removed and what will be kept appart before giving you this score. 
If you wish to get rid of XFCE, you should use this command line : 
```
sudo apt-get remove abiword abiword-common abiword-plugins anthy gnumeric-common gnumeric-gtk gqview gtk2-engines-xfce gxine libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libanthy0 libchewing3 libchewing3-data libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-common libgoffice-gtk-0-3 libgsf-gnome-1-114 libgtkmathview0c2a libjpeg-progs libmodplug0c2 libots0 libpcre3 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxcomposite1 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxine1 libxvmc1 mousepad mozilla-thunderbird orage python-cups python-exo scim-anthy scim-chewing scim-hangul scim-pinyin system-config-printer thunar thunar-archive-plugin thunar-media-tags-plugin vim-runtime xarchiver xfburn xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfprint4 xfwm4 xfwm4-themes xscreensaver xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs
```
And to install Gnome after that : 
```
sudo aptitude install ubuntu-desktop
```

---

### Post by tshirtz1013 on 2007-03-21
Thanks for the info, I was thinking of keeping xfce for now, but having gnome alongside it, and manage the login with gdm, which as of right now. I have to login via terminal there is no login manager. 

But I don't want to get away from my original question, I feel confident that no matter what I do with t desktop environment I will be capable of fixing it via terminal. what i really want to know is what the heck that score is all about ?

---

### Post by Yoooder on 2007-03-21
I haven't encountered the "Score" output, and I wonder if it may be something this is aptitude, not apt, specific.

Try doing a:
> sudo apt-get install ubuntu-desktop

I personally only use aptitude to search for packages, and handle (un)installs through apt-get.  However I don't do this for any particular reason...

---

### Post by tshirtz1013 on 2007-03-21
Yoooder: I have confirmed that when I use
>  sudo apt-get install ubuntu-desktop 
it does not display score information, so apparently this is something aptitude specific. I appreciate the information. Now all I must do is figure out the differences between apt-get and aptitude and what the scoring factor pertains to.

---

### Post by Yoooder on 2007-03-21
You have me curious about the "score" as well.  Aptitude is more of a full-featured packaged manager (kind of like a synaptic for bash) in that if you just run "aptitude" at the command prompt you can browse the entire database--it's really a very powerful utility.

Apt-get is much simpler, in that it lets you update the database, add and remove apps, and not a whole lot more.

---

