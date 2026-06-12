---
title: "Add / Remove Programs"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Billy Bong on 2007-03-17
Hello All,

I recently had probs adding and removing programs. I re-installed Ubuntu due to my lack of knowledge of linux. 

Fresh and new, I d/l Opera for linux and installed it. I respect Opera, so why not?

I then went to uninstall firefox. The  helpful menu told which other programs would be affected. No probs. but it said the desktop would be uninstalled. I thought that was ok because it would be different without the program.The only thing I have done is install Opera.

Now, under >applications, there is no add / remove programs options.

Any ideas?

Billy

---

### Post by Kobalt on 2007-03-17
Uninstalling Firefox doesn't actually uninstall your desktop, it uninstall a meta package (a package that actually links to a list of other packages) called ubuntu-desktop. Removing it is fine, though it's preferable to keep it installed...
I guess you could add the add/remove menu with Alacarte : just press Alt+F2, then enter 'alacarte' and press Enter. You'll be able to configure you menus from there...

---

### Post by Billy Bong on 2007-03-17
Thanks Kobalt,

Yeah, that works...but why? And it´s not the same. I mean why lose my add / remove from my Applications list? I just installed a browser amd removed aother?

---

### Post by Kobalt on 2007-03-17
> **Billy Bong said:**
> ... I mean why lose my add / remove from my Applications list? I just installed a browser amd removed aother?
You uninstalled the ubuntu-desktop package meanwhile. As I told you it's fine removing it, but it kind of affects the configuration of your system.

---

### Post by mcduck on 2007-03-17
> **Kobalt said:**
> You uninstalled the ubuntu-desktop package meanwhile. As I told you it's fine removing it, but it kind of affects the configuration of your system.

No, the problem is not uninstalling the ubuntu-desktop package, but instead uninstalling Firefox. Many other programs on Ubuntu desktop use Firefox's Gecko engine to render HTML, and removing Firefox will break all these applications.

Removing ubuntu-desktop should not cause any troubles (other than when you dist-upgrade to new Ubuntu version), but you should not remove Firefox even if you don't use it.

---

### Post by Billy Bong on 2007-03-17
Mate,

I can see what you are saying...but I still don´t understand...(I´m Australian...it probably takes awhile).

If I uninstalled the ubuntu-desktop package when I got rid of Firefox does that mean it´s part of the Ubuntu desktop. Like Windoze & Explorer?

---

### Post by mcduck on 2007-03-17
No. it doesn't matter if you have ubuntu-desktop package installed or not, removing it will not change anything in your system. It's just empty package that depends on all applications that are included in default ubuntu install (but no application depends on ubuntu-desktop). So installing the ubuntu-desktop package installs everything is included in default ubuntu desktop, but removing it will remove nothing else.

The problem is that many programs need Gecko to work. As long as Mozilla doesn't provide Gecko as a separate package there's nothing we can do about it, you need to have Firefox for those programs to work.

---

### Post by Kobalt on 2007-03-17
> **mcduck said:**
> you need to have Firefox for those programs to work.
Out of curiosity : which apps ?

---

### Post by Kateikyoushi on 2007-03-17
Ubuntu-desktop is just a list of packages which make up together the ubuntu desktop, it is not a software. You can remove it and no problem nothing will be uninstalled. 
On the other hand seems add/remove somehow depended on firefox and because it's dependency got removed it was removed as well because it could not function.
Actually System > Preferences > Synaptic is a more powerful tool and I would recommend to learn to use it.

---

### Post by Kateikyoushi on 2007-03-17
> **Kobalt said:**
> Out of curiosity : which apps ?

Search for firefox in synaptic then properties and check dependent packages. Quite a long list.

---

### Post by Billy Bong on 2007-03-17
Hi McDuck,

Cool name. 

But again, why do I care? I mean about rendering html. I really don´t care. I have Opera installed...as a real linux newbie am I missing something?

¨Removing ubuntu-desktop should not cause any troubles (other than when you dist-upgrade to new Ubuntu version), but you should not remove Firefox even if you don't use it.¨

Why not remove firefox? I really don´t see the importance of it.

If I am not seeing something...just say ¨stupid bastard¨ like I said I´m an aussie so I´ll look in other places.

---

### Post by mcduck on 2007-03-17
> **Billy Bong said:**
> Hi McDuck,

Cool name. 

But again, why do I care? I mean about rendering html. I really don´t care. I have Opera installed...as a real linux newbie am I missing something?

¨Removing ubuntu-desktop should not cause any troubles (other than when you dist-upgrade to new Ubuntu version), but you should not remove Firefox even if you don't use it.¨

Why not remove firefox? I really don´t see the importance of it.

If I am not seeing something...just say ¨stupid bastard¨ like I said I´m an aussie so I´ll look in other places.

Well, you had troubles with the Add/Remove-app, and it's one of those apps that use Gecko for HTML rendering (to provide the info text about packages) so if you want to use the Add/Remove-tool, you need Firefox.

---

### Post by Kobalt on 2007-03-17
> **Kateikyoushi said:**
> Search for firefox in synaptic then properties and check dependent packages. Quite a long list.
Thanks I'll take a quick look.

---

### Post by mcduck on 2007-03-17
> **Kateikyoushi said:**
> Search for firefox in synaptic then properties and check dependent packages. Quite a long list.

That tells you what packages Firefox needs to work, not what packages need Firefox ;)

Anyway, the name of the Add/Remove-app is gnome-app-install, and running apt-cache show gnome-app-install will tell you that it depends on Firefox:
> $ apt-cache show gnome-app-install
Package: gnome-app-install
Priority: optional
Section: gnome
Installed-Size: 1012
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Architecture: all
Version: 0.2.21
Depends: gconf2 (>= 2.12.1-4ubuntu1), python, synaptic (>= 0.57.8), python-gtkhtml2, python-gconf, python-glade2 (>= 2.4.0), python-apt (>= 0.6.13), python-xdg (>= 0.8), gnome-icon-theme, python-launchpad-integration, **firefox**, update-manager, app-install-data (>= 0.2.21), python-dbus, app-install-data-commercial, gksu, python-gdbm, python-gtk2 (>= 2.10.1)
Conflicts: gnome-app-install-data
Filename: pool/main/g/gnome-app-install/gnome-app-install_0.2.21_all.deb
Size: 178458
MD5sum: 58c40f6625b0059cd632b77a9c341072
SHA1: 3aae8861c637beaff1de49c0dec28d1812cfe804
SHA256: 6a59dad89252edcfc71a41f830527d0ec1f9d46a9ae26663fe84b85bfb4deded
Description: GNOME Application Installer
 A pretty application installer for GNOME.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop, xubuntu-desktop


---

### Post by Billy Bong on 2007-03-17
Guys.

Thanx for the feedback...but I´m a newbe. 

To say I know some dos commands is true.
To say I can manipulate the computer (under dos somewhat) is true.

To say I know anything about linux is FALSE.

Is Firefox apart of my installation?

---

### Post by Billy Bong on 2007-03-17
Mr McDuck,

Man, I still laugh at that name...reminds me of daffy...trying to be penguin.

If thats all there is to it then I shall have to reinstall firefox.

I still don´t see why...

Billy

---

### Post by mcduck on 2007-03-17
> **Billy Bong said:**
> Guys.

Thanx for the feedback...but I´m a newbe. 

To say I know some dos commands is true.
To say I can manipulate the computer (under dos somewhat) is true.

To say I know anything about linux is FALSE.

Is Firefox apart of my installation?

If you want to use tools like Add/Remove, the Help browser and many others, then yes, you must have Firefox. If you don't care about not having those tools then you don't need Firefox.

---

### Post by Billy Bong on 2007-03-17
Hi everyone,

I really am a linux newbie.. should I just reinstall firefox and forget about it? I mean that open source is just that. Why should Uuntu care if I remove firefox? I&#314;l just do it reinstall it and everythng will be cool.

Billy

---

### Post by mcduck on 2007-03-19
> **Billy Bong said:**
> Hi everyone,

I really am a linux newbie.. should I just reinstall firefox and forget about it? I mean that open source is just that. Why should Uuntu care if I remove firefox? I&#314;l just do it reinstall it and everythng will be cool.

Billy

I don't know how to explain this more clearly than what I've already done. But yes, just reinstall Firefox, and gnome-app-install as it was most likely removed with Firefox. Then you can hide Firefox from your menus and forget that it exists if you wish..

---

