---
title: "Basic Files and Folders System"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by perito on 2008-03-12
In windows, we have the hard drives (C:\) (D:\) (E:\)...
and windows is usually installed in the C:\  drive,
you can install new programs in other hard drives and arrage your folders and files how ever you want (A drive for games, A drive for music...)

How is the folder system in Ubuntu and Linux?
I know we have the /home folder... but where is it?
Cant I install programs on different partitions?
Im still new, and its so confusing for me right now... I  hope someone can help me with this coz I really wanna learn....

thx

---

### Post by jan quark on 2008-03-12
start here:
[https://help.ubuntu.com/community/LinuxFilesystemsExplained?highlight=%28system%29](https://help.ubuntu.com/community/LinuxFilesystemsExplained?highlight=%28system%29)

---

### Post by zxscooby on 2008-03-12
[https://help.ubuntu.com/community/LinuxFilesystemsExplained?highlight=%28system%29%7C%28file%29](https://help.ubuntu.com/community/LinuxFilesystemsExplained?highlight=%28system%29%7C%28file%29)


linuxcommand.org

---

### Post by Arkenzor on 2008-03-12
Actually, there are two separate questions here:

- First, how does Linux handle multiple partitions?

Unlike in Windows where you have multiple filesystems, one for each partition, in Linux they're all fused into one. What this means is that _all_ your files are contained in the base directory tree (starting with the "/" folder). Then, you can "mount" an external filesystem inside a folder of your tree, and its contents will be accessible there. For example, you may mount your Windows partition in a "/mnt/windows" folder. Then that folder will hold the contents of your partition. It will have subfolders like "/mnt/windows/Program Files", etc.

- For the second section (what's where), you should take a look at [this guide](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html), which explains the basics of the Linux filesystem organization. It's slightly outdated but there haven't really been major changes since then.


EDIT: I've found a few errors in the wiki articles cited above (NTFS _can_ be written to by Linux with the ntfs-3g program, available by default in Ubuntu), I'll see if I can get myself a wiki account and correct them.

---

### Post by PeterJS on 2008-03-12
> **perito said:**
> In windows, we have the hard drives (C:\) (D:\) (E:\)...
and windows is usually installed in the C:\  drive,
you can install new programs in other hard drives and arrage your folders and files how ever you want (A drive for games, A drive for music...)

How is the folder system in Ubuntu and Linux?

According to the [FHS](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
> 
I know we have the /home folder... but where is it?

Well that depends how your system is set up, it could be one of two places. /home/ could be a sub directory named home of the partition mounted at /, or it could be the root of a separate partition that is mounted at /home/

> 
Cant I install programs on different partitions?

Yes and No. You could mount parts of the standard paths, like the entire /usr/ tree (which is what separates /bin/ from /usr/bin/) on separate partitions. But because of interdependency of shared libraries, and things like $PATH, you really really don't want to be moving things out their standard locations.

---

### Post by muteXe on 2008-03-12
Is mounting a folder similar to creating to shortcut?  If i want to play mp3's in ubuntu, i normally have to browse to /media/sda2/documents and settings/user1/my documents/my music (something like that i can't remember exactly).  But could i just permanently mount my "my music" folder so i didnt have to browse down such a long path all of the time?
Cheers,

mute

---

### Post by hyper_ch on 2008-03-12
you can mount only partitions at any location... so if your mp3s are on on sda2 in a subfolders, you can only say where sda2 shall be mounted to...

However you can symlink to the MPs, that would be kind of a shortcut

```

sudo ln -s /path/to/the/files /path/to/where/symlink/shall/be

```

e.g.

```

sudo ln -s "/media/sda2/documents and settings/user1/my documents/my music" /home/USER/Desktop/Music

```

Replace USER with your username and it will put a symlink onto your desktop pointing to your music files.

---

### Post by vishzilla on 2008-03-12
I found a nice [image]("http://bp3.blogger.com/_Vbsj-yhipTw/RvaiatPBPBI/AAAAAAAAABs/yjx3hPlEUNw/s1600/linux_file_structure.jpg") of the filesystem on the internet

---

### Post by muteXe on 2008-03-12
cheers hyper_ch :)

---

### Post by perito on 2008-03-12
@vishzilla  
We cant see the image... can you attach it and upload it here please?
thx

---

### Post by perito on 2008-03-12
ok, after reading everything u linked to... i have question about files.
in windows the extension of the file is the most important thing, .exe .dll ....
what are the most important file types of files in Linux?
Are .deb in linux = .exe in windows?
how does linux know the file type without any extension?

---

### Post by Oldsoldier2003 on 2008-03-12
> **hyper_ch said:**
> [COLOR="DarkRed"]you can mount only partitions at any location[/COLOR]... so if your mp3s are on on sda2 in a subfolders, you can only say where sda2 shall be mounted to...

<snipped>
not true, you can mount folders. try it.
create a new dir in your home

```
mount <some dir i want to see mounted>  <home/me/newdir> -o bind
```

the fstabb entry would look like this is you wanted to make it persistent:

```
/usr/portage/distfiles /home/ftp/distfiles none bind
```
or like this (they are both valid and functionally equivalent)

```
/var/www   /home/username/www   bind   bind   0
```

---

### Post by hyper_ch on 2008-03-12
> **Oldsoldier2003 said:**
> not true, you can mount folders. try it.
create a new dir in your home

```
mount <some dir i want to see mounted>  <home/me/newdir> -o bind
```

the fstabb entry would look like this is you wanted to make it persistent:

```
/usr/portage/distfiles /home/ftp/distfiles none bind
```
or like this (they are both valid and functionally equivalent)

```
/var/www   /home/username/www   bind   bind   0
```

now that's cool... didn't know it ws possible... well, I should have known as you can mount .isos also anywhere you want.

---

### Post by SunnyRabbiera on 2008-03-12
> **perito said:**
> 
Are .deb in linux = .exe in windows?

sorta, .deb's are more like zip archives rather then installer scripts.
most of the dependant files you will see in linux are going to end in .so as files ending in .so are as common as files ending in .dll in windows...
but there are others, .bin .la

Just keep in mind when downloading .deb files from websites sometimes need dependencies, most of the time this is resolved automatically but sometimes you may need more then one installer file.
just use synaptic to install what you need, and if you cant find something in synaptic we can assist you if needed.


as for undertanding how a linux filesystem works its not that hard, typically hard drives are listed as sda or hda
so sda1 can normally be considered our version of C:, but sometimes the hard drive can be listed as hda1 depending
and most of the time cd drives are listed as scd but I have seen others used.
its just finding out how linux listed your system is the hard bit as some list drives differently, but once you know you know...

---

### Post by muteXe on 2008-03-12
i better go read about "fstab" then.
cheers,
mute

---

