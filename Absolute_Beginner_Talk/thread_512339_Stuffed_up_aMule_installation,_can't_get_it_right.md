---
title: "Stuffed up aMule installation, can't get it right"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2007-07-29
Installed aMule via Synaptic and during the configuration I stupidly pointed the download file to a music folder on an NTFS partition.

I'm sure that's why I can't set the permissions.

Realising my mistake, I decided to completely remove aMule, via Synaptic and start again this time pointing to a EXT3 fomatted folder.

On re-downloading aMule, it's still set up as my original, some of the information hasn't been removed during the un-install.

How can I either re-configure aMule ( I can't get past the error message pasted below) or completely remove it and start again.

Thanks.

---

### Post by felicity on 2007-07-29
To remove software and the configuration files you can use this from a terminal:
```

sudo apt-get --purge remove amule

```

Here is some helpful info from the apt manual:

If you no longer want to use a package, you can remove it from your system using APT. To do this just type: apt-get remove package. For example:

     # apt-get remove gnome-panel
     Reading Package Lists... Done
     Building Dependency Tree... Done
     The following packages will be REMOVED:
       gnome-applets gnome-panel gnome-panel-data gnome-session 
     0 packages upgraded, 0 newly installed, 4 to remove and 1  not upgraded.
     Need to get 0B of archives. After unpacking 14.6MB will be freed.
     Do you want to continue? [Y/n]

As you can see in the above example, APT also takes care of removing packages which depend on the package you have asked to remove. There is no way to remove a package using APT without also removing those packages that depend on it.

Running apt-get as above will cause the packages to be removed but their configuration files, if any, will remain intact on the system. For a complete removal of the package, run:

     # apt-get --purge remove gnome-panel
     Reading Package Lists... Done
     Building Dependency Tree... Done
     The following packages will be REMOVED:
       gnome-applets* gnome-panel* gnome-panel-data* gnome-session* 
     0 packages upgraded, 0 newly installed, 4 to remove and 1  not upgraded.
     Need to get 0B of archives. After unpacking 14.6MB will be freed.
     Do you want to continue? [Y/n]

Note the '*' after the names. This indicates that the configuration files for each of these packages will also be removed.

---

### Post by Phosphoric on 2007-07-29
Thanks for the reply felicity,

did all that and reloaded amule, still get the same error message.:(

Do you need to re-boot in between purging the files and re-loading as you have to with Windows?

I'll try that.

---

### Post by RomeReactor on 2007-07-29
Hi. You don't need to reboot; you probably only need to remove the **.aMule** folder in your home directory before launching aMule again; Open Nautilus (the file browser) on your home directory, press CTRL+H, find the .aMule folder and delete it. Or to do it from the terminal (Applications->Accessories->Terminal):
```
rm -R ~/.aMule
```
Then open aMule again.

---

### Post by Phosphoric on 2007-07-29
Hi RomeReactor,

that tip on deleting the .amule file gave me another idea.   I actually found the hidden amule config file and changed the location of the incoming file.

All is now well.  :)

---

### Post by RomeReactor on 2007-07-29
> **Phosphoric said:**
> I actually found the hidden amule config file and changed the location of the incoming file.

All is now well.  :)

Now *that* is a better solution! Glad you worked it out, though.

---

