---
title: "[SOLVED] Problem with write permissions in VirtualBox"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-04-13
Hi,

I've read the other (limited) threads on this issue, but - fearful of losing all permissions - I want to be clear about what I'm doing!  Essentially, I've added Virtual Box using Add/Remove, but each time I attempt to start it I'm told I don't have permission to run it.  Copy/paste of the error below;

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

As I've written, I don't want to THINK I know what I'm doing and find my Gutsy turns into something unpleasant, but would rather admit I DON'T know what I'm doing and ask!  Your advice/help is much appreciated.  Many thanks.

---

### Post by compiledkernel on 2008-04-13
check out this guide -- [http://gaming.gwos.org/doku.php/udsf:virtualbox](http://gaming.gwos.org/doku.php/udsf:virtualbox)

It may give you some better insight.

---

### Post by lswest on 2008-04-13
go to system-->administration-->users and groups
then choose "manage groups"
find "vboxusers" and choose "properties"
then check the box next to your username
logout and back in
Virtualbox will now run.

The thing is virtualbox files are set to be owned by the group vboxusers for security or stability reasons, and so to use it you need to add your user to that group.

---

### Post by sayakb on 2008-04-13
You might also simply edit the VirtualBox launcher and add a "gksudo" in front of the command (ie. run it as root)

---

### Post by lswest on 2008-04-13
> **LinuxIsInnovation said:**
> You might also simply edit the VirtualBox launcher and add a "gksudo" in front of the command (ie. run it as root)

I'm pretty sure that won't work, since you'd be temporarily gaining access to the root group, and not the required vboxusers group.  The solution i posted above works.  I know so, because i use VirtualBox and that process is described in the readme file when you download the binary off sun's servers.

---

### Post by Berean on 2008-04-13
> **lswest said:**
> go to system-->administration-->users and groups
then choose "manage groups"
find "vboxusers" and choose "properties"
then check the box next to your username
logout and back in
Virtualbox will now run.

The thing is virtualbox files are set to be owned by the group vboxusers for security or stability reasons, and so to use it you need to add your user to that group.

lswest,

thanks.  Unfortunately, my name isn't there!  Do I have to add my name?

---

### Post by lswest on 2008-04-13
Are there any names listed in the properties menu of the vboxusers group?

---

### Post by sayakb on 2008-04-13
> **lswest said:**
> I'm pretty sure that won't work, since you'd be temporarily gaining access to the root group, and not the required vboxusers group.  The solution i posted above works.  I know so, because i use VirtualBox and that process is described in the readme file when you download the binary off sun's servers.

 And Im sure that works :). I am running XP on a VBox since almost 6 months with a sudo launcher :D

---

### Post by lswest on 2008-04-13
You can add your user to the group via the terminal with this command:
```
sudo adduser [yourusername] vboxusers
```

and @ LinuxIsInnovation, i'm surprised it works, but then again, root has permissions to anything on the filesystem, but still, it's a risk that may lead to filesystem damage through the executing of a process with more permissions than it should have.

---

### Post by sayakb on 2008-04-13
> **lswest said:**
> @ LinuxIsInnovation, i'm surprised it works, but then again, root has permissions to anything on the filesystem, but still, it's a risk that may lead to filesystem damage through the executing of a process with more permissions than it should have.

 Yes I realize that. I'll implement your method tonite. :)

---

### Post by Berean on 2008-04-13
Thanks to you all.  I logged out and then logged back in and my name appeared.  I'm now installing XP in Virtual Box.  Great!  Many thanks, once again.  Regards,

---

### Post by lswest on 2008-04-13
No problem, glad it works ^^ and LinuxIsInnovation, to each his own, right? ^^

---

