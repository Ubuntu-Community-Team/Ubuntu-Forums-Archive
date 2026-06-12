---
title: "Why do files get copied in a seemingly random order?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by potion on 2007-12-17
Just something I've been wondering since I made the switch to Ubuntu. In Windows, if I copy a directory from one place to another, it'll copy the files in sequence. But in Ubuntu, it skips around, seemingly at random. Is this a characteristic of the ext3 filesystem, or is there some other reason? I was reading about ext3 [here]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting"), and it talks about how scattering files all over the hard drive prevents fragmentation. But isn't it enough to leave some space between the files, or is it also important to mix up the sequence?

I'm mostly asking because I'm curious, but every once in a while it causes problems. For example, when I load music onto my iPod using gtkpod, I have to do it a directory at a time, or it'll copy the songs in the random order in which they appear on the hard drive.

Is there an easy way to force a sequential copy in Ubuntu? Or is this something I should stop worrying about and learn to love?

Thanks for any enlightenment you can give me.

---

### Post by Severun on 2007-12-18
I believe it works this way (I may be wrong, I'm a bit rusty on my fs internals):

In Windoze it sorts and does who knows what before it copies.  Have you ever seen "Preparing to copy" when trying to copy a large amount of data in Windoze?  It's sorting and massaging and pinching and tickling your files before it copies them.

In *nix land, we have what we call inodes in a filesystem.  When you create a file it gets an inode, then it assigns your file name, associates the file data, etc. with the inode you got allocated when you created the file.  When you delete files it frees up the inodes and marks them as available, after awhile they get assigned and re-assigned in no particular order which is why when you do things that do not sort first, the order appears random.

In *nix land, we are already sufficiently massaged, pinched and tickled so we just grab the list of inodes in a given directory and copy them (it's faster than grabbing the filenames and then sorting them before copying)

If you want to copy them in order you could do something like:

for i in `ls * | sort`
do
cp -v $i /somedestinationdir
done

I don't think you even need the |sort as ls prints sorted output.

---

### Post by nowshining on 2007-12-18
Severun ur inodes info. is sort of right, actually EXT2 does that with the marking as available. However in the EXT3 filesystem it overwrites them with zeroes and in a EXT3 fileystem file recovery is not an easy task, u must grep for them and all kinds of terminal/cli stuff to find it if u have any of the contents of the file left at all..

---

### Post by potion on 2007-12-20
Thanks very much for the explanation. I think I can get my head around most of that. :)

---

### Post by capink on 2007-12-20
To rectify this problem on my mp3 I use a program called fatsort. It is present in the repositories. After copying the files do this:

```
sudo umount /mount/point/of/your/mp3
```

```
sudo fatsort /mount/point/of/your/mp3
```

You can look up the mount point of your mp3 by typing:

```
cat /etc/mtab
```

---

