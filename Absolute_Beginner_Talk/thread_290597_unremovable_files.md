---
title: "unremovable files"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by RexLexar on 2006-11-01
How can i remove the .jpg and the .png files?
(backgrounds downloaded from [http://art.gnome.org/backgrounds](http://art.gnome.org/backgrounds))

Boot HDD = SCSI Disk (Ubuntu)
HDD2 = 20g hda1
HDD3 = 80g hdc1 This is where those files are.
The HDD is NTFS Read/Write.
I don't have a dual boot. 

Thanks in advance for the solution (if there is any :-k )

Greetz,
Rex Lexar

> 
root@ubuntu:/media/WinOpslag# ls
[COLOR="YellowGreen"]Bootfont.bin[/COLOR]                                 [COLOR="Red"]NATURE-LonelyTree_1024x768.png[/COLOR]
[COLOR="Blue"]Branden[/COLOR]                                      [COLOR="Red"]NATURE-RedSaturday_1024x768.jpg[/COLOR]
[COLOR="Blue"]Documenten[/COLOR]                                   [COLOR="Red"]NATURE-ScotlandCloseToMallaig_1600x1200.jpg[/COLOR]
[COLOR="Blue"]Downloads[/COLOR]                                    [COLOR="Red"]OTHER-BluelightStar_1400x1050.png[/COLOR]
[COLOR="Blue"]Games[/COLOR]                                        [COLOR="Red"]OTHER-BlueStars_1400x1050.png
GNOME-ScottishLandscapeInMono_1600x1200.jpg  OTHER-OliveStar_1400x1050.png[/COLOR]
[COLOR="Blue"]Movies[/COLOR]                                       [COLOR="Red"]OTHER-SmolovSummer2004_1024x768.jpg[/COLOR]
[COLOR="Blue"]Mp3[/COLOR]                                          [COLOR="Blue"]Progs[/COLOR]
[COLOR="Red"]NATURE-FakaravaCoconutTree_1024x768.jpg[/COLOR]      [COLOR="Blue"]RECYCLER[/COLOR]
[COLOR="Red"]NATURE-FakaravaSand_1024x768.jpg[/COLOR]             [COLOR="Blue"]System Volume Information[/COLOR]
[COLOR="Red"]NATURE-HeavyWinds_1024x768.jpg[/COLOR]
root@ubuntu:/media/WinOpslag# rm NATURE-LonelyTree_1024x768.png
rm: cannot remove `NATURE-LonelyTree_1024x768.png': No such file or directory
root@ubuntu:/media/WinOpslag#


> root@ubuntu:/media/WinOpslag# ls -all
total 192
-rwxrwxr-x 1 root ntfs  4952 2006-11-01 17:11 [COLOR="YellowGreen"]Bootfont.bin[/COLOR]
drwxrwxr-x 1 root ntfs 36864 2006-06-18 23:31 [COLOR="YellowGreen"][COLOR="Blue"]Branden[/COLOR][/COLOR]
drwxrwxr-x 1 root ntfs     0 2006-07-16 15:49 [COLOR="Blue"]Documenten[/COLOR]
drwxrwxr-x 1 root ntfs     0 2006-10-18 21:52 [COLOR="Blue"]Downloads[/COLOR]
drwxrwxr-x 1 root ntfs 28672 2006-09-16 12:05 [COLOR="Blue"]Games[/COLOR]
?--------- ? ?    ?        ?                ? [COLOR="Red"]GNOME-ScottishLandscapeInMono_1600x1200.jpg[/COLOR]
drwxrwxr-x 1 root ntfs  8192 2006-09-14 00:16 [COLOR="Blue"]Movies[/COLOR]
drwxrwxr-x 1 root ntfs 77824 2006-09-26 10:20 [COLOR="Blue"]Mp3[/COLOR]
?--------- ? ?    ?        ?                ? [COLOR="Red"]NATURE-FakaravaCoconutTree_1024x768.jpg[/COLOR]
?--------- ? ?    ?        ?                ? [COLOR="Red"]NATURE-FakaravaSand_1024x768.jpg[/COLOR]
?--------- ? ?    ?        ?                ? [COLOR="Red"]NATURE-HeavyWinds_1024x768.jpg[/COLOR]
?--------- ? ?    ?        ?                ? [COLOR="Red"]NATURE-LonelyTree_1024x768.png[/COLOR]
?--------- ? ?    ?        ?                ? [COLOR="Red"]NATURE-RedSaturday_1024x768.jpg[/COLOR]
?--------- ? ?    ?        ?                ? [COLOR="Red"]NATURE-ScotlandCloseToMallaig_1600x1200.jpg[/COLOR]
?--------- ? ?    ?        ?                ? [COLOR="Red"]OTHER-BluelightStar_1400x1050.png[/COLOR]
?--------- ? ?    ?        ?                ? [COLOR="Red"]OTHER-BlueStars_1400x1050.png[/COLOR]
?--------- ? ?    ?        ?                ? [COLOR="Red"]OTHER-OliveStar_1400x1050.png[/COLOR]
?--------- ? ?    ?        ?                ? [COLOR="Red"]OTHER-SmolovSummer2004_1024x768.jpg[/COLOR]
drwxrwxr-x 1 root ntfs 28672 2006-08-19 17:13 [COLOR="Blue"]Progs[/COLOR]
drwxrwxr-x 1 root ntfs  4096 2006-07-19 00:04 [COLOR="Blue"]RECYCLER[/COLOR]
drwxrwxr-x 1 root ntfs     0 2006-06-18 22:04 [COLOR="Blue"]System Volume Information[/COLOR]
drwxrwxr-x 1 root ntfs  4096 2006-10-11 15:03 [COLOR="Blue"].Trash-bas
[/COLOR]root@ubuntu:/media/WinOpslag#

---

### Post by kkinder on 2006-11-01
Looks like a foreign file system. What file system are you using and is it fully supported?

---

### Post by echo $USER on 2006-11-01
> sudo rm -rf *.jpg *.png will remove all .jpg and .png in the current directory.

---

### Post by RexLexar on 2006-11-02
Well the file system is NTFS.
The files were copied from the ubuntu desktop to the NTFS HDD.
I used fuse to r/w to the NTFS disk.
Now I am using NTFS-3g.

Still not possible to delete the files:

> bas@ubuntu:/media/WinOpslag$ sudo rm -rf *.jpg *.png
Password:
rm: cannot lstat `GNOME-ScottishLandscapeInMono_1600x1200.jpg': Input/output error
rm: cannot lstat `NATURE-FakaravaCoconutTree_1024x768.jpg': Input/output error
rm: cannot lstat `NATURE-FakaravaSand_1024x768.jpg': Input/output error
rm: cannot lstat `NATURE-HeavyWinds_1024x768.jpg': Input/output error
rm: cannot lstat `NATURE-RedSaturday_1024x768.jpg': Input/output error
rm: cannot lstat `NATURE-ScotlandCloseToMallaig_1600x1200.jpg': Input/output error
rm: cannot lstat `OTHER-SmolovSummer2004_1024x768.jpg': Input/output error
rm: cannot lstat `NATURE-LonelyTree_1024x768.png': Input/output error
rm: cannot lstat `OTHER-BluelightStar_1400x1050.png': Input/output error
rm: cannot lstat `OTHER-BlueStars_1400x1050.png': Input/output error
rm: cannot lstat `OTHER-OliveStar_1400x1050.png': Input/output error
bas@ubuntu:/media/WinOpslag$


What to do?

P.s. I am now trying to delete the files via Vmware -> Win Xp (samba share)

RexLexar

---

### Post by gsoundsgood on 2008-01-09
i've got exactly the same issue. any solution?

---

### Post by natehall on 2008-01-09
Some wierd file types you have there! "file" is a neat command which can tell you what type of file a file is. Could you post the result of that for one of those "?" files you have?

---

### Post by F@tNic on 2008-04-02
I also have some undeletable files in my trash. 
*sudo rm -rf ** does not work at all.  ](*,)
Today, I renammed these files (names like "f1, f2...") and delete renammed files using command previously mentionned.
Hoping this will work for you, like it works for me 	\\:D/

---

