---
title: "c++ and c"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by damansandhu on 2007-09-07
hi , i dont know where to write programs of c and c++ ,
in windows i have some c++ software , when i run it  a dos like screen opens where i write programs and compiles them , i need similar thing in ubuntu .

---

### Post by Majorix on 2007-09-07
Try Eclipse or Anjuta. They are both available in repos.

If you don't need debugging etc you can just write your code in Gedit or similar text editor and then compile in terminal.

---

### Post by damansandhu on 2007-09-07
how to compile them in terminal?

---

### Post by LaRoza on 2007-09-07
In the Programming Talk forum you should have posted this.

First install the compiler and libraries:
```

sudo aptitude install build-essential

```

To compile, use gcc and g++ for C and C++ respectively:

```

gcc sourcefile.c -o program.bin

```

The -o option will name the program, if not specified, the executable will be called a.out.

You can compile files into object code with the -c switch:
```

gcc -o sourcefile.c

```
This will give you a file named sourcefile.o, which not executable.

---

### Post by damansandhu on 2007-09-07
when i write that in terminak "sudo aptitude install build-essential"

it started removing my installed applications , so i closed the terminal

what is the problem?

---

### Post by damansandhu on 2007-09-07
yes , many of my themes are removed , what the hell is this??

---

### Post by damansandhu on 2007-09-07
daman@Ultimate:~$ sudo aptitude install build-essential
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  festival festlex-cmu festlex-poslex festvox-kallpc16k
  gtk2-engines-ubuntulooks gtkhtml3.14 gucharmap gutenprint-locales
  hal-device-manager human-cursors-theme human-icon-theme human-theme
  hwdb-client-gnome language-selector libatspi1.0-0 libbeecrypt6 libbrlapi1
  libbtctl4 libestools1.2 libexchange-storage1.2-3 libgail-gnome-module
  libgimp2.0 libglew1 libgnome-mag2 libgnome-pilot2 libgnomebt0
  libgnomecupsui1.0-1c2a libgnomevfs2-bin libgutenprintui2-1 libhsqldb-java
  libmdbtools libopal-2.2.0 libpisock9 libpisync0 libpt-1.10.0
  libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 librpm4
  libservlet2.3-java libwmf0.2-7 libxevie1 lzop nautilus-sendto onboard
  openoffice.org openoffice.org-base openoffice.org-evolution
  openoffice.org-filter-mobiledev openoffice.org-gtk p7zip
  python-bittorrent python-gst0.10 python-notify python-orca-brlapi
  python-virtkey python-vte rdesktop restricted-manager rhythmbox rpm
  rss-glx screensaver-default-images serpentine sharutils sound-juicer
  ssh-askpass-gnome tangerine-icon-theme tango-icon-theme
  tango-icon-theme-common tsclient ubuntu-docs update-manager
  usplash-theme-ubuntu vino vnc-common whois xsane xsane-common xvncviewer
The following packages have been kept back:
  libkrb53
0 packages upgraded, 0 newly installed, 80 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 165MB will be freed.
Do you want to continue? [Y/n/?]

---

### Post by stchman on 2007-09-07
> **damansandhu said:**
> when i write that in terminak "sudo aptitude install build-essential"

it started removing my installed applications , so i closed the terminal

what is the problem?

Use apt-get instead of aptitude.

```
sudo apt-get install build-essential
```

Aptitude is no longer needed since Edgy came out.  If you want to remove an application use the autoremove feature.

---

