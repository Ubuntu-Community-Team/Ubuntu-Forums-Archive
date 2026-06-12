---
title: "tar --exclude question"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Gweilo on 2006-06-12
I'm trying to exclude a folder from the tar command (to do a backup)

```
sudo tar cvpzf /home/xyz/temp/backup.tgz --exclude='folder' * 
```

lets say, I'm in folder ~/a/ and I want to exclude folder ~/a/folder/ from my tar file, but NOT ~/a/b/folder/

How do I make the pattern only match folders starting with 'folder'?

thanks for your help

---

### Post by frenkel on 2006-06-12
[QUOTE=Gweilo]I'm trying to exclude a folder from the tar command (to do a backup)

```
sudo tar cvpzf /home/xyz/temp/backup.tgz --exclude='folder' * 
```

lets say, I'm in folder ~/a/ and I want to exclude folder ~/a/folder/ from my tar file, but NOT ~/a/b/folder/

How do I make the pattern only match folders starting with 'folder'?

thanks for your help[/QUOTE]
```
sudo tar cvpzf /home/xyz/temp/backup.tgz --exclude='~/a/folder/' * 
```

---

### Post by Gweilo on 2006-06-12
thanks for your quick reply, but unfortunately it didn't work, I already had tested that.

```
[14:26:12] ~/a$ sudo tar cvpzf /home/xyz/temp/backup.tgz --exclude='~/a/tpb/' *
bla.display~
file.tar.gz
gtk/tpb/
gtk/tpb/asdf
tpb/
tpb/x/
...
[14:28:03] ~/a$
```

I was thinking this should be possible to solve with regular expressions, but I didn't find out how to match the patterns used in tar.

---

### Post by frenkel on 2006-06-12
[QUOTE=Gweilo]thanks for your quick reply, but unfortunately it didn't work, I already had tested that.

```
[14:26:12] ~/a$ sudo tar cvpzf /home/xyz/temp/backup.tgz --exclude='~/a/tpb/' *
bla.display~
file.tar.gz
gtk/tpb/
gtk/tpb/asdf
tpb/
tpb/x/
...
[14:28:03] ~/a$
```

I was thinking this should be possible to solve with regular expressions, but I didn't find out how to match the patterns used in tar.[/QUOTE]

Don't use direct paths, this should work:
```
tar cvpzf /home/xyz/temp/backup.tgz --exclude='tpb/' *
```

---

### Post by Gweilo on 2006-06-12
Yeah, I've already tried that. Strangely none of the folders are excluded, neither tpb/* nor a subfolder called tpb.

it can't be THAT hard, right?

the man-pages only say it has to mach a PATTERN, but what exactly that is ... I've spent numerous hours googling to find this out and guessed somebody in here might know.

edit, a short conclusion:
'tpb' excludes all folders, subfolders and files that are **equal **to tpb
'tpb/' excludes nothing...

edit2: the only way I figured out how I could do this is using cat and grep and the like to generate a file containing a list of file names to exclude, which can be excluded with the option --exclude-from=FILE (or --files-from=FILE).

---

### Post by frenkel on 2006-06-12
[QUOTE=Gweilo]Yeah, I've already tried that. Strangely none of the folders are excluded, neither tpb/* nor a subfolder called tpb.

it can't be THAT hard, right?

the man-pages only say it has to mach a PATTERN, but what exactly that is ... I've spent numerous hours googling to find this out and guessed somebody in here might know.

edit, a short conclusion:
'tpb' excludes all **folders** and **subfolders **that are **equal **to tpb
'tpb/' excludes nothing...

edit2: the only way I figured out how I could do this is using cat and grep and the like to generate a file containing a list of file names to exclude, which can be excluded with the option --exclude-from=FILE (or --files-from=FILE).[/QUOTE]
So suddenly you want to exclude thing that start with tpb?
Just add a star, like this:
```

frank@Aeon:~$ mkdir a
frank@Aeon:~$ mkdir a/tpb
frank@Aeon:~$ mkdir a/bla
frank@Aeon:~$ cd a
frank@Aeon:~/a$ tar -cjvpf ../backup.tar.bz2 --exclude='tpb*' .
bla/

```
Ah well, it still excludes subfolders also...
Best solution is to use grep and cat I think. Thats the UNIX way anyway.

---

### Post by Gweilo on 2006-06-12
> So suddenly you want to exclude thing that start with tpb?
by start with I mean only folders, and not subfolders. 
> lets say, I'm in folder ~/a/ and I want to exclude folder ~/a/folder/ from my tar file, but NOT ~/a/b/folder/

I want all folders/files named tpb, but not subfolders called tpb.

'tpb*' excludes all files and (sub)folders starting with tpb. 
'tpb' would be right, except, that I don't want subfolders called tpb excluded

It's supposed to work with regular expressions, although I didn't find any references to this - if it even was supported. I think I'll have to generate a file that lists all files/folders to include to solve this problem...

---

### Post by Gweilo on 2006-06-13
couldn't solve the problem directly, but I just listed all directories I didn't wanted backed up and added all others...

```
#! /bin/sh
#
# very simple backup script. don't forget to run as root, 
# since otherwise not all needed files will be backed up
############################################################

######## user settings ######################################

# folders in the root directory to exclude
exclude=("proc" "lost+found" "mnt" "sys" "media" "tmp")
# directory where the backup file should be placed
backupdir="/media/usbdisk/backup/x40 13.06.06"

#############################################################

cd /

# folders/files in root directory to be saved
BACK=""
for i in `ls`
do
	contains=0
	for e in "${exclude[@]}"; do
		if [ "$i" == "$e" ] 
		then 
			contains=1 
		fi
	done

	if [ "$contains" == 0 ] 
	then
		BACK=$BACK" "$i
	fi
done

timestamp=`date +%Y%m%d_%H%M%S`
file="backup"${timestamp}".tar.gz"

# generate tar
tar -cvpzf "$backupdir/$file" --exclude=$file $BACK
```

---

### Post by sql on 2008-02-04
tar -cvzpP --file=/distr/backup.tar.gz --exclude={/dev/*,/proc/*,/sys/*,/srv/*,/distr/*,/tmp/*} /


tar work with directory "/" except for
/dev
/proc
/sys
/srv/
/distr
/tmp



and it really works

---

