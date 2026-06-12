---
title: "3 cdroms and 2 floppies in /media"
date: 2005-08-30
forum: Absolute Beginner Talk
---

### Post by TristanMike on 2005-08-30
I was using cdcat today to catalog my cd's when I got an error on ejecting the cd, said it was already in use, so I restarted and ejected the cd and continued. I was browsing through my computer and I noticed a couple things that I don't understand. This may be confusing....

In the root of the filesystem I have 1 cdrom folder called, incidently enough "cdrom" with a little blue arrow in the top right corner. I checked properties and it says it is a linked folder, and the link is to /media/cdrom0. Ok, fair enough, first questions, why is there only 1 linked folder in the root filesystem and not 2 or 3, one for each drive/floppy? 

So I went to the /media folder to see what was going on and I noticed I had a "cdrom" a "cdrom0" and a "cdrom1" as well as "floppy" and "floppy0" and "windows". 

I only have a cdrom and dvd burner and 1 floppy so I found it odd to have 3 cdrom entries and 2 floppy entries and my windows partition is mounted directly from the filesystem so why the "windows" entry here?

Now, inside "/media" folder, the first cdrom folder, "cdrom" and the first floppy folder "floppy", also have little blue arrows in the top right corners. The cdrom one links to /media/cdrom0 and the floppy links to /media/floppy0. 

So now I have /cdrom and /media/cdrom both linking to /media/cdrom0 and /media/floppy linking to /media/floppy0, but nothing linking too or from "cdrom1" is this kind of liking normal?

So, some other questions are why do I have two "cdrom" linked folders, in seperate locations, that link to the same folder when one of the two is in the folder that it links to anyway, same thing with the floppy, why do I have a linked floppy folder when the folder it's linked to is right next to it?

Can someone explain what is going on here? I thought the /media folder was just for mount points, why is it storing linked folders?

I apologize for any confusion, but I'm pretty confused at this stuff and any answers would be greatly appreciated, I'm still learning... :)

---

### Post by Radi0ShacK on 2005-08-31
hey TristanMike,
dont panic :) these folders with blue arrow on them are just called symbolic links "simillar to shortcuts in windowz" to create a symbolic link for /media/cdrom0 @ ur home directory 

> ln -s /media/cdrom0 ~username/cdrom 
and for more info > man ln

u can delete these symbolic links "but first be sure that its symbolic links by typing ls -l symbolic_file" ok !

and for ejecting cds, you must first unmount it > umount /media/cdrom0 
or by just right clicking on the cd icon on the desktop "if u are using GNOME" and click on eject from menu. Also you can take a look at /etc/fstab file.

well i hope that i ve helped you.

---

### Post by TristanMike on 2005-08-31
Hey Radi0ShacK thanx for the response.  :)  That's cool, it confirmed what I thought. They are indeed symbolic links. My question is, I know you can't answer for sure, but did I make those "symbolic links" myself without realizing it? Where did they come from? Did a program create them? If they are in fact symbolic links, it is completely safe to delete them? (I don't like a cluttered computer) or may something be looking for the symbolic link? Because as it stands now, I have a chain like this... "/cdrom"->"/media/cdrom"->/media/cdrom0" That seems a little unnecissary, is it possible that a program created these symbolic links?

Sorry for the third degree, just very curious on how these made their way here.

I found when using cdcat, (I think) if I point it at the linked folder, it can lock up the program but if I point it directly at the "folder" it reads the cd and doesn't screw up. Big thanx for the codes. Very useful.

---

