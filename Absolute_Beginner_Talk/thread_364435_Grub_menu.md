---
title: "Grub menu"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2007-02-18
When I boot up my computer the Grub menu pops up (its called grub right?) to chose OSes, the only problem is that there are about 4 Ubuntu Options! Can I get rid of these?

And if I got an external HD would both OSes be able to access it?

And when I made my partitions I know I made the Windows half bigger then 25G but thats what shows up

finally when I boot Windows it always asks to do a disk check will this screw up linux?

---

### Post by g3k0 on 2007-02-18
just comment out the extra options in /boot/grub/menu.lst
they are towards the bottom of the file.  You probably need to use root permissions when you open it

By the way.  Keep a recovery mode option

---

### Post by OBnascar on 2007-02-18
> **spyker3292 said:**
> When I boot up my computer the Grub menu pops up (its called grub right?) to chose OSes, the only problem is that there are about 4 Ubuntu Options! Can I get rid of these?
And if I got an external HD would both OSes be able to access it?
And when I made my partitions I know I made the Windows half bigger then 25G but thats what shows up

To get rid of some of your grub menu options do this in a terminal:
```
sudo gedit /boot/grub/menu.lst
```

The first entry for Ubuntu will be your latest Kernel, you can remove the other three but these have a purpose, you may be sorry someday that you removed them. But removing them will not hurt your booting into Ubuntu if it is done correctly. 

To be safe be sure to do a back up of the menu.lst that you have now before you make the changes in case you make a mistake.

I do not understand the last question about your  partition problem.

---

### Post by spyker3292 on 2007-02-18
> **OBnascar said:**
> 
I do not understand the last question about your  partition problem.

When I made the partitions I made the windows half 50G but in Windows it says the HD is 25G

---

### Post by solar george on 2007-02-18
> just comment out the extra options in /boot/grub/menu.lst

That would work, but you would have to keep redoing it when you install new kernels - you can edit the options that ubuntu uses to write the entries at the top of the file.

```

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
**# howmany=all**

```

Change "howmany" to the number that you want to appear (remember the number that appear will be twice the number listed there, it only count the ordinary version of each kernel - not the recovery mode.)

If you set howmany to 1 you will only see the newest kernel and the recovery option.

Once you have finished editing type the following into a terminal.
```
sudo update-grub
```

This will update the menu file according to your options.

---

### Post by spyker3292 on 2007-02-18
> **solar george said:**
> 

```

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
**# howmany=all**

```



Where do I find that part?

---

### Post by OBnascar on 2007-02-18
> **spyker3292 said:**
> When I made the partitions I made the windows half 50G but in Windows it says the HD is 25G

try this command:
```
sudo df -h
```

This will show you what Linux thinks it is.

---

### Post by solar george on 2007-02-18
> Where do I find that part?

Just above the actual kernel list in section marked,
```
##Begin Automagic Kernel List
```

Around Line 100 in my config.

---

### Post by spyker3292 on 2007-02-18
> **OBnascar said:**
> try this command:
```
sudo df -h
```

This will show you what Linux thinks it is.

... I must of screwed up it thinks the Linux side is 50! Can I fix this, I guess I don't care if it doesnt work

---

### Post by spyker3292 on 2007-02-18
> **solar george said:**
> Just above the actual kernel list in section marked,
```
##Begin Automagic Kernel List
```

Around Line 100 in my config.

Don't see it...

---

### Post by spyker3292 on 2007-02-18
In the GRUB menu there is a box with selections.....

About 3- Ubuntu, kernal ##########

About 3- Ubuntu, kernal ########## (recovery)

Ubuntu, mem83 (or something like that)

Other Operating systems

Windows XP Home

---

### Post by OBnascar on 2007-02-18
> **spyker3292 said:**
> ... I must of screwed up it thinks the Linux side is 50! Can I fix this, I guess I don't care if it doesnt work

Yes you can resize your partitions with the Gparted Live CD, but be sure to read the documentations first if you have never used Gparted before. Just take your time.......and do your home work !

---

### Post by mcduck on 2007-02-18
you could just as well uninstall the old kernel versions with Synaptic. Why keep them wasting disk space if you don't need them (and using them is kind of hard anyway if you remove them from Grub menu)..

Uninstalling old kernel packages will automatically remove their entries from Grub menu.

---

### Post by OBnascar on 2007-02-18
> **mcduck said:**
> you could just as well uninstall the old kernel versions with Synaptic. Why keep them wasting disk space if you don't need them (and using them is kind of hard anyway if you remove them from Grub menu)..

Uninstalling old kernel packages will automatically remove their entries from Grub menu.

That is a very good tip mcduck.......thanks !

---

### Post by pebo on 2007-02-18
> **spyker3292 said:**
> When I made the partitions I made the windows half 50G but in Windows it says the HD is 25G

The reason windows thinks the HD is 25G is that normally windows cannot read linux filesystems...so don't worry about it :)

---

### Post by CaveRat on 2007-02-18
> **pebo said:**
> The reason windows thinks the HD is 25G is that normally windows cannot read linux filesystems...so don't worry about it :)

That's unfortunately exactly right. Windows is like the bully on the play ground. It does not play with Linux. This is one of many reasons why Linux is a much better OS. Windows does not recognize Linux Partitions. Windows thinks it is the only OS installed on a drive.

---

