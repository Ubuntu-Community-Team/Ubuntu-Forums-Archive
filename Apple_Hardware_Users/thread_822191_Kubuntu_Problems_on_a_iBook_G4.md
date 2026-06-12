---
title: "Kubuntu Problems on a iBook G4"
date: 2008-06-08
forum: Apple Hardware Users
---

### Post by ivanpk on 2008-06-08
Hi all,
I recently installed Kubuntu on my iBook G4,
I'm having troubles with my trackpad speed, it's incredebly slow. I heard to edit my xcorg.conf file. I followwed the steps found in a different thread with editing it, i pasted the changes, and clicked 'ctrl-x' and then y to save it, but it seems that it didn't save or work, because nothing changed with the speed :[
I've attached a output of my file.
I'm also having trouble installing programs, on 'add or remove programs' for example, Firefox is greyed out. I'm used to just double clicking Apps like on a Mac, so I downloaded firefox online and extracted the files, but I don't know how to compile them.
Another thing, how can I get my Airport card to work? I'm currently tethered to an ethernet cable.... :[
Could anybody help me?
Thanks A TON!

Ivan

---

### Post by Scientia on 2008-06-08
Try changing pointer speed in System>Preferences>Mouse. For airport you'll have to configure your xorg.conf too. Is your iBook a PowerPC or an Intel?

---

### Post by mchladek on 2008-06-08
If it didn't save, it's a good chance you weren't editing the file as root.  Before making changes, back up your working xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Now, to edit your xorg.conf file, execute the following:

```
sudo nano /etc/X11/xorg.conf
```

Make the appropriate changes, ctrl+x to exit, press y to save.

Or you can try the graphical approach scientia recommended.  To get wireless working, check out the [PowerPC Wiki](https://wiki.ubuntu.com/PowerPCFAQ).  I've always been successful with those instructions.  Finally, to get Firefox try using Adept (I think that's the Kubuntu package manager) which should be under System in the KMenu.  Sometimes the Add/Remove Programs does not handle dependencies very well.

---

