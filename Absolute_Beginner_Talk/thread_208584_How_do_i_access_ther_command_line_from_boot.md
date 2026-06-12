---
title: "How do i access ther command line from boot?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by dougmwpsu on 2006-07-03
i boxered my ubuntu install in about 30 seconds and need to edit a config file to get it bootable again. i managed to finally get grub reinstalled, so now all i need to do is figure out how to access the command line from there.

how do i get to the ubuntu cli from grub??!!?!?

---

### Post by soce_32 on 2006-07-03
If you can only get to grub, but have an error during kernel startup, you will most likely need to boot from the install CD using either rescue mode, or mounting your root partition and editing the file from there.

---

### Post by tonyr on 2006-07-03
When you boot, are you at the grub monitor (looks like **grub>**), or do you have
a boot menu with several options?

---

### Post by dougmwpsu on 2006-07-03
i'm at the menu with several options, but i can get to the command line or edit the menu. there's really no way to get directly to the command line?

---

### Post by tonyr on 2006-07-03
One of the boot options should say **recovery mode**.  If it's there, select
that one.  It should boot you into single user mode (root, console, no X).

At the boot menu, you can only boot one of the listed options, or go into the
grub monitor, which is NOT the cli you are looking for.   If the recovery mode
boot doesn't work, you'll need to use **soce_32**'s suggestion.

---

### Post by dougmwpsu on 2006-07-03
i'm really not having any luck.  the recovery mode runs into the same error in grub, the live cd can't mount any of my hard drives. so, how on earth can i do this:


Quote:
Originally Posted by chrism66
Ok, I screwed up before I found this post. I am complete newbie to Linux/Ubnutu. So I tried to activate my wirelesss from the Network option fron the administration. I am hanging up during boot due to the fact that I have the dreaded ra0 entries in the etc/network/interface, how can I deletw these entries inthis file from the commnad lin in recovery mode or console? Any help to get me back on the road to Ubuntu would be greatlt appreciated!!! Thanks in advance .

Chris
type: sudo vi /etc/network/interfaces
key commands:

" i " key= insert (use it to edit)
Quote:
(edit all lines that you need safest way is to add # at the begining of the line)
ex:
auto ra0
change to:
#auto ra0
" esc " key= exit editing (like pressing menu bar)

now to save file and exit use:
"Shift" key and ":" key

type : wq!

done

---

### Post by dougmwpsu on 2006-07-03
ARRRRRGGGG!!!!

ok, i booted up in knoppix live cd, and was fianlly able to find the messed up /etc/network/interfaces config file, but now, i can't change the file. i set the drive to be readable, but i still cant make the nessacary changes.  how on earth do i change this file?!?!?!?

---

### Post by tonyr on 2006-07-04
You have to be root (superuser) to edit the file.  I don't know how to do that in Knoppix.
In  Ubuntu you use **sudo** before the command name, as in
```

sudo vi /etc/network/interfaces

```

In Mandriva, you have to type **su** and enter the root password to become
the root user.

---

### Post by dougmwpsu on 2006-07-04
ok, that did it, i'm finally back in my ubuntu install, and i got wireless working!!!
oh happy days are here again!

---

