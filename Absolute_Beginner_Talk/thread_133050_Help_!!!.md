---
title: "Help !!!"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-02-19
I just installed initng ver 5.2 and now I can't start ubuntu ! I would reinstall but I have to much valueable things. Please Help !

---

### Post by kingsidy on 2006-02-19
you can try login in recovery mode and do a dpkg remove.

---

### Post by xXx 0wn3d xXx on 2006-02-19
[QUOTE=kingsidy]you can try login in recovery mode and do a dpkg remove.[/QUOTE]
great but how ?

---

### Post by kingsidy on 2006-02-19
when it boots, choose recovery mode. it will boot to the command line. from then do a sudo apt-get remove nameofpackage.

---

### Post by xXx 0wn3d xXx on 2006-02-19
What if I re-install the base system without formatting the hd? Would I still have everything. I need to do a report. I need to fix this!

---

### Post by xXx 0wn3d xXx on 2006-02-19
[QUOTE=kingsidy]when it boots, choose recovery mode. it will boot to the command line. from then do a sudo apt-get remove nameofpackage.[/QUOTE]
I don't have that option.

---

### Post by xXx 0wn3d xXx on 2006-02-19
[QUOTE=MasterChief1234]I don't have that option.[/QUOTE]
Please, can someone help ? I'm desperate !

---

### Post by nalmeth on 2006-02-19
at what point does the boot stop? Can you get to GDM? Recovery mode would be picked at the grub menu, so if you can't even see grub things may be difficult.

---

### Post by tadashi on 2006-02-19
If it hangs in xwindows you can try ctrl + alt + backspace.  This should kick you to the command line.  Then you can try to remove the package or at least extract your data.

For the future I find that it is good to have a seperate data drive.  I usually make this about 5 GB but at least 1 GB.  Then if you have to wipe the system you still have your data in a seperate partition.  Also, if you make this partition FAT32 both Linux and Windows can access it.

---

### Post by nalmeth on 2006-02-19
> What if I re-install the base system without formatting the hd?
Perhaps if you created a partition for your home folder, but otherwise it would overwrite everything. Lets explore other options first

---

### Post by xXx 0wn3d xXx on 2006-02-19
[QUOTE=nalmeth]Perhaps if you created a partition for your home folder, but otherwise it would overwrite everything. Lets explore other options first[/QUOTE]
I'm just going to reinstall. At least I learned something from my stupid mistakes.

---

### Post by nalmeth on 2006-02-19
If it is really important we can probably recover your report. Hopefully this doesn't discourage you, I've never had this happen to me. Why don't we try to figure out what happened?

---

### Post by kingsidy on 2006-02-19
you can try booting a live cd and save you data to a flash drive or something like. or burn them if you have a couple of drives.

---

