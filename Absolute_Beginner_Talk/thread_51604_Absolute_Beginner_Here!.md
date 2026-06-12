---
title: "Absolute Beginner Here!"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by Lateralus on 2005-07-24
OK I’m completely new to this and I have some NooB questions.
I've run Live CD and played around with it for a few hours and every things fine and now I won't to install Linux permanently on to a hard drive.
I have 2 hard drives, 1 with WinXP C : and the other is just for storage D :.
Can I just put the ISO onto a CD and install Linux from windows onto the D: drive (Formatting it first of course). Or do I have to install it as if I was installing Windows onto a clean drive? Or better yet can some 1 explain to me the easiest, fastest and best way to do this? 

Thanks!

---

### Post by Firetech on 2005-07-24
You can indeed install Ubuntu on your D: drive. Then at startup time, you can choose if you want to start Windows or Ubuntu.
There is a great guide how to do this at [https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo) (scroll down to the "+Successful Easy Dual-boot Same-Disk installation with WinXP+" header.)
Although, the installer CD is in most cases able to both help you reformat the drive and fix the Windows/Ubuntu choice at startup automatically.

---

### Post by Lunde on 2005-07-24
Upon a clean drive, preferably on an empty space on a drive, but you can delete the partition or disk content with the Ubuntu installer.

Don't just burn the .iso, but choose "burn from image" or similar, the iso is a packed copy of a ready CD to be extracted to a CD.

Hope everything works out fine, else we're here to help you.

Have fun

---

### Post by Firetech on 2005-07-24
You can indeed install Ubuntu on your D: drive. Then at startup time, you can choose if you want to start Windows or Ubuntu.
The installer CD is in most cases able to both help you reformat the drive and fix the Windows/Ubuntu choice at startup automatically.

---

### Post by UbuWu on 2005-07-24
On Ubuntu (and linux in general) your D drive will probably be referenced to as /dev/hdb. And the installer can format it for you.

---

### Post by Kvark on 2005-07-24
If the partitions C and D are on separate physical hard disks then just tell the installer to use the whole secound one.

If the partitions C and D are on the same physical hard disk then the easiest way is to remove the D partition on beforehand and tell the installer to use the free space.

Whatever you do. Make sure you don't tell the installer to use your whole first physical hard disk since that would overwrite the C partition. As always before you do anything major, like installing a new OS, backup all your files.

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=Kvark]
Whatever you do. Make sure you don't tell the installer to use your whole first physical hard disk since that would overwrite the C partition. As always before you do anything major, like installing a new OS, backup all your files.[/QUOTE]

AKA DON"T ACCEPT THE PARTITIONER DEFAULTS!!!

sorry to scream.

---

### Post by Lunde on 2005-07-25
[QUOTE=poofyhairguy]AKA DON"T ACCEPT THE PARTITIONER DEFAULTS!!!

sorry to scream.[/QUOTE]
 Can you go a bit more into details for later reference?

Sorry for wispering...

---

### Post by Lateralus on 2005-07-25
Ok I've got it installed and up and running and now i have a few probs. (nothing big)
1 at the screen where you pick what OS to load Ubuntu, WinXP ex, Ubuntu is the default OS and if you don't pick what OS to load Ubuntu auto loads. How do I configure this to load XP auto or take the auto load out completely?
2 I tried to download and install Xmms and nothing happened at the down load. I click the D/L and nothing happens the same can be said about winamp.

PS: thanks for the speedy replys to my first post.

---

### Post by Kyral on 2005-07-25
I can't help you with the 1st question, but the second question, did you try using Synaptic?

---

### Post by Lunde on 2005-07-25
[QUOTE=Lateralus]Ok I've got it installed and up and running and now i have a few probs. (nothing big)
1 at the screen where you pick what OS to load Ubuntu, WinXP ex, Ubuntu is the default OS and if you don't pick what OS to load Ubuntu auto loads. How do I configure this to load XP auto or take the auto load out completely?
2 I tried to download and install Xmms and nothing happened at the down load. I click the D/L and nothing happens the same can be said about winamp.

PS: thanks for the speedy replys to my first post.[/QUOTE]
 1. Open terminal and type
**sudo gedit /boot/grub/menu.lst **

Find the line
**default		0**

and change it to
**default		4**
if windows is 4th in list

You can also set the timeout if you think it's a bit long..
**timeout		3**

**Save and exit**

---

### Post by Lateralus on 2005-07-25
Thanks Lunde that worked great. 

But as far as d/ling go's I'm still having probs. I got XMMS installed by going to ADD/REMOVE Programs and found it there and installed it but I'm still having probs with D/Ling things. When ever I click on a D/L link of any kind nothing happens. 
Also when ever I try to play a mp3 in XMMS the program freezes. I can't shut it down stop it or nothing. I can't even shut down the computer when this happens.

---

### Post by Lunde on 2005-07-26
I had the same problem with Xmms not so long ago after a freash install, I got around it by changing the sound to Alsa. There's an option for that in the preferences for Xmms.

You may not have Alsa installed / enabled in you system, so check out the following links:

Howto: about sound in Hoary & Linux
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

HOWTO: Hear multiple sounds using Both ESD & ALSA
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

As for D/Ling, I'm not to familiar with that program

---

### Post by Lateralus on 2005-07-26
D/Ling = Downloading

---

### Post by Lunde on 2005-07-26
[QUOTE=Lateralus]D/Ling = Downloading[/QUOTE]
 In Firefox?

---

### Post by Lateralus on 2005-07-27
yes, every time I click on a download link of any kind in firefox nothing happens.

---

### Post by Kvark on 2005-07-27
Open 'System -> Administration -> Synaptic Package Manager' and then search for the programs you want there. Mark the checkbox next to the programs you want and click apply. Unmark the checkboxes to uninstall programs.

Find and install the package called w32codecs from synaptic. The media players won't be able to play much without the codecs.

You'll need to follow [this guide](http://ubuntuguide.org/#repositories) first to enable synaptic to find more programs.


Not sure what the download problem is, but would guess on faulty settings. In firefox, open edit -> settings and check the download section.

But it is generally a bad idea to download programs form websites. Use synaptic instead for programs, it's easier.

---

### Post by Lateralus on 2005-07-29
OK.. Thanks a lot. It's nice to see so many people willing to help out.

---

### Post by Kapre on 2005-07-29
[QUOTE=Lateralus]OK.. Thanks a lot. It's nice to see so many people willing to help out.[/QUOTE]
 This is the reason why lots of people are trying ubuntu (and using the community) because of the speedy reply and a lot of concerned individuals who are always willing to help.

---

