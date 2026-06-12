---
title: "Install Ubuntu on PPC, But First Need To Rescue Data"
date: 2007-08-13
forum: Apple PPC Users
---

### Post by chrisfisehr on 2007-08-13
I have a old iMac G3 Graphite (PPC) with OS-X 10.2 on it.  I recently got the feared folder with a blinking question mark at start up. Apparently, the Mas OS system folder is lost or corrupt.  I really don't care about losing Mac OS-X, and I actually see this an an opportunity to install Ubuntu on another computer I own.  The only problem is that there is data on the drive that i really need.

I am looking for a live CD that is PPC compatible.   I have checked with Fedora, Knoppix, and UBCD4Win with no luck. Does anyone know of other live CD distributions that are PPC compatible??

Thanks!

---

### Post by stmiller on 2007-08-14
Ubuntu is the only one with a live PowerPC CD that goes to a graphical desktop. All others are text based, which could do the job if you are Linux savvy. (Gentoo, Debian, etc.)

Check out the 'where to download PowerPC' sticky to find the Ubuntu Live PowerPC CD.

---

### Post by chrisfisehr on 2007-08-14
I can get the Ubuntu Edgy Live CD started up no problem. However, I cannot figure out how to access the Mac OSX partition. As best I can tell, there is no way to do this through the Ubuntu GUI.  I was hoping that someone might know of a Linux Live CD or a bootable Systems Admin Utility that includes tools for data rescue.  Something like UBCD4WIN, but for Mac. Any ideas? Thanks!

---

### Post by BryannMelvin on 2007-08-17
If the data is REALLY important...it might be worth buying another HD and Firewire case. Install the OS Ubuntu or other on the new HD and then go from there to try and recover your data.

---

### Post by chrisfisehr on 2007-08-18
OK. I appreciate your input. I will consider that. I am still surprised that there isn't a bootable utility that can rescue data in the Mac OS-X. I will keep looking and post if I find something.

---

### Post by pxwpxw on 2007-08-19
> **chrisfisehr said:**
> OK. I appreciate your input. I will consider that. I am still surprised that there isn't a bootable utility that can rescue data in the Mac OS-X. I will keep looking and post if I find something.

With the ubuntu CD running, it should be relatively easy to mount your MacOSX partition,  provided it is still intact, for read access, or to copy stuff to a mounted external disk (e.g. USB flash sticks can do up to 8GB). You may have to do some of it using a command line terminal, but the capability is there. Degree of difficulty depends on the volume of data and what you want to do with it.

---

### Post by 3rdalbum on 2007-08-19
I no longer have access to an Ubuntu PowerPC machine, so this information may be incorrect. It won't hurt to try it, but you need an internet connection as we'll be pulling down some packages.

1. Start up the Ubuntu Live CD.

2. Go into System > Administration > Software Sources (it might be called Software Properties) and enable all the repositories listed.

3. Click "Close". When it asks you if you want to reload the package list, say Yes (or Ok).

4. Go into Synaptic and install the "hfsutils" and "hfsplus" packages.

5. Go into the terminal (Applications > Accessories > Terminal)

6. Type:

```
sudo fdisk -l
```

When you hit Return, it will show you a list of volumes and their corresponding device files. The "device files" are in the left column I believe, and they look something like "/dev/hda1" and stuff like that.

7. Find the one that corresponds to your Mac OS X partition. The size listed will help, and the partition type will most likely be "HFS+".

8. Plug in a flash drive, external hard disk or zip disk, and wait until it mounts the drive.

9. In the terminal, type:

```

sudo su
hpmount -r whateveryourdevicefileis
```

**Instead of "whateveryourdevicefileis", you would actually put the device file path that you found out in step 7** - for instance, /dev/hda6.

10. If I've correctly guided you up to this point, you will see some sort of message telling you some information about the disk.

11. Now you have to use the terminal to navigate your Mac OS X partition. Here are the commands:

hpls - "Lists" the contents of the directory that you are currently in. You typically use this after you've used hpcd, so you know what is in the directory you've moved into.
hpcd - Changes the current directory to whatever you specify in quotes afterward - for instance, if you were in a directory that contains a folder called Cool Stuff:

```
hpcd "Cool Stuff"
```

Or you can type:

```
hpcd ../
```

(that's two fullstops and a slash) to move back a directory - for instance, if you were in the Extensions folder, and you wanted to get back up to the System Folder, that is what you would do.

hpcopy - copies a file from the HFS partition to somewhere that you specify. You must give the file name and then the path to copy to, e.g:

```
hpcopy "Annual Report.doc" /media/disk/
```

The file "Annual Report.doc" is in the current directory of your HFS disk, and /media/disk is the path to your flash drive.

hpumount - Use it just by itself when you have finished working with your HFS disk.

---------
Yes, I'm aware that this is going to feel horrible for someone who might not have used a command-line before, but it's not as hard as it sounds, and it may be the simplest way, and it's the only way I can actually remember.

---

### Post by chrisfisehr on 2007-08-21
> **3rdalbum said:**
> I no longer have access to an Ubuntu PowerPC machine, so this information may be incorrect. It won't hurt to try it, but you need an internet connection as we'll be pulling down some packages.

1. Start up the Ubuntu Live CD.

2. Go into System > Administration > Software Sources (it might be called Software Properties) and enable all the repositories listed.

3. Click "Close". When it asks you if you want to reload the package list, say Yes (or Ok).

4. Go into Synaptic and install the "hfsutils" and "hfsplus" packages.

5. Go into the terminal (Applications > Accessories > Terminal)

6. Type:

```
sudo fdisk -l
```

When you hit Return, it will show you a list of volumes and their corresponding device files. The "device files" are in the left column I believe, and they look something like "/dev/hda1" and stuff like that.

7. Find the one that corresponds to your Mac OS X partition. The size listed will help, and the partition type will most likely be "HFS+".

8. Plug in a flash drive, external hard disk or zip disk, and wait until it mounts the drive.

9. In the terminal, type:

```

sudo su
hpmount -r whateveryourdevicefileis
```

**Instead of "whateveryourdevicefileis", you would actually put the device file path that you found out in step 7** - for instance, /dev/hda6.

10. If I've correctly guided you up to this point, you will see some sort of message telling you some information about the disk.

11. Now you have to use the terminal to navigate your Mac OS X partition. Here are the commands:

hpls - "Lists" the contents of the directory that you are currently in. You typically use this after you've used hpcd, so you know what is in the directory you've moved into.
hpcd - Changes the current directory to whatever you specify in quotes afterward - for instance, if you were in a directory that contains a folder called Cool Stuff:

```
hpcd "Cool Stuff"
```

Or you can type:

```
hpcd ../
```

(that's two fullstops and a slash) to move back a directory - for instance, if you were in the Extensions folder, and you wanted to get back up to the System Folder, that is what you would do.

hpcopy - copies a file from the HFS partition to somewhere that you specify. You must give the file name and then the path to copy to, e.g:

```
hpcopy "Annual Report.doc" /media/disk/
```

The file "Annual Report.doc" is in the current directory of your HFS disk, and /media/disk is the path to your flash drive.

hpumount - Use it just by itself when you have finished working with your HFS disk.

---------
Yes, I'm aware that this is going to feel horrible for someone who might not have used a command-line before, but it's not as hard as it sounds, and it may be the simplest way, and it's the only way I can actually remember.

Thanks so much for taking time to type all this up! I will definitely give this a try.  I do have a command line phobia. Perhaps this will help me get over it :-) .... hopefully this works b/c I really want to install Ubuntu on this computer, but can't until I rescue this data.

---

