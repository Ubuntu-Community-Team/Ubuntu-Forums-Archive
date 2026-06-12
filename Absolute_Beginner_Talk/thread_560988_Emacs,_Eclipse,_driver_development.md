---
title: "Emacs, Eclipse, driver development"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by pachu on 2007-09-27
hi all,
        i am new to Ubuntu... had been using linux very long time back. Almost frogotten all the fundamentals... :-(

I recently downloaded Ubuntu 7.04. I wanted to use it for driver delopment.

I wanted to install 
1) emacs, 
2) eclipse 
3) bittorrent 
4) Emule
5) CHM reader 

I have tried using sudo apt-get emacs21 and also sudo synaptic and also the add remove programs. For some reason all the three didnt work. 

I got some gnome error and the installation stopped. It showed some error which said lot of errors in a perl file. If required i shall post the errors.

But i felt i must be missing something to isntall the above softwares... can anyone suggest me how to use them.

---

### Post by justleen on 2007-09-27
the easiest way is trough apt-get or synaptic (the GUI version..)

you can search with apt-cache search <package name> , perhaps the packages was unknown?

Can you give us the errors? (or a relevant part..)

---

### Post by pachu on 2007-09-27
Hello justleen,
                         Thanks for the reply. I have put below the error strings. 

======================
[COLOR="Orange"]GLib-CRITICAL **:g_datalist_id_set_data_full:assertion 'destroy_func == NULL'
failed at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 54 <> line 7.[/COLOR]

In a similar manner the above lines are repeated many time, with only the line number changing to either 54, 60, 68. Rest of the string is same... Then at the end the following lines are displayed.

[COLOR="Orange"]dpkg:parse error, in file '/var/lib/dpkg/available' near line 10915 package 'libnautilus2-2':
error in version string '131072:': Nothing after colon in verson number  
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install . Trying to recover:[/COLOR]

And sudo apt-get emacs 21, throws and error "E: invalid operation emacs21"

apt-cache does show all the emacs packages. 

Kindly let me know if i am missing something. 

Thanks and regards
Pachu/-

---

### Post by pachu on 2007-09-28
Hi all,
           I dont know if this is right... but after doing the following i am able to install any software i want using synaptic or apt-get. I dont know if this is a bug or it is my ignorance. Kindly let me know. 

[COLOR="DarkOrange"]dpkgarse error, in file '/var/lib/dpkg/available' near line 10915 package 'libnautilus2-2':
error in version string '131072:': Nothing after colon in verson number [/COLOR]


I modified the file /var/lib/dpkg/available and removed the line which says the following

[COLOR="DarkOrange"]package: libnautilus2-2
version: 131072:
[/COLOR]

i understood that libnautilus is required for Ubuntu... but the version number seems wrong. I removed it and ran synaptic again... it said that i need to run " [COLOR="DarkOrange"]dpkg --configure -a[/COLOR]" again to correct the file available. And i did so and after that all installations using apt-get or synaptic seems to be working fine. 

was interesting... let me know if i have done something wrong. 
thanks all of you....

thanks and regards
pachu

---

