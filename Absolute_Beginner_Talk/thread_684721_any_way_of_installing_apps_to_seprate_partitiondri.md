---
title: "any way of installing apps to seprate partition/drive?"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by benji.ijneb on 2008-02-01
hiyo

is there any way of installing apps via synaptic or apt-get to a seperate HD on my pc? (i'm looking for a relatively simple option...)

similaraly, if i were to get an eee pc, would there be any waqy of installing various apps  to an SD card? + How easy is it to install apps on an eee pc?

ta

---

### Post by emarkd on 2008-02-01
Linux doesn't really work like that.  Windows takes the route of keeping most of a program together in one directory, making it easy to move but impossible to share it's stuff with other programs.  Linux puts like files together, so libraries go with libraries, docs go with docs, executables go with executables, etc.  See the attached picture for a decent, but generic representation, but remember that every distribution does things a little differently, so this is not exactly what your Ubuntu's got going on.

You can, however, move your home folder to its own partition if you want to spread things out.  A quick search will reveal lots of information on that.

---

### Post by emarkd on 2008-02-01
Sorry, that last image I uploaded was just the thumbnail.  That's quite useless.  Here's the full version.

---

### Post by benji.ijneb on 2008-02-01
> **emarkd said:**
> Linux doesn't really work like that.  Windows takes the route of keeping most of a program together in one directory, making it easy to move but impossible to share it's stuff with other programs.  Linux puts like files together, so libraries go with libraries, docs go with docs, executables go with executables, etc.  See the attached picture for a decent, but generic representation, but remember that every distribution does things a little differently, so this is not exactly what your Ubuntu's got going on.

You can, however, move your home folder to its own partition if you want to spread things out.  A quick search will reveal lots of information on that.

so, it's not possible to free up space by changing where programes are installed...
what about installing them all to a mounted /opt directory?

---

### Post by emarkd on 2008-02-01
Technically, you can break off practically any directory into it's own partition and just mount it under your root filesystem.  Remember that in Linux, EVERYTHING is a file, so it doesn't really matter how your physical drives/partitions are arranged as long as the filesystem is mounted properly.

---

### Post by benji.ijneb on 2008-02-01
> **emarkd said:**
> Technically, you can break off practically any directory into it's own partition and just mount it under your root filesystem.  Remember that in Linux, EVERYTHING is a file, so it doesn't really matter how your physical drives/partitions are arranged as long as the filesystem is mounted properly.

that's quite useful.......
so if i *were* to get an eee pc, i'd need to get one with more space

is it not possible to compile software from source and choose the install directory. that could do it......

oooh! (now i'm just getting desperate) is there no way of 'merging' the two drives so that ubuntu thinks they are one?
thanks for all your help

---

### Post by emarkd on 2008-02-01
I don't know anything about the eepc, but Linux makes it very easy to share files around the network/internet.  My laptop looks like it has about 1TB of harddrive space when in fact 90% of the files available there are located on my server.  Of course, any files not really local to the laptop are subjected to network lag, transfer speeds, etc.

You can compile software and do that; you can also edit the .deb files that are already compiled and move things around.  You just have to be careful that everything still makes sense when you're done.

---

### Post by benji.ijneb on 2008-02-01
> **emarkd said:**
> I don't know anything about the eepc, but Linux makes it very easy to share files around the network/internet.  My laptop looks like it has about 1TB of harddrive space when in fact 90% of the files available there are located on my server.  Of course, any files not really local to the laptop are subjected to network lag, transfer speeds, etc.

You can compile software and do that; you can also edit the .deb files that are already compiled and move things around.  You just have to be careful that everything still makes sense when you're done.

thanks, very useful
- is there any way of merging the HDs into one?

---

### Post by emarkd on 2008-02-01
Not sure what you mean by merging....  Linux only has one filesystem, so it doesn't matter how my physical drives/locations you're using.  For instance, it doesn't matter what you're doing or where you're going, in Linux everything starts with /

---

### Post by philinux on 2008-02-01
Go to system>admin>system monitor.

Click the file systems tab take a print screen and post it. That way we can see your disk usage etc.

---

### Post by benji.ijneb on 2008-02-01
> **emarkd said:**
> Not sure what you mean by merging....  Linux only has one filesystem, so it doesn't matter how my physical drives/locations you're using.  For instance, it doesn't matter what you're doing or where you're going, in Linux everything starts with /

by merging, i mean take the space from the empty HD, and fool ubuntu into thinking that it is part of the root filesystem, giving it more space.

i could simply put the directorys where apps are installed on the empty HD and then mount them back onto the root filesystem - which directorys are these, and could i do this?

thanks for all the help

---

### Post by emarkd on 2008-02-01
Yes, you can mount that empty drive anywhere, but it will always be its own directory.  You can't "merge" that empty space into /usr, for instance.  You could instead move all of your /usr stuff into the empty drive and then mount the drive at /usr, but you'd want to do that from a Live CD of some sort.

---

### Post by benji.ijneb on 2008-02-01
> **philinux said:**
> Go to system>admin>system monitor.

Click the file systems tab take a print screen and post it. That way we can see your disk usage etc.

sorry, i would, but i dont have it with me at the mo (im working on annother PC)
but basicly, its the root filesystem (10GB) which is pretty full up, and an empty HD with about 10GB on it too.

---

### Post by benji.ijneb on 2008-02-01
> **emarkd said:**
> Yes, you can mount that empty drive anywhere, but it will always be its own directory.  You can't "merge" that empty space into /usr, for instance.  You could instead move all of your /usr stuff into the empty drive and then mount the drive at /usr, but you'd want to do that from a Live CD of some sort.

cool

and /usr is the directory i would want to do that with?
would the ubuntu live cd do? why do i need to use it and how?

this is getting really helpful, thanks...

---

### Post by emarkd on 2008-02-01
That was just a suggestion.  Most people choose to break off the /home directory because that's where all your config stuff is stored and you won't lose it if your main drive crashes.  The best thing to do is to use the Disk Usage Analyzer at Applications > Accessores to see how much space you'd gain by moving /home.  If you're a command line type, check out the 'du' command instead.

Yeah, the Ubuntu Live CD would do it for you.  You'd use gparted to partition and format the new drive, if you needed to, and then copy everything out of /home onto that drive.  Then you'd have to edit your /etc/fstab file to mount the new drive at /home.  That's a topic in itself and you'd be better off doing a search for examples on doing that.

---

### Post by philinux on 2008-02-01
Is your home folder within root. If so how much space is home taking up.

---

### Post by lakris61 on 2008-02-01
You can have a look at LVM and similar methods of merging several storage media. They give opportunities to add and remove, resize and all kinds of stuff. Usually mostly interesting  to multi-user and networked environments.

Most packages though, can accept options to for example place the installed package somewhere else than the default location. Use dpkg on the command line, check the man page for options available.

/Lakris

---

