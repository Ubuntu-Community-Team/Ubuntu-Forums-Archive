---
title: "firefox  &amp; dpkg probs from a fresh newbie"
date: 2008-09-04
forum: Apple Hardware Users
---

### Post by nosilaver on 2008-09-04
Hi 
Two days ago I was given an apple mac with ubuntu on it. I am a first time user. I got firefox up for a day all working well then I allowed it to update and since then very little works - firefox and even ubuntu won't launch. I have looked at other threads and seen advice.

A search for firefox produced a message saying could not find compatible GRE 1.9.0 (etc)
I then ran sudo dpkg - - configure -a and was told it aborted.

Since then I have followed other instructions from threads and below is the massive list of all the results.

**Bottom line -  am I way in over my head and I need to get someone to remove all the programs and start again as I have no data on this machine.
Thanks 

To get to here I am currently working off a Windows PC in another room so can move between both.



User@user-desktop:~$ sudo apt-get update 
[sudo] password for user:  
0% [Connecting to ports.ubuntu.com] [Connecting to archive.ubuntu.com] 
0% [Connecting to ports.ubuntu.com] [Connecting to archive.ubuntu.com]^[[C^[[C 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy Release.gpg                         ^[[D^[[D3~ 
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy/main Translation-en_AU               
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy/restricted Translation-en_AU         
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy/universe Translation-en_AU           
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy/multiverse Translation-en_AU         
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-updates Release.gpg                  
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-updates/main Translation-en_AU       
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-updates/restricted Translation-en_AU 
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-updates/universe Translation-en_AU   
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-updates/multiverse Translation-en_AU 
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security Release.gpg                 
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security/main Translation-en_AU      
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security/restricted Translation-en_AU 
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security/universe Translation-en_AU  
  Could not resolve 'ports.ubuntu.com' 
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security/multiverse Translation-en_AU 
  Could not resolve 'ports.ubuntu.com' 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                        
  Could not resolve 'archive.ubuntu.com' 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                
  Could not resolve 'archive.ubuntu.com' 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy/Release.gpg](http://ports.ubuntu.com/ubuntu-ports/dists/hardy/Release.gpg)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy/main/i18n/Translation-en_AU.bz2](http://ports.ubuntu.com/ubuntu-ports/dists/hardy/main/i18n/Translation-en_AU.bz2)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy/restricted/i18n/Translation-en_AU.bz2](http://ports.ubuntu.com/ubuntu-ports/dists/hardy/restricted/i18n/Translation-en_AU.bz2)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy/universe/i18n/Translation-en_AU.bz2](http://ports.ubuntu.com/ubuntu-ports/dists/hardy/universe/i18n/Translation-en_AU.bz2)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy/multiverse/i18n/Translation-en_AU.bz2](http://ports.ubuntu.com/ubuntu-ports/dists/hardy/multiverse/i18n/Translation-en_AU.bz2)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'archive.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-updates/Release.gpg](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-updates/Release.gpg)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-updates/main/i18n/Translation-en_AU.bz2](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-updates/main/i18n/Translation-en_AU.bz2)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-updates/restricted/i18n/Translation-en_AU.bz2](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-updates/restricted/i18n/Translation-en_AU.bz2)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-updates/universe/i18n/Translation-en_AU.bz2](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-updates/universe/i18n/Translation-en_AU.bz2)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-updates/multiverse/i18n/Translation-en_AU.bz2](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-updates/multiverse/i18n/Translation-en_AU.bz2)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/Release.gpg](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/Release.gpg)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/main/i18n/Translation-en_AU.bz2](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/main/i18n/Translation-en_AU.bz2)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/restricted/i18n/Translation-en_AU.bz2](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/restricted/i18n/Translation-en_AU.bz2)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/universe/i18n/Translation-en_AU.bz2](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/universe/i18n/Translation-en_AU.bz2)  Could not resolve 'ports.ubuntu.com' 
 
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/multiverse/i18n/Translation-en_AU.bz2](http://ports.ubuntu.com/ubuntu-ports/dists/hardy-security/multiverse/i18n/Translation-en_AU.bz2)  Could not resolve 'ports.ubuntu.com' 
 
W: Some index files failed to download, they have been ignored, or old ones used instead. 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  
user@user-desktop:~$  
user@user-desktop:~$ sudo apt-get upgrade 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  
user@user-desktop:~$ sudo dpkg --configure -a  
Setting up gvfs-backends (0.2.5-0ubuntu2) ... 
 
Setting up libpango1.0-common (1.20.5-0ubuntu1) ... 
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
Failed to clean up for defoma: 256 at /usr/sbin/update-pangox-aliases line 48. 
dpkg: error processing libpango1.0-common (--configure): 
 subprocess post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of libpango1.0-0: 
 libpango1.0-0 depends on libpango1.0-common (>= 1.20.5-0ubuntu1); however: 
  Package libpango1.0-common is not configured yet. 
dpkg: error processing libpango1.0-0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org-core: 
 openoffice.org-core depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing openoffice.org-core (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org-draw: 
 openoffice.org-draw depends on openoffice.org-core (= 1:2.4.1-1ubuntu2); however: 
  Package openoffice.org-core is not configured yet. 
dpkg: error processing openoffice.org-draw (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of evince: 
 evince depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing evince (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org-gtk: 
 openoffice.org-gtk depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.4.1-1ubuntu2); however: 
  Package openoffice.org-core is not configured yet. 
dpkg: error processing openoffice.org-gtk (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libpolkit-gnome0: 
 libpolkit-gnome0 depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libpolkit-gnome0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libeel2-2: 
 libeel2-2 depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libeel2-2 (--configure): 
 dependency problems - leaving unconfigured 
Setting up bind9-host (1:9.4.2-10ubuntu0.1) ... 
dpkg: dependency problems prevent configuration of transmission-gtk: 
 transmission-gtk depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing transmission-gtk (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of file-roller: 
 file-roller depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing file-roller (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libedataserverui1.2-8: 
 libedataserverui1.2-8 depends on libpango1.0-0 (>= 1.20.5); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libedataserverui1.2-8 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of update-notifier: 
 update-notifier depends on libpango1.0-0 (>= 1.20.5); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing update-notifier (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libpoppler-glib2: 
 libpoppler-glib2 depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libpoppler-glib2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of deskbar-applet: 
 deskbar-applet depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing deskbar-applet (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of tomboy: 
 tomboy depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing tomboy (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of yelp: 
 yelp depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing yelp (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of evolution-exchange: 
 evolution-exchange depends on libedataserverui1.2-8 (>= 2.22.3); however: 
  Package libedataserverui1.2-8 is not configured yet. 
 evolution-exchange depends on libpango1.0-0 (>= 1.20.5); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing evolution-exchange (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org-writer2latex: 
 openoffice.org-writer2latex depends on openoffice.org-core (>= 1:2.3.0~oog680m1); however: 
  Package openoffice.org-core is not configured yet. 
dpkg: error processing openoffice.org-writer2latex (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgtksourceview2.0-0: 
 libgtksourceview2.0-0 depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libgtksourceview2.0-0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of nautilus: 
 nautilus depends on libeel2-2 (>= 2.21.90); however: 
  Package libeel2-2 is not configured yet. 
 nautilus depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing nautilus (--configure): 
 dependency problems - leaving unconfigured 
Setting up ttf-dejavu-extra (2.23-1) ... 
E: /var/lib/defoma/locked exists. 
E: Another defoma process seems running, or you aren't root. 
E: If you are root and defoma process isn't running undoubtedly, 
E: it is possible that defoma might have aborted. 
E: Please run defoma-reconfigure -f to fix its broken status. 
dpkg: error processing ttf-dejavu-extra (--configure): 
 subprocess post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of libgtkhtml3.14-19: 
 libgtkhtml3.14-19 depends on libpango1.0-0 (>= 1.20.5); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libgtkhtml3.14-19 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of evolution-plugins: 
 evolution-plugins depends on libedataserverui1.2-8 (>= 2.22.2); however: 
  Package libedataserverui1.2-8 is not configured yet. 
 evolution-plugins depends on libgtkhtml3.14-19 (>= 3.18.2); however: 
  Package libgtkhtml3.14-19 is not configured yet. 
 evolution-plugins depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing evolution-plugins (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of pidgin: 
 pidgin depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing pidgin (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org-calc: 
 openoffice.org-calc depends on openoffice.org-core (= 1:2.4.1-1ubuntu2); however: 
  Package openoffice.org-core is not configured yet. 
dpkg: error processing openoffice.org-calc (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org-filter-binfilter: 
 openoffice.org-filter-binfilter depends on openoffice.org-core (= 1:2.4.1-1ubuntu2); however: 
  Package openoffice.org-core is not configured yet. 
dpkg: error processing openoffice.org-filter-binfilter (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of evolution: 
 evolution depends on libedataserverui1.2-8 (>= 2.22.2); however: 
  Package libedataserverui1.2-8 is not configured yet. 
 evolution depends on libgtkhtml3.14-19 (>= 3.18.2); however: 
  Package libgtkhtml3.14-19 is not configured yet. 
 evolution depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing evolution (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of notification-daemon: 
 notification-daemon depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing notification-daemon (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libwnck22: 
 libwnck22 depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libwnck22 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ttf-dejavu: 
 ttf-dejavu depends on ttf-dejavu-extra; however: 
  Package ttf-dejavu-extra is not configured yet. 
dpkg: error processing ttf-dejavu (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-applets: 
 gnome-applets depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
 gnome-applets depends on libwnck22 (>= 2.19.5); however: 
  Package libwnck22 is not configured yet. 
dpkg: error processing gnome-applets (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of policykit-gnome: 
 policykit-gnome depends on libpolkit-gnome0; however: 
  Package libpolkit-gnome0 is not configured yet. 
dpkg: error processing policykit-gnome (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of tracker: 
 tracker depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
 tracker depends on libpoppler-glib2 (>= 0.6); however: 
  Package libpoppler-glib2 is not configured yet. 
dpkg: error processing tracker (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org-common: 
 openoffice.org-common depends on openoffice.org-core (>> 1:2.4.1); however: 
  Package openoffice.org-core is not configured yet. 
dpkg: error processing openoffice.org-common (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org-writer: 
 openoffice.org-writer depends on openoffice.org-core (= 1:2.4.1-1ubuntu2); however: 
  Package openoffice.org-core is not configured yet. 
dpkg: error processing openoffice.org-writer (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of compiz-gnome: 
 compiz-gnome depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
 compiz-gnome depends on libwnck22 (>= 2.19.5); however: 
  Package libwnck22 is not configured yet. 
dpkg: error processing compiz-gnome (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of firefox-3.0: 
 firefox-3.0 depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing firefox-3.0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of python-uno: 
 python-uno depends on openoffice.org-core (= 1:2.4.1-1ubuntu2); however: 
  Package openoffice.org-core is not configured yet. 
dpkg: error processing python-uno (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of nautilus-sendto: 
 nautilus-sendto depends on libpango1.0-0 (>= 1.20.5); however: 
  Package libpango1.0-0 is not configured yet. 
 nautilus-sendto depends on nautilus-extensions-2.0; however: 
  Package nautilus-extensions-2.0 is not installed. 
  Package nautilus which provides nautilus-extensions-2.0 is not configured yet. 
dpkg: error processing nautilus-sendto (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gtk2-engines-murrine: 
 gtk2-engines-murrine depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing gtk2-engines-murrine (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org: 
 openoffice.org depends on openoffice.org-calc; however: 
  Package openoffice.org-calc is not configured yet. 
 openoffice.org depends on openoffice.org-core (= 1:2.4.1-1ubuntu2); however: 
  Package openoffice.org-core is not configured yet. 
 openoffice.org depends on openoffice.org-draw; however: 
  Package openoffice.org-draw is not configured yet. 
 openoffice.org depends on openoffice.org-filter-binfilter; however: 
  Package openoffice.org-filter-binfilter is not configured yet. 
 openoffice.org depends on openoffice.org-writer; however: 
  Package openoffice.org-writer is not configured yet. 
 openoffice.org depends on ttf-dejavu; however: 
  Package ttf-dejavu is not configured yet. 
dpkg: error processing openoffice.org (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gdm: 
 gdm depends on libpango1.0-0 (>= 1.20.5); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing gdm (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of xulrunner-1.9: 
 xulrunner-1.9 depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing xulrunner-1.9 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-system-monitor: 
 gnome-system-monitor depends on libpango1.0-0 (>= 1.20.5); however: 
  Package libpango1.0-0 is not configured yet. 
 gnome-system-monitor depends on libwnck22 (>= 2.19.5); however: 
  Package libwnck22 is not configured yet. 
dpkg: error processing gnome-system-monitor (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of compiz: 
 compiz depends on compiz-gnome; however: 
  Package compiz-gnome is not configured yet. 
dpkg: error processing compiz (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org-style-human: 
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.4.1-1ubuntu2); however: 
  Package openoffice.org-common is not configured yet. 
dpkg: error processing openoffice.org-style-human (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org-gnome: 
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.4.1-1ubuntu2); however: 
  Package openoffice.org-core is not configured yet. 
 openoffice.org-gnome depends on openoffice.org-gtk; however: 
  Package openoffice.org-gtk is not configured yet. 
dpkg: error processing openoffice.org-gnome (--configure): 
 dependency problems - leaving unconfigured 
Setting up dnsutils (1:9.4.2-10ubuntu0.1) ... 
 
dpkg: dependency problems prevent configuration of seahorse: 
 seahorse depends on libgtksourceview2.0-0 (>= 2.2.0); however: 
  Package libgtksourceview2.0-0 is not configured yet. 
 seahorse depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing seahorse (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgtk-vnc-1.0-0: 
 libgtk-vnc-1.0-0 depends on libpango1.0-0 (>= 1.20.1); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libgtk-vnc-1.0-0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libgweather1: 
 libgweather1 depends on libpango1.0-0 (>= 1.20.5); however: 
  Package libpango1.0-0 is not configured yet. 
dpkg: error processing libgweather1 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openoffice.org-java-common: 
 openoffice.org-java-common depends on openoffice.org-common; however: 
  Package openoffice.org-common is not configured yet. 
dpkg: error processing openoffice.org-java-common (--configure): 
 dependency problems - leaving unconfigured 
dpkg: too many errors, stopping 
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed. 
Aborted

---

### Post by cyberdork33 on 2008-09-04
First, it would be most helpful to identify what hardware you are using. From what I can see you are on a PowerPC-based Mac, but what type? (iBook?, iMac?, PowerBook?)

Just a basic diagnosis, it looks like the machine cannot access the internet (or at least it cannot access the server where the updates are).

I am sure someone with more experience on PPC macs will be able to help you further, but you can try looking here in the meantime:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

---

