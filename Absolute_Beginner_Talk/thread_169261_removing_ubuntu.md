---
title: "removing ubuntu"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by big-hed on 2006-05-02
After installing Ubuntu as a dual boot with XP how do i leave the PC back the way it was??? i.e. booting up XP and removing all traces of GRUB.  

I know you may wonder why id wanna do this but i just wanna try it out and see how or can it be done! (though i still favour Ubuntu).  The reason is i wanna try it at my place of work which ive dual booted with XP but as im leaving soon i'll want to take it off again and leave it as i got it.????

---

### Post by byenary on 2006-05-02
i think there is a way to boot up with a dos boot disk than do
fdisk /mbr
and set the windows partition active, but i'm not shure of this :???:

---

### Post by Rinzwind on 2006-05-02
Boot into windows with your CD and choose the repair option.

At the prompt typ:

fixmbr


and your Grub is gone.

---

### Post by irw on 2006-05-02
If at work you cannot get access to a Windows CD, you could edit the grub menu to remove the non-windows options and set the delay to zero.

Using a live CD use GParted or similar to remove the linux partitions and expand the Windows one.

I've not tried this, but assume it should work.

---

### Post by Rinzwind on 2006-05-02
[QUOTE=irw]If at work you cannot get access to a Windows CD, you could edit the grub menu to remove the non-windows options and set the delay to zero.

Using a live CD use GParted or similar to remove the linux partitions and expand the Windows one.

I've not tried this, but assume it should work.[/QUOTE]


No it wont. You'll end up with a boot that stops with a message like 'no operating system found'.

---

### Post by irw on 2006-05-02
[QUOTE=Rinzwind]No it wont. You'll end up with a boot that stops with a message like 'no operating system found'.[/QUOTE]
:confused: Why not?

if you leave the Windows options, does it not automatically boot it, or does it need more than one option?  If so could you give it two entries pointing to the same windows partition?

---

### Post by Rinzwind on 2006-05-02
[QUOTE=irw]:confused: Why not?

if you leave the Windows options, does it not automatically boot it, or does it need more than one option?  If so could you give it two entries pointing to the same windows partition?[/QUOTE]


After deleting Ubuntu (With your live-cd or Gparted) where do you think your system is going to find grub!?

---

### Post by irw on 2006-05-02
[QUOTE=Rinzwind]After deleting Ubuntu (With your live-cd or Gparted) where do you think your system is going to find grub!?[/QUOTE]


Ahh ... good point!  :oops:

---

