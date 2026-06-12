---
title: "how do I defragment in Linux?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Shadowmeph on 2008-02-24
I have downloaded and deleted and downloaded allot of TV episodes and coming from windows I would defrag my HD but I was reading about defrag in Linux and allot of people say that Linux doesn't need to be defraged which kind of plays with my head so is this true that you don't need to defrag Linux?

---

### Post by ruy_lopez on 2008-02-24
It doesn't need defragmenting. Every once in a while it runs a sanity check when you boot.

---

### Post by sanderella on 2008-02-24
Linux has a tiny kernel all in one place, it doesn't need defragging, not never. :KS

---

### Post by ruy_lopez on 2008-02-24
> **sanderella said:**
> Linux has a tiny kernel all in one place, it doesn't need defragging, not never. :KS

Defragmenting has nothing to do with the size of the kernel. Defragmenting relocates files on the hard drive so they aren't scattered everywhere. It prevents the disc read head from having to zip about all over the place.

Linux uses ext3 which places files closer together, reducing the need for defragmenting.

"Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system." [http://en.wikipedia.org/wiki/Defragmentation]("http://en.wikipedia.org/wiki/Defragmentation")

---

### Post by p_quarles on 2008-02-24
Fragmentation is an effect caused by the characteristics of the filesystem you use. The default filesystem in Ubuntu, Ext3, fragments extremely slowly, and is not normally a problem. 

Contrary to what others have said so far, it *does* fragment over time, and can do so more quickly depending on the kind of wear and tear you place on it. For more info, read this:
[http://ubuntuforums.org/showthread.php?t=169551]("http://ubuntuforums.org/showthread.php?t=169551&highlight=pyfragtools")

---

### Post by Arthur Archnix on 2008-02-24
Yeah, it's just one of those things that takes getting used to... like not having an antivirus installed, never watching out for spyware, uninstalling programs and not worrying about bits and pieces left lying around in weird places like a "registry" (something else linux doesn't have).

Edit: interesting link p_quarles. You have to scroll down to the authors comment where jdong notes:
> Note that 90%+ of Linux users will never ever need a defragmenter. The rest, 99% of them will only need it after 1+ year of heavy use. Most people will never need to defragment; Linux does a superb job of maintaining great filesystem performance.

But still, interesting.

---

### Post by mastahkillah666 on 2008-02-24
It depends on the **file system** of your partitions.  If you have used the **ReiserFS** or the **ext3** file systems, then you wouldn't need to defrag your partitions, provided that you have enough free space (that's because these file systems use indexation).

If you used an **ext2** file system, then your partition may be a little bit fragmented (it is not comparable to the FAT 16/32, NTFS file systems fragmentation).  In that case, if you **really want** to defrag your partition, you could use e2defrag or defrag.

**DO NOT, I repeat, DO NOT DEFRAG AN EXT3 OR REISERFS PARTITION !!** There is no **safe way** to defragment these file systems.  You could convert them to ext2 and then do a defrag but then some info stored by ext3 will be lost...

The choice is yours.  If you do want to defrag, **BACKUP YOUR DATA FIRST**.

Hope it helps.
See ya around the forums

P.S. : If you want to view your fragmentation level use :
```
sudo filefrag * 
```

---

### Post by p_quarles on 2008-02-24
> **Arthur Archnix said:**
> Edit: interesting link p_quarles. You have to scroll down to the authors comment where jdong notes:

But still, interesting.
I did read the post, of course. In any case, one of the few cases in which an Ext3 partition will experience significant fragmentation is with extensive multithreaded downloading, e.g. bittorrent.

---

### Post by seventhc on 2008-02-24
@ **mastahkillah666** I have **ext3** and one */boot* partition [B]ReiserFS
[/B]I've never seen that command you put, and out of curiosity would
```
sudo filefrag *
```give any information on this filesystem and is it safe?
b/c I'd like to run it...

---

### Post by Shadowmeph on 2008-02-24
Well this is great News because I used to defrag my Windows system every week or so now this is one ( ok allot more) thing I don't need to worry about :)

---

### Post by mastahkillah666 on 2008-02-24
> **seventhc said:**
> @ **mastahkillah666** I have **ext3** and one */boot* partition [B]ReiserFS
[/B]I've never seen that command you put, and out of curiosity would
```
sudo filefrag *
```give any information on this filesystem and is it safe?
b/c I'd like to run it...

No problem with the command.  It only tells you if your files are fragmented and how many fragments there are.  You can use it without fear.

---

### Post by Duck2006 on 2008-02-24
> **mastahkillah666 said:**
> No problem with the command.  It only tells you if your files are fragmented and how many fragments there are.  You can use it without fear.

Nice command will try it.

---

### Post by asmoore82 on 2008-02-24
> **mastahkillah666 said:**
> **DO NOT, I repeat, DO NOT DEFRAG AN EXT3 OR REISERFS PARTITION !!** There is no **safe way** to defragment these file systems.  You could convert them to ext2 and then do a defrag but then some info stored by ext3 will be lost...

LOL, if it really bothers you, all you have to do is move the files off the drive and then back again;
there can't possibly be *fragmented* files when there are *no* files, right?
and then when you copy them back, they will be placed in a clean, non-fragmented, order.

All that having been said, GNU/Linux system do *not* fragment. Which is, as pointed out earlier, not entirely true.
Linux filesystems do become "non-contiguous" which means that the files are slightly scattered.
But this can only start to happen on a large scale when the filesystem is very close to full;
and even then, there is no drain on filesystem performance. Performance will be infinitely more impacted
by whether or not you use the "noatime" option(which breaks POSIX compliance) or the "writeback" journaling
strategy(which has potential for data loss on power loss) rather than any sort of fragmentation.

---

### Post by mastahkillah666 on 2008-02-24
If, after executing the command I gave, a file has many extends(fragments), in order to defragment the file, simply copy it from on location to another. 8)

---

### Post by mastahkillah666 on 2008-02-24
> **asmoore82 said:**
> LOL, if it really bothers you, all you have to do is move the files off the drive and then back again;
there can't possibly be *fragmented* files when there are *no* files, right?
and then when you copy them back, they will be placed in a clean, non-fragmented, order.


Ooops, I was too slow... ;)

P.S. : As for my warning, I was referring to using an application or command (like defrag).

---

### Post by seventhc on 2008-02-24
> **mastahkillah666 said:**
> No problem with the command.  It only tells you if your files are fragmented and how many fragments there are.  You can use it without fear.
OK thanks, want to see the output of that. :)

---

### Post by Arthur Archnix on 2008-02-24
> **p_quarles said:**
> I did read the post, of course. In any case, one of the few cases in which an Ext3 partition will experience significant fragmentation is with extensive multithreaded downloading, e.g. bittorrent.

Yes, sorry. I didn't mean to imply that you hadn't read it. It was just interesting to me so I quoted it and tossed it in here for those who might not have. Since I usually do a full backup and clean restore about once every six months (funny, that's about the rate of new buntu's isn't it?) it's not something I'll every have to worry about.

---

### Post by ahaslam on 2008-02-24
Linux FSs certainly do fragment & quite significantly given the chance, I had mine up to 78% non-contiguous. Due to issues with ext3 (not frag related), I switched to xfs, here a simple 'xfs_fsr' works wonders. 

;)

---

### Post by Glaxed on 2008-02-24
The purpose of the registry in Windows was to keep important options nice and hidden from users. GConf is Gnome's answer to Windows registry, except it isn't used as a crutch. It's also much, much smaller and friendly to edit.
```
$ gconf-editor
```
Don't run it with sudo, su, gksu, or gksudo because you will then be modifying root-account settings.
:D

---

### Post by asmoore82 on 2008-02-24
> **Glaxed said:**
> The purpose of the registry in Windows was to keep important options nice and hidden from users. GConf is Gnome's answer to Windows registry, except it isn't used as a crutch. It's also much, much smaller and friendly to edit.
```
$ gconf-editor
```
Don't run it with sudo, su, gksu, or gksudo because you will then be modifying root-account settings.
:D

And on a more personal note, the "registry" is a twisted pile of junk data!
Whereas GConf has a foolproof "fallback" system:
1. gconf-editor, edit it "user-friendly" and graphically;
2. gconftool-2, edit it "UNIX-user-friendly" from the command line;
3. It is stored under "$HOME/.gconf" in a directory delimited database of plaintext XML files,
so, if all else fails, grab your favorite text editor and start hacking it.

---

### Post by Glaxed on 2008-02-26
How does the fallback work? If something delete's a bunch of entries (be it you, or something else), how will Gconf recover? -[bad place for question, will look it up]/

---

### Post by asmoore82 on 2008-02-26
> **Glaxed said:**
> How does the fallback work? If something delete's a bunch of entries (be it you, or something else), how will Gconf recover? -[bad place for question, will look it up]/

I meant "fallback" in the sense that if you can't use the gui app `gconf-editor` you can use `gconftool-2`
and failing that, it is stored as plaintext and human readable give or take some XML

Apple is very *close* to the same level of hacker-friendly "practicality" with their plist system:
it can be edited from the command line with `defaults` but unfortunately, the *.plist files aren't human readable.

---

