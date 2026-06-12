---
title: "Finished ripping CD now the icon refuses to disappear..."
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by daacosta on 2006-03-07
That's right... I just ripped a CD using sound juicer and after it finished it asked me to close the program or eject the CD... I chose to eject the CD and the icon for the CD remained there idle... I can't remove it... I double click on it and I get the soundjuicer program...

On my desperation I tried at CLI to remove the cdrom by doing sudo 

rm cdrom at the /media directory... How can I remove the stupid icon from the desktop and learn how to correct this recurring problem?  Also, what I did in the command line, was it a terrible mistake? At the /media directory I have: cdrom0 cdrom1 floppy floppy0... :( :( 

I hate that little bug! :confused:

---

### Post by stalefries on 2006-03-07
That cdrom that you deleted was just a symbolic link. Right click the icon, click eject.

---

### Post by daacosta on 2006-03-07
[QUOTE=stalefries]That cdrom that you deleted was just a symbolic link. Right click the icon, click eject.[/QUOTE]

I also did that one... It didn't work either... :confused:

*_**EDIT:**_*  I mean, I clicked on the symbolic link and ejected it several times and it didn't work.  Btw, it is not the first time that this happens to me and I am only asking how to solve this problem in a clean manner (i.e., no rebooting!)

---

### Post by aysiu on 2006-03-07
Your desktop just needs refreshing. Have you tried opening a terminal and typing ```
killall nautilus
nautilus
```? You could also try logging out and logging back in again.

---

### Post by Terry of Astoria on 2006-03-07
[QUOTE=daacosta]

On my desperation I tried at CLI to remove the cdrom by doing sudo 

rm cdrom at the /media directory... How can I remove the stupid icon from the desktop and learn how to correct this recurring problem?  Also, what I did in the command line, was it a terrible mistake? At the /media directory I have: cdrom0 cdrom1 floppy floppy0... :( :( 

I hate that little bug! :confused:[/QUOTE]
In /media I have a cdrom directory. You might want to re-create it. Just type "sudo mkdir /media/cdrom"
see my /media/ dir?:
```
me@maestro:/media$ ls
cdrom  cdrom0  floppy  floppy0

```

Sometimes I get those cds that won't eject. I just do:
```
sudo umount -l /media/cdrom0
```
and then
```
sudo eject /media/cdrom0
```

It always works for me here. Replace cdrom0 with the name of the directory where your cd is mounted.
The -l in the umount command is for lazy. In other words "regardless", or "force"

---

### Post by daacosta on 2006-03-07
[QUOTE=aysiu]Your desktop just needs refreshing. Have you tried opening a terminal and typing ```
killall nautilus
nautilus
```? You could also try logging out and logging back in again.[/QUOTE]

Thanks for feedback!

Aysiu,

As a very, very last resort I accept the solution about killing nautilus and restarting it. As for the second solution of logging out and back again that is precisely what I would like to avoid at all costs.  I mean, this is linux and we are not supposed to reset a la Windows whenever a process doesn't respond!  I am sorry but that can not be the solution to the problem (Not to talk about killing uptime by doing it this way...)

Terry,

I think that your solution is the right one and the one that I will adopt consisting of umounting and then ejecting from the console.  But now my question is why does this happen?  Why is it that sometimes the symbolic link to the CD refuses to die and stays there idle?  Is it a problem with sound juicer?  Has anyone reported this annoying bug?

Rgds,


-D-

---

### Post by daacosta on 2006-03-08
None of the solutions worked... killing nautilus didn't eliminate the stupid icon... umount didn't work... I know for a fact that reseting my box will work but what about uptime? what about it?

sheshhh...

Has anybody had this problem before?


Rgds,


-D-

---

### Post by aysiu on 2006-03-08
Logging out doesn't have anything to do with your uptime--your computer will still be running, and so will the Linux kernel.

Log out and log back in. You don't have to reboot.

---

