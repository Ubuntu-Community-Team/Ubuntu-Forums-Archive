---
title: "Mount and NFS file sharing."
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by PerpsTherapy on 2006-04-27
Greetings to all.

I have a question regarding using NFS to share files between two machines, one running Suse 10.0 and the other (this one) running Ubuntu Breezy 5.1. 

I've successfully configured the Ubuntu machine as an NFS server, and the Suse machine is having no problems seeing the home directory of the Ubuntu machine. However, despite having set up the Suse machine as an NFS server (Suse 10.0 has a nice GUI NFS server setup in Yast), I can't successfully mount the Suse home directory on the Ubuntu machine, using the mount command, or entering it into /etc/fstab.

At the command line, I attempt to use the mount command as su:

mount -t nfs 10.1.1.3:/home /mnt/susehome

which does nothing but blink the konsole cursor at me...(i've left it for at least five minutes with no response).

Alternitavely, I've entered the following into my /etc/fstab:

10.1.1.3:/home  /mnt/susehome     nfs     defaults 0 0

which also hangs for ages during bootup doing nothing, at which point I hit Ctrl+C to break it and continue booting. Incidentally, this is the same format as appears in the /etc/fstab of the Suse machine, which can see the Ubuntu machine correctly.

Can anyone out there shed some light on this one? I'm not sure if this is the right area to be posting in (Absolute Beginner Talk), but I've only been using linux for a couple of weeks.

Thanks,

- PerpsTherapy.

---

### Post by jazzmuzik on 2006-04-27
Do you have an /etc/export file?

---

### Post by PerpsTherapy on 2006-04-27
Thanks for the speedy reply jazzmuzik.

Checked my Ubuntu machine, and no, I don't have an /etc/export file. Is this necessary to get NFS happening properly? I setup the Ubuntu machine using this guide...
[http://nfs.sourceforge.net/nfs-howto/server.html]("http://nfs.sourceforge.net/nfs-howto/server.html")

Thanks,

- PerpsTherapy

---

### Post by jazzmuzik on 2006-04-27
When I was running Fedora Linux a year or so ago, the /etc/export file was necessary to tell the system what directory you want to give access to another computer. I'm assumming NFS hasn't changed in that year and this is still the case with Ubuntu. See this thread:

[http://ubuntuforums.org/showthread.php?t=53579&highlight=%2Fetc%2Fexport](http://ubuntuforums.org/showthread.php?t=53579&highlight=%2Fetc%2Fexport)

Just to be clear, /etc/export file goes on the computer that is sharing the files, i.e., the remote computer. It's simple though. Just a one line thing.

The export file contents look like this:

/extra          192.168.5.34(rw)

You specify the directory you want to share (/extra) and who can gain access (192.168.5.35) and the type of access, read/write etc.

And then you mount that nfs share (on the non-remote computer) with the mount command (mount -t nfs ...) or add a line in /etc/fstab to mount automatically each time you boot up:

```
192.168.99.123:/extra  /media/mountpoint  nfs  rsize=8192,wsize=8192,timeo=14,intr
```

192.168.99.123 is the remote computer's ip address, /extra the the directory you want to mount. /media/mountpoint is your local mountpoint and where you will locally access the remote computer's files. nfs is the type of filesystem, an the other stuff is what was suggested during my research on nfs.

---

