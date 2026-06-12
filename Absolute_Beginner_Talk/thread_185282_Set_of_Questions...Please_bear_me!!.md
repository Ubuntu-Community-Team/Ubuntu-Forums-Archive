---
title: "Set of Questions...Please bear me!!"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by hellmet on 2006-05-31
Dear All,
After nearly 15 days of proper Ubuntu usage,I found out that there
were certain things that I cud not do/ are out of my understandin..
I'd like you people to please clarify some of these..

1)How do I create shortcuts to folders in FAT32 partitions?
2)How do I remove Drive icons on Desktop
3)How to Rename Drive/Partition names?
4)Again How do I create links to these drives somewhere else.
5)Is there a nice GUI for PPPoE(ADSL) connection(Rpppoe doesn't seem to work)
6)How do I upgrade to Dapper without breaking packages..(Is update manager fine?)

Thanks..
-hellmet

---

### Post by rado_london on 2006-05-31
1. Right click on Panel-Add to Panel- Custom Application launcher and there choose type to be link and fill the path

2. Go to Applications-Configuration-Configuration editor. In there go to Apps-Nautilus-Desktop and untick volumes_visible

3. I dont know. Sorry

4. Same as 1 just drag it from the panel to the place

5. I dont know as I dont have pppoe

6. I think it should be fine but updating often causes many troubles.

Good luck

---

### Post by xael on 2006-05-31
hellemt, 

There are lots of good info in the Official Wiki.

---

### Post by hellmet on 2006-05-31
Yaa xael..but petty things such as these..are not covered I guess..
Ppl who've used Ubuntu for some time..will have no problem telling these..rite?
Thanks Rado...
but can I create shortcuts to the Desktop??
not to the panel alone..
thnkx

---

### Post by meng on 2006-05-31
Have you tried searching within synaptic for "pppoe"? If there is a nice GUI in the repositories, this may give you some clues.

(And it's "bear with me", not "bear me" - that would mean either carrying you or giving birth to you!)

---

### Post by rado_london on 2006-05-31
[QUOTE=hellemt]Yaa xael..but petty things such as these..are not covered I guess..
Ppl who've used Ubuntu for some time..will have no problem telling these..rite?
Thanks Rado...
but can I create shortcuts to the Desktop??
not to the panel alone..
thnkx[/QUOTE]
Yes sure. Right click on the desktop-Create Launcher. Then change the type to link and specify the path.
EDIT: The type should be folder sorry not link as it will ask for URL.

---

### Post by hellmet on 2006-05-31
Doesn't work..it does not allow me to select a Folder...it keeps going inside..
I selected type"Directory"
Please explain

---

### Post by hellmet on 2006-05-31
Next set of Ques...
How do I set the default app. to open mp3 to XMMS.
Can I open mp3 into XMMS just by clickin on it..
It doesn't seem to happen.
I have mp3pro support in XMMS..so i'd like to use it for all mp3.

Also when we move our mouse over an mp3 file it starts to play..
It doesn't happen for mp3pro.
Can i install some codecs so that even that works??

---

### Post by meng on 2006-05-31
In GNOME/Nautilus, right-click on any mp3 file, choose Properties, Open With, and set XMMS as the default. This works for any other file associations you wish to do too.

---

### Post by Ecthelion on 2006-05-31
> 3)How to Rename Drive/Partition names?

```
sudo gedit /etc/fstab
```

change the partition name you want
example:
> /dev/hdb1       /media/**Music**     ext2    defaults        0       2

I changed hdb1 (original name) to Music
Then:
```
sudo mkdir /media/**new__name_for_that_partition**
```
And finally
```
sudo mount -a
```

That should do the trick.

---

### Post by Ecthelion on 2006-05-31
[QUOTE=hellemt]4)Again How do I create links to these drives somewhere else.[/QUOTE]

Since you don't want them on your desktop, you could also simply mount your partition on another location...
You can mount a drive/partition anywhere you want in Ubuntu.
This simply means that you can choose what the path is for that particular drive / partition.

You only have to change in fstab
> /dev/hdb1     **  /media**/Music     ext2    defaults        0       2
to the path you want.
Again, after you do that type
```
sudo mount -a
```
To apply those changes in your current session

---

### Post by nudnik on 2006-05-31
Upgrading to Dapper should work fine if you have Gnome using:

gksudo "update-manager -d"

This is typed into the "terminal" found under "applications" tab, sub tab "accessories"

Do this only if you have broadband, even then it takes quite a while.

---

### Post by hellmet on 2006-05-31
If for some reason the download stops in the middle..
will I be able to resume it...
And if I can't...will I be breaking some packages??

---

### Post by hellmet on 2006-05-31
[QUOTE=meng]Have you tried searching within synaptic for "pppoe"? If there is a nice GUI in the repositories, this may give you some clues.
[/QUOTE]
I tried that..no use dude..
Rp-pppoe doesn't seem to work..installed it a few days back..
> (And it's "bear with me", not "bear me" - that would mean either carrying you or giving birth to you!)
LOL..I know that dude...I realised my grave mistake after I submitted the Thread.
Sorry:D

---

### Post by 3rdalbum on 2006-06-01
The easiest way to do #1 (creating links to folders on Fat32 partitions) is to click the folder icon with the left mouse button to select it, then drag it using the middle mouse button (or scroll wheel, or both mouse buttons) to the place you want the link to be. When you release the button, a menu will pop up asking you whether you want to "Move here", "Copy here" or "Link here". Choose "Link here".

---

