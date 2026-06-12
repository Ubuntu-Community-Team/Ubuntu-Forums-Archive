---
title: "What is this Package ERROR?"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by Knyven on 2005-08-21
IMAGES:

[IMG]http://geocities.com/knyven/screenshot.png[/IMG] 
?
[IMG]http://geocities.com/knyven/screenshot-1.png[/IMG] 

When i install my yahoo messenger that package is either an error or missing?
Even if i install plugins it says "Depends: (xxxxxx)not going to be installed"
[I][COLOR=Red]Uroot@kerberos:/home/kerberos # dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 58778 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger[/COLOR][/I]

another is:

[I][COLOR=Red]root@kerberos:/home/kerberos # sudo apt-get install gstreamer0.8-ffmpeg
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ymessenger: Depends: libgdk-pixbuf2 (>= 0.13.0) but it is not going to be installed
              Depends: libglib1.2 (>= 1.2.0) but it is not going to be installed
              Depends: libgtk1.2 (>= 1.2.0) but it is not going to be installed
              Depends: libssl0.9.6 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/COLOR][/I]

I have already manually updated and installed java, acrobat and replaced sources.list
I have tried adding -f but still the same, so do i need to download such file or i have a bad .iso or burning image defect???? ](*,)

---

### Post by Knyven on 2005-08-21
\\:D/ Ok i can't delete this post because i finally got it , it says apt-get -f install (without the package) meaning you just type [COLOR=Blue]apt-get -f install[/COLOR]
And it downloaded and installed the missing plugin.........sorry about that oh how absolute beginner i am.....i cant delete this post so sorry anyway

---

