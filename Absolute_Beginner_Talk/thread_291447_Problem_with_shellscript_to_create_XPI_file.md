---
title: "Problem with shellscript to create XPI file"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by samji on 2006-11-02
Hi, everyone.

I recently wrote a shellscript to zip up files for a Firefox extension into an XPI file using p7zip.

I had no problems up to a point, but the output I get is a Salamander.xpi file with an extra (unicode?) formatted character in the filename.

Here is the my shell script:

```

#!/bin/sh
# Build a Firefox XPI extension script

# (build.sh)

# ====================================================

# Set extension path, XPI and JAR filenames

extpath=/media/hda5/sams/programming/ffext/xPMvb
xpi=Salamander.xpi

jar=xpmr.jar

# ====================================================
clear
echo "Deleting old XPI file..."
rm $xpi
echo "Done."
echo
echo "Building JAR file..."
mkdir build
cd build
mkdir chrome
cd $extpath/chrome/
7z a -tzip $jar * -r -mx=0
echo "Done."
echo
echo "Moving JAR file..."
mv $jar -f $extpath/build/chrome/
echo "Done."
echo
echo "Copying additional required files..."
cp $extpath/chrome.manifest -f $extpath/build/
cp $extpath/install.rdf -f $extpath/build/
echo "Done."
echo 
echo "Building new XPI file..."
cd $extpath/build/
7z a -tzip $xpi * -r -mx=9
echo "Done."
echo
echo "Moving new XPI file..."
mv $extpath/build/$xpi -f $extpath
echo "Done."
echo 
echo "Clearing up..."
cd $extpath
rm -rf build
echo "Done."

```

Here is the output file I get with the extra character I don't want after the extension in the filename.

[[IMG]http://img162.imageshack.us/img162/3161/screenshotsalamanderxpiqb1.th.png[/IMG]](http://img162.imageshack.us/my.php?image=screenshotsalamanderxpiqb1.png)

Is there something wrong with one of my variables which is causing this problem?

Thanks in advance. ;)

---

### Post by samji on 2006-11-03
[Problem solved. Thanks anyway.](http://forums.3drealms.com/vb/showthread.php?p=438276)

---

