---
title: "Broken Dependencies - Cant Install"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by liamwithers on 2007-07-29
Hi, I can't install my download of the new Opera browser (probs not new, not used pc in months) and it wont let me. It says "Your system has broken dependencies. This application cannot continue until this is fixed. To fix it run 'sudo synaptic' or 'sudp apt-get install -f' 

Ive tried both, tried to fix my one broken package in synaptic but no luck. 

PLEASE HELP!

---

### Post by TeaSwigger on 2007-07-29
Which broken dependencies? Specifics?

Might be a silly question, but have you ran [COLOR="DarkRed"]sudo apt-get update[/COLOR] (or clicked "reload" in Synaptic) and used the automatic update very recently? If it hasn't been ran or updated in months, you'd want to be sure it's updated before trying to install new packages.

That's probably only a typo but to be clear, it's [COLOR="DarkRed"]sudo apt-get install -f[/COLOR] not [COLOR="DarkRed"]sudp apt-get install -f[/COLOR].

---

### Post by liamwithers on 2007-07-29
When i came back from leicester about a week ago i had tried to install my updates from the update manager thing and got the same message. :(

---

### Post by TeaSwigger on 2007-07-29
> **liamwithers said:**
> When i came back from leicester about a week ago i had tried to install my updates from the update manager thing and got the same message. :(

Being a newbie to ubuntu myself, the only suggestion I know to make here is that you might approach it first as a matter of ubuntu being too outdated for the easiest automated installation routes, so try to bring it to date. First, are you running the feisty fawn, aka ubuntu 7.04? If not, then I can't but suggest you look into updating to it; you'll find guides for updating. If your ubuntu is a feisty fawn (rather enjoy saying that ;) ) and you haven't done so yet, open a terminal and type at the prompt:

[COLOR="DarkRed"]sudo apt-get update[/COLOR]

It will ask for your password; enter it and wait for it to go through its paces and return you to the prompt. This is updating the inventory lists, if you like, of the package manager that the automatic updater uses to match things up so to speak. Among the scroll of updates it fetches, note any additional comments if it adds any, such as "you may want to run..." or if it lists the names of anything. Follow any instruction you may derive from that or paste the comments here for further help. If it suggests you run apt-get update despite just having done so, repeat the process anyway. If there are no notes, proceed to try ubuntu's automatic updater, update manager or whatever it's called. First hit the reload button and after that's done, have it check. Apply suggested updates. If that goes well, then move on to adding whatever it was you were attempting to add. 

If you still have problems please try to post the specific messages and someone more advanced than I should be able to help :)

---

### Post by forestpixie on 2007-07-29
you could check for partial installs

```

sudo dpkg -C
``` 

have you tried to purge the package in question?

by the way which broken package won't synaptic let you fix.

and as TeaSwigger has said better you post the actual messages you get

---

### Post by az on 2007-07-29
Exactly what happens when you run sudo apt-get -f install.  Post the output.  You probably need to update your sources, or you have mixed repositoties in your sources.list.

---

### Post by liamwithers on 2007-07-30
Sudo apt-get update:

liam@liam-desktop:~$ sudo apt-get update
Password:
Get:1 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/universe Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release                        
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Get:6 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]    
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
Fetched 6B in 4s (1B/s)
Reading package lists... Done


Ardour is broken.

liam@liam-desktop:~$ sudo dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 ubuntustudio-audio   Ubuntu Studio Audio Package


liam@liam-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  guile-1.6 libcrypto++5.2c2a amule-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ardour
The following NEW packages will be installed:
  ardour
0 upgraded, 1 newly installed, 0 to remove and 98 not upgraded.
1 not fully installed or removed.
Need to get 0B/4968kB of archives.
After unpacking 17.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 142556 files and directories currently installed.)
Unpacking ardour (from .../ardour_1%3a2.0-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in package ardour-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by az on 2007-07-30
There is no ardour package in feisty - just ardour-gtk.  You must have installed it from a 3rd-party source and that's what's causing our problems.  Remove it

sudo apt-get remove ardour

That package was improperly built - it should conflict with ardour-gtk (and remove ardour-gtk before it tries to install itself)

---

### Post by liamwithers on 2007-07-31
I think ardour was included with Ubuntu Studio. Thats why it would be there :)

---

### Post by liamwithers on 2007-07-31
liam@liam-desktop:~$ sudo apt-get remove ardour
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ardour is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ubuntustudio-audio: Depends: ardour
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by hazuken on 2007-07-31
I'm having the exact same problem, and this all came after I updated to ubuntu studio. 
My x server fails to load, and when I try to follow instructions to fix it, I end up at the same error messages regarding Ardour that liamwithers is getting.

---

### Post by az on 2007-07-31
Try 
sudo dpkg -r ardour

---

### Post by liamwithers on 2007-08-17
Sorry been in Leicester again.

liam@liam-desktop:~$ sudo dpkg -r ardour
Password:
dpkg - warning: ignoring request to remove ardour which isn't installed.

---

### Post by liamwithers on 2007-09-16
Help PLEASE!

---

