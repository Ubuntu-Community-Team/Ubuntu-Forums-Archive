---
title: "&quot;Mapping&quot; network storage"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by timpaton on 2008-03-25
I have a ClarkConnect server/firewall/router box sitting in a cupboard minding its own business (CC is a pre-configured Linux distro, designed to be used as a firewall plus a bunch of other stuff. For the purposes of this post, consider it a NAS of sorts).

In Windows, I used to find the server's shared drive and map it as drive "S:", then the computer would pretend that it was a local drive. Each computer has the same S-drive, and that's where all the documents live.

Now I'm using Ubuntu (7.10, installed from the factory on my Acer Aspire 4315 laptop... very nice!). I want the same functionality. I've played with various Linuces for more than a decade but I'm still a noob.

I can find the server's shared drive using the "connect to server" function in the "places" menu, and connect to it. Now in Nautilus, I have an entry for the server's drive. So far so good.

But it doesn't work like a local drive.

For starters, GIMP won't even look at a file that's stored on the server; I have to copy it to my local drive (home directory), then work on it, then put it back when finished.

The "Save As" and "Open File" dialogs of most applications can't see the shared server drive; it doesn't seem to be mounted anywhere on my local filesystem, and that's all they can see. Is that true? I thought everything was considered as a "file" somewhere on the filesystem... but I can't see the shared drive anywhere except in Nautilus (or in some applications that use Nautilus or a Nautilus-like file handling system).

I guess what I'd like is to just have the shared drive mounted in my home directory, as ~/server or something like that, and for all applications to treat the contents as if they were local files.

Any ideas?

tim

---

### Post by peitschie on 2008-03-25
Hi,

You are wanting to know how to "mount" a network share.  See here: [https://help.ubuntu.com/community/SettingUpSamba#head-d0cf07ad854d6a463aa1ba9345600732832d47ef](https://help.ubuntu.com/community/SettingUpSamba#head-d0cf07ad854d6a463aa1ba9345600732832d47ef) 
This will walk you through setting up a share that is mounted on boot by Linux, so it will function very similar to your mapped 'S:' drives.

Oh, to make gimp open things on the networekd drives without that hassle, run the following command in a terminal:
```

sudo apt-get install gimp-gnomevfs

```

---

