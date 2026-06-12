---
title: "Autoremove autoremoved too much. Sheesh."
date: 2012-11-21
forum: Any Other OS
---

### Post by p.s. on 2012-11-21
I ran *sudo apt-get autoremove *to clear out some unnecessary packages I thought might be sitting around. The list that started running down the screen was looking a little fishy (and large) and when I saw gedit go by I knew something was wrong.

I canceled the process, and my system still runs, but it removed an enormous chunk of packages.

It seems to me that the optimal solution is to run *sudo apt-get install all-those packages-that got-removed etc-etc.*

So right now I'm trying to figure out a good way to generate this list, without doing it by hand.

I scrolled up in the terminal and copied the list that the terminal was making of what had been removed. I also started digging around in var/log to try and find the exact *apt-get remove list* so I could just copy and paste it. I found something almost like it in var/log/apt, but it has a lot of other characters (a :i386 is appended to every package, and there's a set of parentheses with a version number) and when I copy that list into *apt-get install* it can't read it.

Anyone have any thoughts on this? I guess some sort of script could maybe remove all the extraneous stuff from the log entry I have and format the packages with a single space between them, but I'm no scripting wizard. Ideally there's an already formatted list of what got removed somewhere in the logs and I just can't find it? Or a "reverse x" command that I don't know about? Or something?

I've attached the two lists that I currently have.

Dell Inspiron 1521
Debian Squeeze

---

### Post by bab1 on 2012-11-21
> **p.s. said:**
> ...So right now I'm trying to figure out a good way to generate this list, without doing it by hand.

You can always run apt-get with the *-s* switch to preview what will happen.  If you direct the output to a file you can open it in you favorite text editor.  This will redirect the output to a file in you home directory named *autoremove.file*```
sudo apt-get [COLOR="Red"]**-s **[/COLOR] autoremove > autoremove.file
```

---

### Post by p.s. on 2012-11-21
Are you saying that this is a way to reverse what I did?

Or that it's a way that I could have previewed what I did before I did it, and should do that next time?

Thanks for your help and interest either way, I'm just not sure I understand.

---

### Post by bab1 on 2012-11-21
> **p.s. said:**
> Are you saying that this is a way to reverse what I did?

Or that it's a way that I could have previewed what I did before I did it, and should do that next time?

Thanks for your help and interest either way, I'm just not sure I understand.

I said > You can always run apt-get with the -s switch to **preview** what will happen...

I don't know of anyway to undo what you have done.  When you use sudo you are acting as the superuser root.  No action will be questioned including potentially destructive actions.  But... The apt-get scripts have been used for many years by thousands of users.  I doubt that the script is at fault for what happened.  Have you modified the install in any way?

---

### Post by PaulW2U on 2012-11-21
From the apt-get man page

> autoremove
autoremove is used to remove packages that were automatically installed to satisfy dependencies for other packages and are now no longer needed.

So why do you want to re-install packages that you no longer need? :confused:

If most of the packages have :i386 appended to their name I am presuming you have a 64-bit system. May be you installed a 32-bit package at some time which automatically installed all the 32-bit dependencies? 

If everything works then apt-get is correctly removing unwanted packages. By removing them the number of packages that you might need to update in the future has been reduced.

---

### Post by SlugSlug on 2012-11-21
```
sudo apt-get install abiword-common gnome-user-share libapache2-mod-dnssd apache2.2-bin software-center aptdaemon baobab binfmt-support additional bogofilter bogofilter-bdb bogofilter-common cheese cheese-common chromium-browser-inspector tomboy libndesk-dbus-glib1.0-cil libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libndesk-dbus1.0-cil libmono-addins-gui0.2-cil libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-addins0.2-cil libgnomepanel2.24-cil libgnomepanel2.24-cil libgnome2.24-cil libgnome2.24-cil libglade2.0-cil libglade2.0-cil libgtk2.0-cil libgtk2.0-cil libgnome-vfs2.0-cil libgnome-vfs2.0-cil libgconf2.0-cil libgconf2.0-cil libart2.0-cil libart2.0-cil libgmime2.4-cil libgmime2.4-cil libglib2.0-cil libglib2.0-cil cli-common dasher dasher-data dmz-cursor-theme using dnsmasq-base ekiga empathy nautilus-sendto-empathy empathy-common eog epiphany-extensions espeak gok gnome-orca libgnome-speech7 libespeak1 espeak-data evolution-common evolution-plugins evolution-webcal file-roller freedesktop-sound-theme gnome-games python-gtkglext1 python-opengl freeglut3 gcalctool gconf-editor gconf-defaults-service gdebi gdebi-core gedit-plugins gedit gedit-common geoclue-yahoo geoclue-manual geoclue-localnet geoclue-hostip geoclue gnome-accessibility-themes gnome-backgrounds gnome-bluetooth gnome-games-data gnome-cards-data gnome-codec-install gnome-disk-utility gnome-games-extra-data gnome-mag gnome-nettool gnome-screenshot gnome-search-tool gnome-session-canberra gnome-system-log gnome-system-tools gnome-themes gnome-themes-extras gnome-themes-more gnuchess-book gnuchess gnumeric-common
```


might work :/

---

### Post by arpanaut on 2012-11-21
From "man apt-get"
> autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed.

Are you sure that apt was not just removing old or obsolete versions of said packages, that were dependences at one time but no longer needed.  
As said above, it would be unusual for apt to hose the system unless your system is set up in an unusual manner or is in an inconsistent or broken state.
Check the version numbers of the packages removed as compared to what you have installed.
Have you added PPA's or removed PPA's without using PPA-purge?
Have you done a release upgrade recently and opted not to remove "old packages"

Just throwing out some ideas here...

---

### Post by p.s. on 2012-11-21
Bab1: I haven't modified the installation in any way that seems relevant. I did install xfce recently just to try it out, and I read that debian is moving to xfce in the next version, so maybe by installing it somehow thought that all of the gnome packages needed to go?

  Either way, I'm definitely not saying the script is somehow "at fault". I'm just trying to figure out a way of generating a list of removed packages from the output of *apt-get remove* that will be readable by apt-get install. The alternative would be my hand-typing all the package names (onerous even with autocomplete and uneducational) or reinstalling (annoying and uneducational).

PaulW2U: It removed many packages that I want. (Gedit, eog, gnome-screenshot, etc.) Gedit isn't just some library that's no longer required. I can't think of any good reason why the system would decide that gedit should be removed unless I told it to remove it. That makes me feel like something went awry.

---

### Post by p.s. on 2012-11-21
SlugSlug! Mind telling us how you did that?

---

### Post by SlugSlug on 2012-11-21
are you on unity now?

maybe just a 


```
apt-get install --reinstall ubuntu-desktop
```

---

### Post by p.s. on 2012-11-21
> **arpanaut said:**
> From "man apt-get"


Are you sure that apt was not just removing old or obsolete versions of said packages, that were dependences at one time but no longer needed.  
As said above, it would be unusual for apt to hose the system unless your system is set up in an unusual manner or is in an inconsistent or broken state.
Check the version numbers of the packages removed as compared to what you have installed.
Have you added PPA's or removed PPA's without using PPA-purge?
Have you done a release upgrade recently and opted not to remove "old packages"

Just throwing out some ideas here...

Well, that's what I would have thought, but how does gedit fit into that mix? Or eog? And why did it leave me with a mouse/cursor/clock graphics setup that looks like it's 1992?

---

### Post by p.s. on 2012-11-21
> **SlugSlug said:**
> are you on unity now?

maybe just a 


```
apt-get install --reinstall ubuntu-desktop
```


Well, I'm using Debian on this machine, so not using Unity. It's Gnome.

---

### Post by SlugSlug on 2012-11-21
> **p.s. said:**
> SlugSlug! Mind telling us how you did that?

opend your text file in openoffice calc :) got a column of apps after adding a 'space' as a separator, then pasted in to google to turn that column into a row :D

---

### Post by lykwydchykyn on 2012-11-21
These problems usually happen when you mix package managers, particularly aptitude and apt-get, or aptitude and synaptic, etc.  Is this debian?  I noticed you marked it [other_os] but I don't see if you mentioned which OS it is.

If it's Debian I'd recommend using aptitude to avoid these problems in the future.  It's designated as the "official" apt front end, so automatic package installs (like say tasksel or debian installer) are likely going to register installs with aptitude's database rather than apt-get's. 

Anyway, what probably happened is something in xfce conflicted with something in gnome, causing a meta-package like "gnome-desktop-environment" or similar to get removed.  Since your gnome packages were installed as dependencies of the meta-package, they get detected as "unneeded" once the meta-package is removed.  Annoying shortcoming of the whole "autoremove" functionality.

That's all speculation of course, but the first thing I'd check is if the meta-package is installed or not.

---

### Post by PaulW2U on 2012-11-21
> **p.s. said:**
> PaulW2U: It removed many packages that I want. (Gedit, eog, gnome-screenshot, etc.) Gedit isn't just some library that's no longer required. I can't think of any good reason why the system would decide that gedit should be removed unless I told it to remove it. That makes me feel like something went awry.

So gedit no longer works?

Please confirm whether you have a 32-bit or 64-bit installation.

---

### Post by p.s. on 2012-11-21
> **SlugSlug said:**
> opend your text file in openoffice calc :) got a column of apps after adding a 'space' as a separator, then pasted in to google to turn that column into a row :D

That is absolutely genius.

---

### Post by p.s. on 2012-11-21
> **PaulW2U said:**
> So gedit no longer works?

Please confirm whether you have a 32-bit or 64-bit installation.

It removed gedit and everything associated with it entirely. The first thing I did was reinstall it because I didn't want to have to solve the rest of the problem in nano.

I have a 32 bit installation. The machine is capable of 64, but I never bother with it. One gig of ram, and all I really do with my computer is use email, use google maps, and break it through uninformed experimentation.

---

### Post by PaulW2U on 2012-11-21
> **p.s. said:**
> It removed gedit and everything associated with it entirely. The first thing I did was reinstall it because I didn't want to have to solve the rest of the problem in nano.

I have a 32 bit installation. The machine is capable of 64, but I never bother with it. One gig of ram, and all I really do with my computer is use email, use google maps, and break it through uninformed experimentation.

Thanks for confirming 32-bit.

Obviously a very different problem from what I first thought.....:confused:

---

### Post by p.s. on 2012-11-21
> **lykwydchykyn said:**
> These problems usually happen when you mix package managers, particularly aptitude and apt-get, or aptitude and synaptic, etc.  Is this debian?  I noticed you marked it [other_os] but I don't see if you mentioned which OS it is.

If it's Debian I'd recommend using aptitude to avoid these problems in the future.  It's designated as the "official" apt front end, so automatic package installs (like say tasksel or debian installer) are likely going to register installs with aptitude's database rather than apt-get's. 

Anyway, what probably happened is something in xfce conflicted with something in gnome, causing a meta-package like "gnome-desktop-environment" or similar to get removed.  Since your gnome packages were installed as dependencies of the meta-package, they get detected as "unneeded" once the meta-package is removed.  Annoying shortcoming of the whole "autoremove" functionality.

That's all speculation of course, but the first thing I'd check is if the meta-package is installed or not.

Thanks. I'll look into the aptitude thing. I came from Ubuntu to Debian, and have just continued to use the nomenclature I'm used to.

I'm glad to hear that my suspicion that it was a conflict with xfce wasn't unreasonable. Most of the packages whose function I can identify by sight are gnome-related.

---

### Post by p.s. on 2012-11-21
Well, SlugSlug's list worked like a charm as far as I can tell. Thanks!!

---

### Post by oldos2er on 2012-11-21
Moved to Other OS/Distro Talk.

---

### Post by PaulW2U on 2012-11-21
> **p.s. said:**
> Thanks. I'll look into the aptitude thing. I came from Ubuntu to Debian, and have just continued to use the nomenclature I'm used to.

So we weren't even talking about Ubuntu? :(

---

### Post by p.s. on 2012-11-21
> **PaulW2U said:**
> So we weren't even talking about Ubuntu? :(

No, but we were talking about its mommy, so it's all copacetic.

(N.B. My OP states that this problem occurred on a Debian installation and was marked as "Other OS".)

---

### Post by PaulW2U on 2012-11-21
> **p.s. said:**
> No, but we were talking about its mommy, so it's all copacetic.

(N.B. My OP states that this problem occurred on a Debian installation and was marked as "Other OS".)

I see that now.     :(

---

### Post by p.s. on 2012-11-21
> **PaulW2U said:**
> I see that now.     :(

Well, thanks for helping me to figure it out either way!

---

