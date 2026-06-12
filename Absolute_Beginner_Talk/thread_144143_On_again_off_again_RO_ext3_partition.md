---
title: "On again off again RO ext3 partition"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Placid on 2006-03-13
I am a linux n00b but enjoying my experience away from Windows so far. I am having an issue where a new drive I have added into my machine which is coming up read only a lot of the time.

The entry in /etc/fstab looks like this:

/dev/sdd1       /media/stuff      ext3    defaults 0 2

Weird thing is that if I Browse the disk via the Disks tool then I can write to the drive but otherwise the option to create a new folder is greyed out and other apps complain about not being able to write.

I tried changing the owner of /media/stuff from root to my own id but that doesn't seem to have fixed the problem. Any thoughts?

Cheers

---

### Post by derelict on 2006-03-13
You can type "mount" without any arguments to see how that drive is mounted (if it's read-write or read-only). The "defaults" option includes "rw", so it may be a permission/ownership problem.

Try:
sudo chown -R yourusername /media/stuff
sudo chmod -R 700 /media/stuff

The 700 above means that the owner (which you changed to yourself on the first command) can do everything with the files in /media/stuff and no one else can do anything; are you familiar with file permissions being expressed this way?  It's the same as "sudo chmod -R u=rwx /media/stuff", more info: [http://www.computerhope.com/unix/uchmod.htm](http://www.computerhope.com/unix/uchmod.htm)

---

### Post by Placid on 2006-03-13
That worked a treat, thanks!

I've had vague experience with linux over the years so have some familiarity with ownership and file modes. Biggest issue is understanding the appropriate action to take with making a mess of access rights.

Cheers

---

