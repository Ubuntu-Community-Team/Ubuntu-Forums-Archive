---
title: "Resize ext3 partition"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by jriff on 2005-11-29
Hi All!

I am running Ubuntu Breezy and I need to resize the partition that my installation is running on. First I installed gparted but this program can't manipulate a mounted partition. Then I tried to boot the Ubuntu installation cd with "rescue" and start parted. This didn't work either since the partition I am trying to resize is mounted in rescue mode also. 

What to do?

- Jacob

BTW. Ubuntu and Linux is great!! I am SO glad I installed this as my primary system on my new T43p :D

---

### Post by startailpro on 2005-11-29
Sadly u might have reinstall the whole thing. Its really the same as windows u could never resize the main partion it was using so i would of thought that includes linux as well as but comparison to windows is a bad thing. Linux might a programme hidden in the world wide web and some may know just not me. DAMM.

---

### Post by gingermark on 2005-11-29
I believe you can use a Live CD to do this. I'm not 100% on the ins and outs of it, but by booting off a Live CD your primary drive is then available to partition. This is the way I'd investigate going, but I'd wait for someone who knows. Don't go reinstalling just yet though!

---

### Post by Brunellus on 2005-11-29
theoretically it should be possible to run a livecd which has a partitioner...since the livecd can run without mounting your / partition, you should be home free.

---

### Post by az on 2005-11-29
You want to shrink it or grow it?

You probably can do it.  It depends on how much space you have.

---

### Post by jriff on 2005-11-29
I want to grow it - AND move it. 

Strange that it is that difficult. One should hink that it would be less of a problem in Linux than in Windows.

Can I use the install cd or do I have to get a live cd?

---

### Post by az on 2005-11-29
It depends.  You cannot change the beginning point of a partition, just the end.

If, for example it is in the middle of a hard drive and you want to bring it closer to the beginning, you will need to shrink it so that you have enough room to move it (or copy it) to then end of the drive, delete the previous partition and move it back to the place you want it (closer to the beginning) and then delete the partition you just created after it so that you can grow your original partition to use that space.

Clear enough, eh?

What is your current layout?

Yes, you can do all of this with the installer cd.  You will have an easier time using the live cd, though.


This is not an absolute beginner topic.

---

### Post by jriff on 2005-11-29
My layout is: 

10 GB NTFS
20 GB Free space
20 GB ext3
3,5 GB swap

All I want is to move the ext3 partition to the beginning of the free space and resize it so it is 30 GB in size. Then I want to move the swap partition to the beginning of the new free space. Thus getting a layout like this:

10 GB NTFS
30 GB ext3
3,5 GB swap
xx GB free space

And I would very much like to use the install cd. Just to learn how.

---

### Post by az on 2005-11-29
1.  Read the parted manual

it is simple

parted /dev/hda 
(if hda is the drive we are talking about)
print
(that shows you the partitions)
move
(enter partition to move)
(enter the place you want it moved to)

removing and resizing partitions is just as simple.  Be sure to resize the filesystem, too, not just the partition.


Do not forget to change the fstab and grub menu.list if applicable.

If you cannot bott, you can always fix it.  You can always boot the installer, let it detect your hardware and chroot into your linux system and, say, reinstall grub.

So, to get to use parted using the installer disk, boot it and let it detect your hard drives and so forth.  Then hit CTRL-ALT-F2 to get into a console.  You are root.  So, then run parted

parted /dev/hda



Off you go!  (Back up your data first, since I will not be held accountable if you bork your system)

---

### Post by jriff on 2005-11-29
Well - that dosn't sound too dificult. It was the CTRL-ALT+F2 thing that I didn't know. 

I can see in the manual that "resize" resizes the filesystem. How do I resize the partition? By moving it and specifying different start-end values? Won't the partition be truncated thus making me loose data? Or should I resize the filesystem first?

Btw. The reason I posted in Absolute Beginner is that I AM an absolute beginner regarding Linux. Hope it's ok :-)

---

### Post by butter on 2005-11-30
I just had to resize an ext3, and, ultimately, it was painless.  It took a while to find but eventually I stumbled upon the pclinuxos live cd.  Boot, sign in as user root, password root, open a terminal, and type in diskdrake.  Simple from there, and no problems for me whatsoever. [http://www.pclinuxonline.com/pclos/](http://www.pclinuxonline.com/pclos/)  . Good luck.

---

### Post by az on 2005-11-30
[QUOTE=jriff]By moving it and specifying different start-end values? Won't the partition be truncated thus making me loose data? Or should I resize the filesystem first?

Btw. The reason I posted in Absolute Beginner is that I AM an absolute beginner regarding Linux. Hope it's ok :-)[/QUOTE]

Hmm.  Resize will resize the partition.  It will first shrink the filesystem and move everything out of the way, but you end up with a smaller partition.  If you ask it to shrink the partition too much, like smaller than the amount of data on it, it will balk and refuse (rightly so) to do it.

As for the absolute beginner, I did not post that for you, but for others reading this thread who may be thinking you have to have a degree in physics to be an absolute beginner in linux.  I try hard to post graphical display solutions to questions and avoid the command-line in this section, but that is not what you asked.  That's all.

---

