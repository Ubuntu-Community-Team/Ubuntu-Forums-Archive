---
title: "CD and DVD multisession"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by HuwSy on 2007-03-06
Is there any way to resume a multission disc so that it automatically updates any newer dated files and removes any no longer in the specified path.


I had tried making a script as follows, which generated a file "~/.hl" of files that only exist on the dics, which was then passed to growisofs to hide these files. But hte -graph-points input doesnt understand that i only want the newer versions written and not all the data again. So is there any easy way via diff, or such like, to get a list of changed files on the left (or right) side only so i can pass it to -graph-points.  As its results are too human form for easy parsing imo.

```
#!/bin/bash

cd /media/cdrom1
find > ~/.ons

cd ~/Documents
find > ~/.hns

sort -o ~/.os ~/.ons
sort -o ~/.hs ~/.hns

comm -3 -2 ~/.os ~/.hs > ~/.hl

growisofs -M /dev/hdc -V Docs -J -ldots -allow-lowercase -allow-multidot -d -D -hide-list ~/.hl -iso-level 2 -joliet-long -l -max-iso9660-filenames -udf -r -pad -graft-points /=~/Documents/

rm ~/.ons
rm ~/.hns
rm ~/.os
rm ~/.hs
rm ~/.hl

```


Or if theres an easier way then that would be better. :)

---

### Post by HuwSy on 2007-03-08
Ah got it now, cant use ~ in graph points.  So heres something for anyone else needing incremental backups which adds/replaces any files changed in the source and removes any files only still in the destination.  Im not too sure on the read input commands, as iv not used them. But if you execute it like with the args then it works.  ie ./backupscript.sh /home/user/source /media/cdrom /dev/hdc '-V Disc_Title -R -J -udf'

```
#!/bin/bash

if [-z $1]; then
	echo "Enter source directory, must be full path and omit trailing slash... ie /home/user"
	read sourcedir
else
	sourcedir=$1
fi
if [-z $2]; then
	echo "Enter destination directory, must be full path and omit trailing slash... ie /media/cdrom0"
	read destinationdir
else
	destinationdir=$2
fi
if [-z $3]; then
	echo "Enter device block... ie /dev/hdc"
	read blockpath
else
	blockpath=$3
fi
if [-z $4]; then
	echo "Additional mkisofs parameters... ie '-V Title -R -J -udf -l' "
	read additional
else
	additional=$4
fi

if [-e $destinationdir/*]; then
	type='-M'
else
	type='-Z'
fi

cd $destinationdir
find > /tmp/.destinationfind

cd $sourcedir
find > /tmp/.sourcefind

gawk '{ sub("./", ""); print }' /tmp/.destinationfind > /tmp/.destinationgawk
gawk '{ sub("./", ""); print }' /tmp/.sourcefind > /tmp/.sourcegawk

sort -o /tmp/.destinationsorted /tmp/.destinationgawk
sort -o /tmp/.sourcesorted /tmp/.sourcegawk

comm -3 -2 /tmp/.sourcesorted /tmp/.destinationsorted > /tmp/.tohide

growisofs $type $blockpath $additional -hide-list "/tmp/.tohide" -pad -graft-points /=$sourcedir/
eject $blockpath

echo "Please reload disc for data verification..."
read

diff -r -q $destinationdir $sourcedir

```

---

