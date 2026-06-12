---
title: "Change desktop's location"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by marko_4454 on 2007-04-16
Is there any way to change the location of the desktop for a user. 
I have partition sda1 which is my boot partition (has /, /boot, home/ and /home/marco/Desktop/ and all that)
I want to change the location of "Desktop" to my other partition sda3. Is there any way to do this?
Can you do symbolic link or something like that?
-Thanks,
marco

---

### Post by SOULRiDER on 2007-04-16
Im not too sure about this, but i guess you could mount sda3 at /home/marco/Desktop but that will make the whole partition be your desktop.

---

### Post by marko_4454 on 2007-04-16
Yeah. I just want this because I always save everything to the desktop, but my partition 1 got corrupted recently (not partition 3) so I lost all of my info in my Desktop and partition 1. 
I did this in Windows XP by going into the regedit and modifying a field that put the Desktop's path.
Anyone else?
Is this even possible?

---

### Post by marko_4454 on 2007-04-18
can someone perhaps move this so somewhere where is not newbie? Maybe they can answer it in another place?
-Thanks!

---

### Post by meborc on 2007-04-18
i think you can edit your fstab file so that the mount poin of your 3rd partition is /home/marco/Desktop... then sudo umont -a and sudo mount -a and you should be set :)

try it out to see if it works... never tried it miself

---

### Post by marko_4454 on 2007-04-18
I am not home, but I'll try that for sure. Thanks, I'll post results.

---

### Post by marko_4454 on 2007-04-18
OK I read your post and I realized what you really meant. Maybe it isnt possible...or something. The problem with your suggestion is that some programs that I have already have the data path to be in /media/(name of sda3) and I'll have to change it to /home/marco/Desktop for all of them...kind of a pain, but possible.
While this may work, I was looking for some easy tweak or something like in Windows. But I guess I'll just stick with the try-not-to-save-much-stuff-to-desktop mentality and save everything to my 3rd partition.
Anyways, Thanks to both of you for your suggestions!

---

### Post by earobinson on 2007-04-18
remove the Desktop folder first
```
rm -rf ~/Desktop
```
then make a link to whatever folder you want your new desktop to be
```
ls -s <path to new desktop folder> ~/Desktop
```

Let us know how it goes

---

### Post by marko_4454 on 2007-04-19
That seems like it may work....but do you mean "ls"?? or "ln"???

I am not home right now, so I cant try it. But once I do, I'll try it out.
Again, Thanks!

---

### Post by earobinson on 2007-04-20
oops ln sorry

let us know how it goes

---

### Post by jorgealfonso on 2007-08-22
earobinson> Worked great!

```
ln -s <path to new desktop folder> ~/Desktop

```

I have actually 3 partitions (windows/ubuntu/shared-data). I wanted to have my desktop shared between windows/linux on a folder on the "third" disk (shared-data).

Did the registry-thing on Windows + your suggestion on Ubuntu and it's now up and running :-)

My desktop's mess looks actually nicer on Ubuntu, by the way :-P

---

### Post by sam_hatoum on 2008-06-23
hi

I did this and for some reason, my desktop now points to my home directory!

which means the entry in my home directory for the desktop (currently a link) is now useless.

does anyone know where the location for the desktop, as a special folder, is maintained?

Thanks

---

### Post by ad_267 on 2008-06-23
> **sam_hatoum said:**
> hi

I did this and for some reason, my desktop now points to my home directory!

which means the entry in my home directory for the desktop (currently a link) is now useless.

does anyone know where the location for the desktop, as a special folder, is maintained?

Thanks

Can you post the exact command you entered?

You can change the folder used for the desktop by editing the file ~/.config/user-dirs.dirs then logging out and back in again.

---

### Post by ad_267 on 2008-06-23
I forgot you should first hit Alt-F2 and run "gconf-editor" then go to apps - nautilus - preferences and then in the right hand side make sure "desktop_is_home_dir" is not enabled.

---

### Post by sam_hatoum on 2008-06-23
perfect! exactly what I'm after. thanks

I used

```
ln -s /media/shared/documents/Desktop /home/sam/Desktop
```


but /media/shared is a windows drive, and the Desktop is my windows Desktop. The idea is to share the desktop on both windows and ubuntu. 

Seems to be problematic, but I'll give it another go and see how that goes.

thanks agian

---

### Post by sam_hatoum on 2008-06-23
> **ad_267 said:**
> I forgot you should first hit Alt-F2 and run "gconf-editor" then go to apps - nautilus - preferences and then in the right hand side make sure "desktop_is_home_dir" is not enabled.

nice to know about gconf-editor, thanks :)

it's not enabled btw. I think something went wrong perhaps with the NTFS drive not being ready, or shut down correctly or whatever, so ubuntu couldn't see it and decided to default to home.

---

