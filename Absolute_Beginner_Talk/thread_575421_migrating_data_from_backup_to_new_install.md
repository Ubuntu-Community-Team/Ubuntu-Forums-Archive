---
title: "migrating data from backup to new install"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by jaygo on 2007-10-14
Hallo,
After a nasty hardware failure, I have kubuntu up and running and have my backup data copied onto the desktop. Now I need to reconfigure everything. I've migrated my /home data and I assume that I'll need to reinstall all of the apps I had. After installing the software, I'm hoping to save a day or two of tweaking by just migrating over folders from my backup.

I did a bit of this last week with some success: I copied the ./.kde subfolders to get my kontact data and some other stuff. In fact, all of the hidden folders in my home dir make sense to me, so mainly I'm curious how to migrate my other system configs, game files, themes and everything else that takes forever to rebuild.

My backup files include mostly intact copies of:
[LIST][*]bin
[*]boot
[*]etc
[*]initrd
[*]lib
[*]opt
[*]root
[*]sbin
[*]srv
[*]usr
[*]var
[/LIST]
Obviously, I just backed up most everything.

Also, I'll be doing this again in a week when I get some replacement hard drives (and may just reinstall to get 7.10). What can I do to make the migration easier next time? And what folders should I be backing up besides home? I plan on trying aptoncd ... anything else?

Thanks in advance.

---

### Post by Ferri on 2007-10-14
Your personal settings and files are in your user folder, inside /home. Most of the are in hidden folders (like /.kde).
Usually should be enough restoring the content of /home. In the other folders you have mentioned there are system data and you should keep them as they are. If you miss some app is better to reinstall it, you may cause quite a mess if you copy the contents of a previous /usr/bin folder, for instance.

---

### Post by philinux on 2007-10-14
+1 ferri only restore your home folder. Once restored read this to save any bother next time.

[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

---

### Post by nick_h on 2007-10-14
Yes /home will contain most settings.

The contents of /var/cache/apt may be worth copying over to save time downloading packages again. It may also help with remembering what packages were installed.

There may also be some files in the /etc directory which may be useful to copy across. For example the /etc/X11/xorg.conf for video settings and /etc/default/acpi-support if you had to tweak it for suspend/hibernate.

---

### Post by jaygo on 2007-10-15
Great. Yeah my old xorg.conf saves me a lot of headache setting up dual monitors, custom keyboard, & 7 button mouse. I'll grab acpi too. I read about building the list of installed packages with dpkg. I'm going to try doing it with aptoncd so I won't have to download most of the packages again.

So far, I've migrated most of the hidden folders out of /home with complete success. All of my keyboard shortcuts came over, kontact data, etc. A lot of the other configuration had to be redone. Oh well. 

Thanks for the tips :)  Hopefully someday we can build a script to grab all of this stuff before reinstalling and import it afterwards.

---

### Post by philinux on 2007-10-15
Oh one I forgot is sources.list

---

### Post by nick_h on 2007-10-15
Yes, thats another worth restoring.  I make a list of all files outside of /home that I have edited - there aren't that many that needed changing.

---

### Post by jaygo on 2007-10-16
ok, sources.lst added.

I imagine just copying over the entire home dir would work. However, I hand-copied some of the hidden config folders over ecause I was concerned about conflicts between old & new versions and didn't want to keep the files from apps I wasn't going to reinstall. Oops, I missed my kontact address book -- no worries, finally found it. Learning quickly...

---

