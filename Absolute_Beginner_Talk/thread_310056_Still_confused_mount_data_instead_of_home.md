---
title: "Still confused: mount /data instead of /home"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-11-30
Hi,

sorry to start a new thread on this but I'm still very confused after years of Windows. I will dualboot XP and Ubuntu and want a common separate partition for documents, emails and internet bookmarks so that these are accessible to both XP and Ubuntu. I definitely not want to mount the whole /home filesystem on this separate partition because I don't want Ubuntu user's configuration files on it. I only want documents, emails etc. On the XP side this is easily achieved by moving "my documents" folder on the selected partition. Now in Linux I'm confused. If I mount a /data partition during the installation process, will for example OpenOffice documents automatically be saved under /data or will I have to manually select /data each time I want to save a documents?? My real target is as in XP: when you move "My documents" folder, all programs automatically saves documents in the new location. I'd just to the same for Linux but without moving the whole /home since I don't want user's configuration file of Linux to be on my documents.

PS: This is for a single user system.

Thanks

---

### Post by spin2cool on 2006-11-30
Most apps will default to your home directory.  However, it's very easy to make links in your home directory to your documents directory, etc.

For example, if your shared partition is mounted as /media/data, and your main documents folder is on that partition, you could do the following:

ln -s /media/data/documents /home/documents

That will create a link to your documents folder that's easily accessible.

---

### Post by kilou on 2006-11-30
What is the purpose of the "/media" prefix? Is it not possible to directly mount the shared partition as /documents?

---

### Post by compmodder26 on 2006-11-30
You can mount it as whatever you like.

---

### Post by kilou on 2006-11-30
What if I simply mount the shared partition as /home/documents directly?? Do I still need to create links?

---

### Post by kilou on 2006-11-30
@spin2cool
I try to understand the command you propose:
ln -s /media/data/documents /home/documents

If I read this well it is a symbolic link. As far as I could understand (my newbie brain is VERY limited) it means that /media/data/documents will be linked to /home/documents but those documents that are or were already in /home/documents won't be moved??? Is that right??

---

### Post by CatKiller on 2006-11-30
> **kilou said:**
> What if I simply mount the shared partition as /home/documents directly?? Do I still need to create links?

Using sub-directories of /mnt or /media is traditional, that's all.

> **kilou said:**
> @spin2cool
I try to understand the command you propose:
ln -s /media/data/documents /home/documents

If I read this well it is a symbolic link. As far as I could understand (my newbie brain is VERY limited) it means that /media/data/documents will be linked to /home/documents but those documents that are or were already in /home/documents won't be moved??? Is that right??

I don't think you could have a directory called /home/documents and a link called /home/documents at the same time.

The link will behave exactly like a directory though.

---

### Post by kilou on 2006-11-30
So if I type:
ln -s /media/data/documents /home/documents

all documents will be saved in /media/data/documents only....and not in /home/documents as well? I don't want this link to act as a copy, I really want documents only on the shared drive and no more in /home document.

If this is so, can this command be used if Ubuntu is already installed (i.e. if /home/documents is not empty)? Will this efficiently move (and not copy!) the files from /home/documents to the shared drive?

Sorry for all these questions :oops:

---

### Post by bodhi.zazen on 2006-11-30
Just a thought.

/home/user_name contains two types of information. configuration/preferences and data.

IMO I prefer a /data partition over a /home partition.

I back up and share /data and some system configuration files in /data (background images, xmms skins, etc) in /data

The configuration files do not need backup and if you run multiple distros, as I do, the configuration files in /home/user_name can conflict.

So a potential (easy) solution: Just create a shared /data partition and move you data out of /home.

I personally have a data partition: /mnt/Zen

Fstab: /dev/sda14 /mnt/Zen ext3 auto,users,exec 0 0

Now, make a link in /home/bodhi (cd ~):

ln -s /mnt/Zen Zen

ln -s /mnt/Zen/documents documents

ln -s /mnt/Zen/music music

ln -s /nmt/Zen/bin bin

    for the occasional bash or python....


ln -s /mnt/Zen/src src

    for source code I download and ./configure make checkinstall


ln -s /mnt/Zen/downloads downloads

Add as many links as you like. Just as good as the "real thing" in /home/user_name, just all on a separate partition. If I re-install Ubuntu, just re-create the links in home.

Viola

---

### Post by CatKiller on 2006-11-30
> **kilou said:**
> So if I type:
ln -s /media/data/documents /home/documents

all documents will be saved in /media/data/documents only....and not in /home/documents as well? I don't want this link to act as a copy, I really want documents only on the shared drive and no more in /home document.

If you use that command, /media/data/documents and /home/documents will be more-or-less indistinguishable as far as any programs are concerned. Saving in one is the same as saving in the other. Think of it as a box with two holes in - it doesn't matter which hole you put stuff in, it still ends up in the box.

> If this is so, can this command be used if Ubuntu is already installed (i.e. if /home/documents is not empty)? Will this efficiently move (and not copy!) the files from /home/documents to the shared drive?

If /home/documents already exists, then it won't let you make the link, as I understand it. There's no reason why you couldn't copy the contents of /home/documents to /media/data/documents first, then delete (or temporarily rename) the /home/documents directory, and then make the link, should you wish. That's what I'd do, just so I could make sure the documents were really there.

It doesn't really matter. Mount your partition wherever would be convenient to you. And if you later find that you'd like it to be mounted somewhere else instead, you can move the mount point. If you later find that you'd like it to be mounted somewhere else as well, you can make a link.

With all this talk about links though, it's probably worth pointing out that the FAT filesystem doesn't support links. You can't make a link on a FAT partition, whether it's to the same partition or a different one.

You can still make links on a more sensible filesystem to a FAT partition though.

> Sorry for all these questions :oops:

It's the way you find stuff out. Generally I think people need to read quite a lot, and ask quite a lot, to get the subject from a few perspectives, and then suddenly it clicks and they're like, "of course! **Now** I understand." :D

---

### Post by aysiu on 2006-11-30
Thought I'd weigh in on this. I, too, don't like saving configuration files (except my Firefox, Rhythmbox, and Thunderbird settings), so I use a separate data partition. I mount mine at /documents and then symlink the subfolders into my home directory.

For example, I link /documents/pictures to /home/*username*/pictures (also known as ~/pictures) and I link /documents/music to ~/music.

That way, they appear in my /home/*username* as music and pictures, but they're *really* located on a separate partition mounted at /documents.

Does that make sense?

---

### Post by po0f on 2006-11-30
All this talk of creating separate partitions, symlinking like crazy, etc over-complicates things greatly.  The idea of a "data" partition is a good idea (I personally use it myself), but IMO there is no need to go willy-nilly with all the symlinks.  For instance:
```
[FONT="Courier New"]/storage/..
  audio/
  backups/
    etc/
    home/
    projects/
  disk_images/
  images/
  roms/
  video/[/FONT]
```

All of the folders under /storage are world-readable, except backups (and lost+found, but whatever...).  Instead of the symlinks,  I instead create bookmarks in Nautilus for most of these places, for easy access.

[EDIT]

As an added bonus, Nautilus' bookmarks show up in GNOME's open file dialog.  :)

---

### Post by kilou on 2006-11-30
> **CatKiller said:**
> Generally I think people need to read quite a lot, and ask quite a lot, to get the subject from a few perspectives, and then suddenly it clicks and they're like, "of course! **Now** I understand." :D

I probably still don't have the big "click" now but I start to understand things much better now and I have plenty information here to look into it further! Thanks for all your kind replies!

---

