---
title: "Apt Errors"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by ashkev on 2007-08-15
Every time I install a package with apt-get, I get the following error.

Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-filter-mobiledev
 openoffice.org-style-human
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas?

Thanks

---

### Post by dannyboy79 on 2007-08-15
what version are you running, Feisty, Edgy, Gutsy? Are you remembering to always do a 
sudo aptitude update 
first?

---

### Post by st33med on 2007-08-15
Also, for a better error descriptions (usually) try adding --verbose after anything. Example:
```
sudo apt-get install <program> --verbose
```

However, the --verbose could be different in other programs. If the code I gave you doesn't work, check this:

```
apt-get --help
```

There should be a command that makes output verbose.

---

### Post by st33med on 2007-08-15
> **dannyboy79 said:**
> what version are you running, Feisty, Edgy, Gutsy? Are you remembering to always do a 
sudo aptitude update 
first?

This also might be a dpkg problem. Notice the end of the line:
> E: Sub-process /usr/bin/dpkg returned an error code (1)


I am away from my computer, so I don't know how to test dpkg. Could someone else fill-in?

---

### Post by ashkev on 2007-08-15
I am running Edubuntu Server Feisty.  The Errors started right after install, when I updated.

---

### Post by Hobo Joe on 2007-08-15
Make sure no other install program is running, synaptic, update manager, automatix, etc.

---

### Post by ashkev on 2007-08-15
I just ran apt-get update then apt-get install -f.  Here is the output:
Fetched 3B in 5s (1B/s)  
Reading package lists... Done
kevin@edubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
17 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up ttf-opensymbol (2.2.0-1ubuntu4) ...
Updating fontconfig cache...
/usr/share/fonts: failed to write cache
/usr/share/fonts/X11: failed to write cache
/usr/share/fonts/X11/100dpi: failed to write cache
/usr/share/fonts/X11/75dpi: failed to write cache
/usr/share/fonts/X11/Type1: failed to write cache
/usr/share/fonts/X11/encodings: failed to write cache
/usr/share/fonts/X11/encodings/large: failed to write cache
/usr/share/fonts/X11/misc: failed to write cache
/usr/share/fonts/X11/util: failed to write cache
/usr/share/fonts/truetype/freefont: failed to write cache
/usr/share/fonts/truetype/kochi: failed to write cache
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-arabeyes: failed to write cache
/usr/share/fonts/truetype/ttf-bengali-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-bitstream-vera: failed to write cache
/usr/share/fonts/truetype/ttf-dejavu: failed to write cache
/usr/share/fonts/truetype/ttf-devanagari-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-gentium: failed to write cache
/usr/share/fonts/truetype/ttf-gujarati-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-kannada-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-lao: failed to write cache
/usr/share/fonts/truetype/ttf-malayalam-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-mgopen: failed to write cache
/usr/share/fonts/truetype/ttf-oriya-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-punjabi-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-tamil-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-telugu-fonts: failed to write cache
/usr/share/fonts/type1: failed to write cache
/usr/share/fonts/type1/gsfonts: failed to write cache
/usr/share/X11/fonts: failed to write cache
/usr/share/X11/fonts/100dpi: failed to write cache
/usr/share/X11/fonts/75dpi: failed to write cache
/usr/share/X11/fonts/Type1: failed to write cache
/usr/share/X11/fonts/encodings: failed to write cache
/usr/share/X11/fonts/encodings/large: failed to write cache
/usr/share/X11/fonts/misc: failed to write cache
/usr/share/X11/fonts/util: failed to write cache
/usr/local/share/fonts: failed to write cache
/var/lib/defoma/fontconfig.d/A: failed to write cache
/var/lib/defoma/fontconfig.d/C: failed to write cache
/var/lib/defoma/fontconfig.d/F: failed to write cache
/var/lib/defoma/fontconfig.d/G: failed to write cache
/var/lib/defoma/fontconfig.d/H: failed to write cache
/var/lib/defoma/fontconfig.d/K: failed to write cache
/var/lib/defoma/fontconfig.d/L: failed to write cache
/var/lib/defoma/fontconfig.d/N: failed to write cache
/var/lib/defoma/fontconfig.d/O: failed to write cache
/var/lib/defoma/fontconfig.d/R: failed to write cache
/var/lib/defoma/fontconfig.d/T: failed to write cache
/var/lib/defoma/fontconfig.d/U: failed to write cache
/var/lib/defoma/fontconfig.d/V: failed to write cache
/var/lib/defoma/fontconfig.d/a: failed to write cache
/var/lib/defoma/fontconfig.d/j: failed to write cache
/var/lib/defoma/fontconfig.d/m: failed to write cache
/var/lib/defoma/fontconfig.d/u: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 55
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 2.2.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-impress; however:
  Package openoffice.org-impress is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
 openoffice.org depends on openoffice.org-math; however:
  Package openoffice.org-math is not configured yet.
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.2.0) | openoffice.org-core-experimental (>> 2.2.0); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 python-uno
 openoffice.org-writer
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-filter-mobiledev
 openoffice.org-style-human
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by st33med on 2007-08-15
I think I should have asked this the first time. Did you put a sudo in front of 'apt-get'?

Just checking...

---

### Post by ashkev on 2007-08-15
yes I did

---

### Post by st33med on 2007-08-15
Alright, try this:
```
sudo dpkg --configure -a
```

This should configure all unpacked packages that haven't been configured. If it gives errors, post them here.

---

### Post by ashkev on 2007-08-15
kevin@edubuntu:~$ sudo dpkg --configure -a
Password:
Setting up ttf-opensymbol (2.2.0-1ubuntu4) ...
Updating fontconfig cache...
/usr/share/fonts: failed to write cache
/usr/share/fonts/X11: failed to write cache
/usr/share/fonts/X11/100dpi: failed to write cache
/usr/share/fonts/X11/75dpi: failed to write cache
/usr/share/fonts/X11/Type1: failed to write cache
/usr/share/fonts/X11/encodings: failed to write cache
/usr/share/fonts/X11/encodings/large: failed to write cache
/usr/share/fonts/X11/misc: failed to write cache
/usr/share/fonts/X11/util: failed to write cache
/usr/share/fonts/truetype/freefont: failed to write cache
/usr/share/fonts/truetype/kochi: failed to write cache
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-arabeyes: failed to write cache
/usr/share/fonts/truetype/ttf-bengali-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-bitstream-vera: failed to write cache
/usr/share/fonts/truetype/ttf-dejavu: failed to write cache
/usr/share/fonts/truetype/ttf-devanagari-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-gentium: failed to write cache
/usr/share/fonts/truetype/ttf-gujarati-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-kannada-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-lao: failed to write cache
/usr/share/fonts/truetype/ttf-malayalam-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-mgopen: failed to write cache
/usr/share/fonts/truetype/ttf-oriya-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-punjabi-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-tamil-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-telugu-fonts: failed to write cache
/usr/share/fonts/type1: failed to write cache
/usr/share/fonts/type1/gsfonts: failed to write cache
/usr/share/X11/fonts: failed to write cache
/usr/share/X11/fonts/100dpi: failed to write cache
/usr/share/X11/fonts/75dpi: failed to write cache
/usr/share/X11/fonts/Type1: failed to write cache
/usr/share/X11/fonts/encodings: failed to write cache
/usr/share/X11/fonts/encodings/large: failed to write cache
/usr/share/X11/fonts/misc: failed to write cache
/usr/share/X11/fonts/util: failed to write cache
/usr/local/share/fonts: failed to write cache
/var/lib/defoma/fontconfig.d/A: failed to write cache
/var/lib/defoma/fontconfig.d/C: failed to write cache
/var/lib/defoma/fontconfig.d/F: failed to write cache
/var/lib/defoma/fontconfig.d/G: failed to write cache
/var/lib/defoma/fontconfig.d/H: failed to write cache
/var/lib/defoma/fontconfig.d/K: failed to write cache
/var/lib/defoma/fontconfig.d/L: failed to write cache
/var/lib/defoma/fontconfig.d/N: failed to write cache
/var/lib/defoma/fontconfig.d/O: failed to write cache
/var/lib/defoma/fontconfig.d/R: failed to write cache
/var/lib/defoma/fontconfig.d/T: failed to write cache
/var/lib/defoma/fontconfig.d/U: failed to write cache
/var/lib/defoma/fontconfig.d/V: failed to write cache
/var/lib/defoma/fontconfig.d/a: failed to write cache
/var/lib/defoma/fontconfig.d/j: failed to write cache
/var/lib/defoma/fontconfig.d/m: failed to write cache
/var/lib/defoma/fontconfig.d/u: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 55
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.2.0) | openoffice.org-core-experimental (>> 2.2.0); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-gtk
 openoffice.org-calc
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org
 openoffice.org-evolution
 openoffice.org-style-human
 openoffice.org-gnome
 openoffice.org-java-common
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math
 openoffice.org-filter-mobiledev

---

### Post by dannyboy79 on 2007-08-16
well now that I see more info I am aware of this problem. It's a bug reported here with a solution

[https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/104553](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/104553)

---

### Post by ashkev on 2007-08-16
Thanks for all the help.  I just went ahead and reinstalled the OS and everything is fine now.

---

### Post by ulfric on 2007-08-21
I did a quick search for your error and found this, (it solved my issue which matched yours exactly btw) hope it helps.


Workaround as per forums:
find /usr/share/fonts /usr/local/share/fonts /var/lib/defoma/fontconfig.d -type d -print0 | xargs --null touch


This command did NOT work with the sudo command, I had to create a root shell with sudo su -
in order to run the command and have it complete successfully. All the print0 and --null do is make it work with file names that have spaces or other weird characters, so basically for some reason the time stamp on the files were off and thus it couldn't hit the font files. 


It seems to me like no one actually READ your problem and just put a bunch of newbie answers instead of actually thinking about it.  


p.s. I didn't check the date on this thread and it suddenly occurred to me I may be grave digging, if this thread is an oldy and moly my apologies, however since I ran into the issue with the latest build (on 64 bit amd) then it must still be relevant.

---

### Post by ulfric on 2007-08-21
Doh i posted to the wrong tab! #-o that's what I get for griping about other peoples replies

---

### Post by dajhorn on 2007-08-22
This isn't a dead issue.  It happened to me with the latest Feisty update.

---

### Post by Arthur Archnix on 2007-08-22
Maybe I missed something, but what was up with the command:
```
sudo apt-get install -f
```

Edit: Oh I see. Thank you man page. Never needed that before, don't think I'll ever need it, but good to know.  Wait... does it work with install?

---

