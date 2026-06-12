---
title: "Where is the 'disks manager' ?"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by juff on 2006-12-26
Hi all,

I'm a linux newbie who has just installed Ubuntu Edgy on my second (hdb) hard drive.  I wanted to be able to look at the Windows XP files on the first hard drive (hda), and so went looking on the *Ubuntu Help Centre* for advice on how to mount the drives  This is what I found:

[COLOR="Blue"]Make Windows partitions available from Ubuntu

Windows partitions should be automatically available from any Ubuntu system. If they are not, you can make them available using the **Disks Manager**.

   1. Open  System &#8594; Administration &#8594; **Disks**     					
   2. Select the correct hard disk, and click Partitions.    					
   3. Select the relevant partition, and click Enable.
   4. To unmount the partition, click Disable.[/COLOR]

Well, that looked like good simple instructions that even I could follow.  The only problem is, '**Disks**' does not seem to appear as a menu item under System &#8594; Administration, and I can't find it under any of the other menus.  :confused: 

So, my question is, is there really a 'disks manger' for Gnome Edgy Ubuntu, and if so where do I find it?

---

### Post by pay on 2006-12-26
I don't know about a disk manager but you can mount a drive/partition with ```
sudo mount /dev/hdX /where/I/want/it #for a drive
sudo mount /dev/hdX/1 /where/i/want/it# for a partition 
```

---

### Post by idrinkwhisky on 2006-12-26
i'm not sure what you mean with "disk manager". but if you click on Places--> Computer.
You should see all your harddrives and cdrom. Rightclick a harddrive and you'll see the option "unmount".

---

### Post by xpod on 2006-12-26
We had "disks" in dapper ........just not here in Edgy for some reason:-k 

This should help though

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Good luck

---

### Post by juff on 2006-12-26
Thanks for the tips all.

[COLOR="Blue"]pay,[/COLOR] I'm guessing your commands will only work for the current session, and that you need to edit the fstab table for a more permanent solution between boots.

[COLOR="Blue"]xpod,[/COLOR] I tried the solution at [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
and that worked fine (though a bit complicated for a 'human' OS)

[COLOR="Blue"]idrinkwhisky,[/COLOR] I had tried the file manager at Places-->Computer, but my Windows hda1 and hda2 partitions just didn't appear (though a previous install of Suse 10.0 had found and mounted them OK).  Also, when I installed Ubuntu to my hdb drive, the grub loader didn't find my Win XP installation on hda1, so I'll have to attend to that too.  It might perhaps be due to the fact that I had previously installed an Acronis boot loader on hda???

---

### Post by H.E. Pennypacker on 2006-12-29
juff, it is very important to understand that there is very little that actually requires the use of the terminal.  It has become custom (actually, it has always been) of Linux users to explain instructions with the use of terminal commands.  That does not mean the terminal is necessary at all.

When you visit the psychocats.net website, you'll find that the use of the terminal is typical.  If it is not preferable, look into instructions that use GUI instead.  

As far as "Disks Manager" (I don't think it had that name - that guide you followed just calls it that.  It's called just "Disks," another oddity about Linux, whereas Windows will give names to different places of the OS), it so happens that it is not available under Edgy.  It is available under Dapper, though.  There's no explaining this, as far as I know.  

See if there's something new, something I haven't picked up on yet, that has replaced the old functionality.

---

