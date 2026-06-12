---
title: "Moving space from one partition to another"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by eklypze on 2006-01-06
Hello everyone!

When I first installed Ubuntu, I had no idea how much space I was going to need, so I started off by giving the Ubuntu partition 5GB of disk space. Now I am comfortable with Ubuntu, and would like to give it some more disk space from my other Windows XP NTFS partition.

Is it possible to take some space from the NTFS partition onto my Ubuntu partition?

Thanks. :)

---

### Post by TeeAhr1 on 2006-01-06
It is.  Gparted (in the repositories) is, from the little bit I've used it, a very slick, easy-to-use program.  Boot the live CD to do it, though; you can't resize a partition you're using at the time.

---

### Post by eklypze on 2006-01-06
Thanks for the reply.

I have booted with the Live CD, and opened up GPartEd. I was able to take space out of the NTFS drive properly, and it left some unallocated space that I could use. The problem though is my Ubuntu partition (ext3) says that it's maximum size is only 4700MB, and it would not increase any more, even though I have some unallocated space left to use.

Is there a solution to this problem? Thanks. :)

---

### Post by TeeAhr1 on 2006-01-06
Hmm.  Huh.  I don't recall running into that when I resized.  I'm at work right now, but I'll have a look when I get home, unless anyone else wants to take a shot at this...

---

### Post by eklypze on 2006-01-06
I'm not sure if this has to do with the reason I cannot add this unallocated space to the Ubuntu partition but it says something about this space being added to either the beginning of a partition or to the end, I simply lowered the maximum space in the NTFS drive, and maybe that space was added to the end of the NTFS partition?

I am a complete newbie at all of this, I'm not even sure if what I'm saying makes sense or not. :razz: 

Thanks.

---

### Post by Sef on 2006-01-06
Since you are increasing the size of the partition, I would add it to the end.

---

### Post by wyohermit on 2006-01-06
As I understand it. It's not possible to add to the beginning of a partition.  So if I am understanding your prediciament correctly.  The only solution I see (short of a COMPLETE reinstall) would be to create a new partition out of the unused space you have created and use it as data storage or link your home directory to it.

---

### Post by TeeAhr1 on 2006-01-07
Damn, didn't mean to leave you hanging last night, sorry.  Anyway, can you post a screenshot of what your Gparted screen looks like, and another one of the error message?

---

### Post by eklypze on 2006-01-07
Oh, It's OK now, I got it to work by completely wiping out the NTFS drive. And there was no error message, it just would not allow me to enter a bigger number than 4700MB.

---

### Post by TeeAhr1 on 2006-01-07
So you can put that space into your ext3 partition now?  Good deal!

---

### Post by eklypze on 2006-01-07
Yup. Thanks for all your help. :)

---

### Post by kopolee11 on 2006-01-08
I believe I have the same problem, so I didn't want to make a different thread. Here's a screenshot of the Gparted screen [[IMG]http://img496.imageshack.us/img496/8498/screenshot6wp.th.png[/IMG]](http://img496.imageshack.us/my.php?image=screenshot6wp.png)

And this is what I get when I make the Fat32 partition smaller. [[IMG]http://img350.imageshack.us/img350/403/screenshot25ur.th.png[/IMG]](http://img350.imageshack.us/my.php?image=screenshot25ur.png)

I'm sorry for being newbish, but what do I do now? When I try to increase the Ubuntu partition it does not let me. I want to keep the Windows partition. Thanks in advance, and sorry for asking such a basic question.

---

### Post by kopolee11 on 2006-01-08
Can anyone help??:confused:

---

### Post by dueY on 2006-01-08
I'm not familiar with Gparted so I can't give specific instructions, but you need to take the unallocated space and format it in ext3 then add it to the end of your existing ext3 partition.

---

### Post by plors on 2006-01-09
You cannot move the start of an ext3 filesystem. So you might have a little problem here.
However there is a way to resolve this, but it's going to be close. :)

- shrink your fat32 partition even further (you may grow it back later if you like)
- shrink your ext3 partition to it's bare minimum :)

the unallocated space should be slighly larger then the ext3 now 
if so, you may proceed with the following steps:

- copy the ext3 partition to the unallocated space (if possible, you could leave some room for the fat32 to grow back)
- if that was succesfull you can safely remove the old ext3
- then grow your freshly copied ext3 into the unallocated space..

All this can be done with gparted. Just make sure you have a backup of important files and perform all these steps ONE by ONE! 

good luck!

---

### Post by kopolee11 on 2006-01-09
> I'm not familiar with Gparted so I can't give specific instructions, but you need to take the unallocated space and format it in ext3 then add it to the end of your existing ext3 partition.

Thanks for responding, but just wondering. Why is the partition only able to extend from the bottom, and not the top. (If that makes any sense :p)  Just wondering if there is a particular reason for this.

> You cannot move the start of an ext3 filesystem. So you might have a little problem here.
However there is a way to resolve this, but it's going to be close.

- shrink your fat32 partition even further (you may grow it back later if you like)
- shrink your ext3 partition to it's bare minimum

the unallocated space should be slighly larger then the ext3 now
if so, you may proceed with the following steps:

- copy the ext3 partition to the unallocated space (if possible, you could leave some room for the fat32 to grow back)
- if that was succesfull you can safely remove the old ext3
- then grow your freshly copied ext3 into the unallocated space..

All this can be done with gparted. Just make sure you have a backup of important files and perform all these steps ONE by ONE!

good luck!

Thanks, I didn't think of that! I'll have to remove a few program, but I can always just reinstall it....

...Right? ;) 

Thanks again, I'm still learning how to use Ubuntu GNU/Linux.

---

### Post by KermitJr on 2006-01-09
Use a livecd (Knoppix I know has it) and run qtparted.

Very userfriendly.

---

### Post by plors on 2006-01-10
[QUOTE=KermitJr]Use a livecd (Knoppix I know has it) and run qtparted.

Very userfriendly.[/QUOTE]

Wouldn't help him as the 'static start' of ext3 is universal. just run the steps i described and it should be fine.

---

### Post by kopolee11 on 2006-01-10
Yea, plors cutting and pasting plan worked out. ;)

Thanks!

---

### Post by plors on 2006-01-10
good to hear that! :D

Btw.. GParted could use some manuals about scenarios like yours. Maybe you'd like to create a small step-by-step manual on this scenario (and maybe others as well) ?

feel free to [contact]("http://gparted.sourceforge.net/contact.php") us about this.

---

### Post by tvor on 2007-04-07
Hmm. seems to be stuck at exactly the same point. Have unallocated space which I would like to add (increase size) of my existing /home partition. GParted does not allow me to increase the size by typing higher number that it's actuall existing size....I'm able to create new partition from unallocated space, but that's not what I'm after !

It seems to me GParted is only able to decrease and split partitions - I'm wrong here? :confused: 
(I'm using bootable GParted CD) and the unallocated space is AFTER all partitions (at the bottom of the list)
[IMG]http://tvor.bloguje.cz//img/mmm.png[/IMG]

---

