---
title: "Failed Upgrade &amp; Nautilus"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Stavro on 2007-11-18
Hi all,

I'm a bit a beginner, and would greatly appreciate some help with this matter.

Downloaded and installed all the fixes outstanding for 7.04 and went for upgrade download to 7.10 but this failed.

Now Nautilus won't allow me to navigate to my folders (and keeps removing and redisplaying the open window), and the bin has gone.

How do I return to the (working) 7.04 ?

---

### Post by geirha on 2007-11-18
Could you be more specific on how it failed? What error messages you got for instance?

From what you've said allready though, it sounds like you have passed the "point of no return", while your upgrade hasn't properly completed. Meaning you can't get back to 7.04. I believe your best option is to try running 
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```
in a terminal. It will take a lot of time, and will require you to answer some questions from time to time. If it gives you any error messages, be sure to note them (and post them here for further help).

---

### Post by MegaJim on 2007-11-18
Can you try to continue the update process?

There isn't a way to go back to 7.04 from 7.10 (apart from reinstalling that is)

---

### Post by Stavro on 2007-11-19
Here is a error log from Nautilus

===== BEGIN MILESTONES =====
0x8187880 2007/11/19 19:36:24.4818 (GLog): failed to load icon 'lpi-help': Icon 'lpi-help' not present in theme
0x8187880 2007/11/19 19:36:24.4820 (GLog): gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed
0x8187880 2007/11/19 19:36:24.4820 (GLog): failed to load icon 'lpi-translate': Icon 'lpi-help' not present in theme
0x8187880 2007/11/19 19:36:24.4821 (GLog): gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed
0x8187880 2007/11/19 19:36:24.4822 (GLog): failed to load icon 'lpi-bug': Icon 'lpi-help' not present in theme
0x8187880 2007/11/19 19:36:24.5444 (GLog): failed to load icon 'lpi-help': Icon 'lpi-help' not present in theme
0x8187880 2007/11/19 19:36:24.5444 (GLog): gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed
0x8187880 2007/11/19 19:36:24.5445 (GLog): failed to load icon 'lpi-translate': Icon 'lpi-help' not present in theme
0x8187880 2007/11/19 19:36:24.5445 (GLog): gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed
0x8187880 2007/11/19 19:36:24.5445 (GLog): failed to load icon 'lpi-bug': Icon 'lpi-help' not present in theme
0x8187880 2007/11/19 19:36:32.1243 (GLog): failed to load icon 'lpi-help': Icon 'lpi-help' not present in theme
0x8187880 2007/11/19 19:36:32.1244 (GLog): gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed
0x8187880 2007/11/19 19:36:32.1244 (GLog): failed to load icon 'lpi-translate': Icon 'lpi-help' not present in theme
0x8187880 2007/11/19 19:36:32.1244 (GLog): gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed
0x8187880 2007/11/19 19:36:32.1244 (GLog): failed to load icon 'lpi-bug': Icon 'lpi-help' not present in theme
0x8187880 2007/11/19 19:36:35.7905 (USER): debug log dumped due to signal 11

---

### Post by Stavro on 2007-11-19
> **geirha said:**
> Could you be more specific on how it failed? What error messages you got for instance?

From what you've said allready though, it sounds like you have passed the "point of no return", while your upgrade hasn't properly completed. Meaning you can't get back to 7.04. I believe your best option is to try running 
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```
in a terminal. It will take a lot of time, and will require you to answer some questions from time to time. If it gives you any error messages, be sure to note them (and post them here for further help).

After the first command, I got the following errors:

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 compiz
 libgnomeui-0
 update-notifier
 python-apt
 compiz-gnome
 update-manager-core
 update-manager
 python-support
 python-numeric
 python-cairo
 launchpad-integration
 liblaunchpad-integration0
 synaptic
 libgksu2-0
 gksu

Help would be appreciated. Can I just go on and enter the second command?

---

### Post by geirha on 2007-11-20
It doesn't look good. You can try to do the two other commands, and then the first again and see if that helps.

You could also try to run ```
sudo dpkg-reconfigure -a
``` which will reconfigure all packages allready installed.

---

