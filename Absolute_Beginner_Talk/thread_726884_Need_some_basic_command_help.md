---
title: "Need some basic command help"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Arcor on 2008-03-17
I've looked and looked, but i can't seem to find anything that tells me how to do this.

Basically, Ubuntu is installed on a partition, Windows on a spereate one, and then a large partition for them both to share files.

I've downloaded Phun, a physics sandbox program, and i'm tryign to run it. Doubleclicking isn't doing anything, so i'm tryign to run it through a command in the terminal... only... i don't know how to change partitions in Terminal.

When i start it, it places me at the desktop in my home directory, but i don't know how i would go about changing it to MySharedPartition/Applications/Phun. as opposed to MyLinuxPartition/root/home/Arcor/Desktop or whatever it's currently at.

Linux is confusing the hell out of me atm. It's taking so much more effort to simply run an executable file. :S

---

### Post by NightwishFan on 2008-03-17
```
cd /path/to/directory/
```
To change directory terminal uses.

To move a file a gui method is sufficient.

---

### Post by Ub1476 on 2008-03-17
Have you checked if Phun is in the repos? Search for it in System>Administration>Synaptic packagemanager.

If it's not, what's the filename of the phun file (entire filename)?

---

### Post by Calmor on 2008-03-17
Your first problem - getting to the other disk - is relatively easy.  Assuming the disk is mounted, by default it should appear in the /media folder.  My shared FAT32 partition mounts at /media/disk.  If you cd into that folder, you should see everything.  Note that 'disk' should be the label of your drive, if it has no label it will default to disk.  Alternatively, you can go to Places -> Computer to see all of the available devices (and mount them)

The launching of the file may be a different story.  If you downloaded the Windows version, it won't run in Linux (except maybe under WINE).  There is a Linux version out - try searching the Synaptic Package Manager.  Until you're more comfortable with the way things work, this is probably your best bet for installing any new software.

---

### Post by Arcor on 2008-03-18
Thanks for the responses guys, i did make sure to get the Linux version, which is why i was so surprised that simply doubleclicking it wouldn't work.

I didn't think it would be under the Package Manager, which is why i went ahewad and grabbed it from the site.
It comes with a readme saying something about pointing Linux to the libraries, which i didn't really understand.

Also, how would i go about compiling the source? I found another application i wanna use under Linux (Zsnes, SNES Emulator.) But it's not available as a Binary for Linux, only as Source.

Thanks in advance :)

---

### Post by kpkeerthi on 2008-03-18
> **Arcor said:**
> I found another application i wanna use under Linux (Zsnes, SNES Emulator.) But it's not available as a Binary for Linux, only as Source.

Thanks in advance :)
Both are available in repository. 
[http://packages.ubuntu.com/gutsy/zsnes](http://packages.ubuntu.com/gutsy/zsnes)
[http://packages.ubuntu.com/gutsy/zsnes](http://packages.ubuntu.com/gutsy/zsnes)

You need to enable universe and multiverse repos under System -> Admin -> Software sources.

---

### Post by kpkeerthi on 2008-03-18
> **Arcor said:**
> Also, how would i go about compiling the source? 

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by 3rdalbum on 2008-03-18
Get the package "nautilus-gksu" from Synaptic Package Manager. Log out and log back in, and you'll find a new item in your contextual menu called "Open in terminal". This will open the selected/current folder in the terminal, so all you'll need to do is type:

```
./phun
```

And then hopefully it will tell you what package or library you're missing, because Phun should just load with a double-click.

---

### Post by Arcor on 2008-03-18
Once again, thanks for the help guys. Ubuntu is quite confusing and intimidating for a newbie like myself.
Cheers :D

---

### Post by hyper_ch on 2008-03-18
> **Arcor said:**
> Once again, thanks for the help guys. Ubuntu is quite confusing and intimidating for a newbie like myself.
Cheers :D
It's not confusing... you're just not used to the way it's done in linux ;) those are two different things ;)

---

