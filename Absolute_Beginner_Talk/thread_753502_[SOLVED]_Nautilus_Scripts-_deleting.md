---
title: "[SOLVED] Nautilus Scripts- deleting"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by carterrocks on 2008-04-12
So in  an attempt to mount iso images by just right clicking I installed, if that's the right word a Nautilus Script which mounts iso images.  Nowz not only did it not work but i also have no idea how to get rid of it.  It's really bothering me.  Anyone tell me how to delete it?

---

### Post by Helgiks on 2008-04-12
It is in ~/.gnome2/nautilus-scripts
There you can find the script and delete it.
I made a script for that once, have been using it for a while, you can try that one if you want, just open the file and replace what is there with the following,

```
#!/bin/bash
for ISO in `echo $*`
	do
		root=`gksudo -u root -k -m "Enter your root password." /bin/echo "Enter your root password."`
 		sudo mkdir -p /media/ISO
 		sudo mount -o loop -t iso9660 $ISO /media/ISO 
 		nautilus /media/ISO
	done
done
exit0
```

This one should work.
Make the script executable, than just rightclick on ISO file and run the script.

Here is another script for unmounting, if your interested.

```
#!/bin/bash
for ISO in `echo $*`
	do
		root=`gksudo -u root -k -m "Enter your root password." /bin/echo "Enter your root password."`
		sudo umount $ISO
 		rmdir /media/ISO
	done
done
exit0
```

---

### Post by fdesign on 2008-04-12
I use gmountiso

It's in the repos, just search for it. It will show up in the System menu after installed.

---

### Post by carterrocks on 2008-04-13
> **Helgiks said:**
> It is in ~/.gnome2/nautilus-scripts
There you can find the script and delete it.
I made a script for that once, have been using it for a while, you can try that one if you want, just open the file and replace what is there with the following,

```
#!/bin/bash
for ISO in `echo $*`
	do
		root=`gksudo -u root -k -m "Enter your root password." /bin/echo "Enter your root password."`
 		sudo mkdir -p /media/ISO
 		sudo mount -o loop -t iso9660 $ISO /media/ISO 
 		nautilus /media/ISO
	done
done
exit0
```

This one should work.
Make the script executable, than just rightclick on ISO file and run the script.

Here is another script for unmounting, if your interested.

```
#!/bin/bash
for ISO in `echo $*`
	do
		root=`gksudo -u root -k -m "Enter your root password." /bin/echo "Enter your root password."`
		sudo umount $ISO
 		rmdir /media/ISO
	done
done
exit0
```

Okay this might sound like a stupid question but where can I find .gnome2?

---

### Post by joshrobinson on 2008-04-13
in your home folder, but its hidden, so you have to go to view > show hidden files, or ctrl+h

---

