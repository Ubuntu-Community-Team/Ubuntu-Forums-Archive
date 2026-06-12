---
title: "Install/Uninstall Programs + Fragmentation"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by P4rD0nM3 on 2007-10-08
Hello again, I was wondering if installing and then uninstalling programs in Ubuntu would leave certain files from the uninstalled program like Windows, wherein you actually have to have a 3rd party program monitor all files being installed + registry so that when you click uninstall you can trace back which one wasn't uninstalled. Thanks.

How do I defrag files in Ubuntu? Thanks.

---

### Post by dfreer on 2007-10-08
In general, yes, there are files left behind. Any file/folder that is installed with the program, that hasn't been modified by the user will be removed when uninstalled with *apt-get remove **yourprogramname***, unless the file is specifically mentioned in the DEBIAN/conffile included with the package. If the file is listed in DEBIAN/conffile, then it will get removed when you do an *apt-get --purge remove **yourprogramname*** .
Other files that will generally stick around, will be files that are created when the program *runs*, for example a user configuration file stored in the home directory. As long as you run the program as your regular user, it shouldn't be able to write files outside of your home directory anyways. /etc/ is also another place to check for global configuration files.

I'm not 100% positive on all unix/linux filesystems, but I'm pretty sure they take care of fragmented files themselves, without the need for user interaction.

EDIT: I dunno about programs that use the gnome registry, I never understood the need for it in the first place.

---

### Post by P4rD0nM3 on 2007-10-08
Is there like a place where I can read all the logs?

---

### Post by RomeReactor on 2007-10-08
Hi. As long as you use Synaptic, Add/Remove, or terminal package managers such as Apt-Get or Aptitude to install your programs, then your system will keep track of what goes where and will install any additional libraries the program you want to install needs. When you uninstall a program using those package managers, sometimes a few libraries will remain installed; this may be due to other programs needing them to function. In any case, upon uninstalling a program, you can run a command from the terminal (Applications->Accessories->Terminal) to remove any orphaned packages--those not used by any other program, and thus just using up space, although usually they  won't take up too many MB):
```
sudo apt-get autoremove
```

If you also want to remove the downloaded **.deb** packages used for installing programs (once a program is installed, these are largely useless unless you plan on re-installing something and don't want to download it again), then use this command:
```
sudo apt-get clean
```

Regarding fragmentation, by default Ubuntu uses the EXT3 filesystem, which is more efficient than NTFS or FAT in dealing with fragmentation; this means the filesystem fragments very little, so you practically don't need to defragment it.

EDIT: Logs are stored in **/var/log**; to view the system log, go to "System->Administration->System Log".

---

### Post by odzk on 2007-10-08
OT: is there a program in ubuntu that will defrag the hd? like the windows defrag?

---

### Post by P4rD0nM3 on 2007-10-08
When I type sudo apt -get autoremove, it says command not found.

Sorry, I'm really sensitive to this and usually if I can't figure out where the files are I just do a complete reinstall of the OS.

Like today I installed KwikDisk then uninstalled it. Where should I look for its files? I mean even though they might be harmless I really want to know where the files are so I can delete them just making my Ubuntu just like a fresh install.

---

### Post by mindtrick on 2007-10-08
As far as I know, linux doesn't need defragment. 

Also, there's a program called gtkorphan. It checks unneeded dependencies and configuration files.

---

### Post by jon zendatta on 2007-10-08
don't worry about fragmentation!
to clean i use
sudo aptitude autoclean
:KS

---

### Post by P4rD0nM3 on 2007-10-08
Are those commands available on a fresh install of ubuntu?

---

### Post by hyper_ch on 2007-10-08
> **P4rD0nM3 said:**
> When I type sudo apt -get autoremove, it says command not found.


it's
```

sudo apt-get autoremove

```

---

### Post by NotoriousMOK on 2007-10-08
This is a cool little how-to that I found really useful for dumping the garbage you are referring to


[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by odzk on 2007-10-08
> **mindtrick said:**
> As far as I know, linux doesn't need defragment. 

Also, there's a program called gtkorphan. It checks unneeded dependencies and configuration files.

ei cool, thats one thing i hate with windows. thanks ill check on that

---

### Post by dfreer on 2007-10-08
If you are really paranoid, *sudo apt-get --purge remove **yourpackagename*** should take care of everything, and delete the corresponding configuration file/folder in your home directory if it's there. But honestly, this isn't windows anymore, and unless you are having a problem there's absolutely no need to worry yourself about this.

Also, *sudo apt-get autoremove* as stated before, will uninstall any of the libraries that came with your original package, as long as nothing is using them. But there's nothing wrong with having extra libraries, saves you some time when installing the next program that needs them :D

---

