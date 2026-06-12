---
title: "apt-get install -f , acxcidently uninstalled alot of packages"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Rev_Chris on 2007-10-31
I accidentally removed alot of packages with this command.
Is there anyway to restore them or perhaps a way in reinstall the default packages without  deleting my other content  (pics ect) I am using 7.10 with latest updates but the last cd I have is 7.04 , any advice?

---

### Post by llamakc on 2007-10-31
For Ubuntu:

```

sudo apt-get update && sudo apt-get install --reinstall ubuntu-desktop

```

Will pull back in all of the packages.

---

### Post by Rev_Chris on 2007-10-31
Hey , thanks for the very fast response.

I got a few errors:

chris@chris-laptop:~$ sudo apt-get update
E: Some index files failed to download, they have been ignored, or old ones used instead.

(there were alot of ign in between)
and

chris@chris-laptop:~$ sudo apt-get install --reinstall ubuntu-desktopReading package lists... Done
Segmentation fault (core dumped)


Any ideas?

---

### Post by llamakc on 2007-10-31
You broke something badly. Why were you running the 'sudo apt-get -f install' command to begin with.

Try running this:

```

sudo aptitude install --reinstall ubuntu-desktop

```

If that fails there's a bigger problem with 'dpkg'. You may want to begin considering a backup plan to get your files (pics, songs, docs) off of that machine and reinstall.

Once again, what were you trying to install (that resulted in running the apt-get -f install command?

---

### Post by Rev_Chris on 2007-10-31
Hey,

chris@chris-laptop:~$ sudo aptitude install reinstall Ubuntu-desktop
Reading package lists... Done
Segmentation fault (core dumped)

(--reinstall isn't a valid command)

The whole story is I left my laptop on and the battery went dead , when it booted back up it was having problems (session less than 10 seconds, various unstarted program errors) and the update manager opened itself and suggested an update.

I tried to run the update manager and it gave me an error and suggested install -f  be run first , so I ran it and wasnt paying attention when it asked me to remove a huge list of packages. 
Luckily I was away and the uninstallation of something in the l(s) failed which seemed to allow the desktop to continue to function in some manner (im on it now)

That give you any insight?

---

### Post by llamakc on 2007-10-31
Get your stuff off of it before you go any further is my advice.

---

### Post by Rev_Chris on 2007-11-02
wow , was it ever messed up. I couldn't even reinstall properly until; I unformatted the whole disk , reformatted the entire thing to ntfs , then ran the installer and let it reformat the ntfs to ext3/swap. It would just keep crashing and giving me dpkg errors evertime I reinstalled without formatting.

I got kubuntu on it now and Im going to add gnome when im off work, it seems its all working now.

---

### Post by az on 2007-11-02
Check you ram (memtest)  and scan your drive for badblocks.

If you force the installation of a package that conflicts with others, when you run 
sudo apt-get -f install

it may very well remove some of your packages.  You should never mix packages from different sources than the Ubuntu repos and for the same release you are running.  This is not a binary-compatible OS.

---

