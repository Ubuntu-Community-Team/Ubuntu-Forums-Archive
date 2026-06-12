---
title: "Installing Vista Fonts in Ubuntu"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-16
**I found this blog entry today from Carthik Sharma, at Planet Ubuntu and thought it might of interest to members:**

[http://planet.ubuntulinux.org/](http://planet.ubuntulinux.org/)

Microsoft&#8217;s new ClearType fonts for Vista are great. The fonts include Constantia, Corbel, Calibri, Cambria, Candara and Consolas.

[IMG]http://i17.tinypic.com/4z3s13b.jpg[/IMG]

Getting them installed in Ubuntu is a breeze, thanks to a script I found.
To install the **Vista ClearType fonts** in Ubuntu, you need to install **cabextract** first.

**CabExtract**

```


http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=cabextract&searchon=names&subword=1&version=feisty&release=all


```

**Cabextract** is a utility found in the universe repository, so before you run the following command, make sure you have universe enabled in your repository list. Once this is done, install cabextract using:

$ Then, once that is done, use this script to install the Vista fonts. **Create a file called &#8220;vista-fonts-installer.sh&#8221; in your home (~) directory.**

```


#!/bin/sh
# Copyright (c) 2007 Aristotle Pagaltzis
# 
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to
# deal in the Software without restriction, including without limitation the
# rights to use, copy, modify, merge, publish, distribute, sublicense, and/or
# sell copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
# FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
# IN THE SOFTWARE.

set -e

exists() { which "$1" &> /dev/null ; }

if ! [ -d ~/.fonts ] ; then
	exec 2>&1
	echo 'There is no .fonts directory in your home.'
	echo 'Is fontconfig set up for privately installed fonts?'
	exit 1
fi

# split up to keep the download command short
DL_HOST=download.microsoft.com
DL_PATH=download/f/5/a/f5a3df76-d856-4a61-a6bd-722f52a5be26
ARCHIVE=PowerPointViewer.exe
URL="http://$DL_HOST/$DL_PATH/$ARCHIVE"

if ! [ -e "$ARCHIVE" ] ; then
	if   exists curl  ; then curl -O "$URL"
	elif exists wget  ; then wget    "$URL"
	elif exists fetch ; then fetch   "$URL"
	fi
fi

TMPDIR=`mktemp -d`
trap 'rm -rf "$TMPDIR"' EXIT SIGINT SIGQUIT SIGTERM

cabextract -L -F ppviewer.cab -d "$TMPDIR" "$ARCHIVE"

cabextract -L -F '*.TTF' -d ~/.fonts "$TMPDIR/ppviewer.cab"

( cd ~/.fonts && chmod 600 \
	calibri.ttf calibrib.ttf calibrii.ttf calibriz.ttf \
	cambriab.ttf cambriai.ttf cambriaz.ttf \
	candara.ttf candarab.ttf candarai.ttf candaraz.ttf \
	consola.ttf consolab.ttf consolai.ttf consolaz.ttf \
	constan.ttf constanb.ttf constani.ttf constanz.ttf \
	corbel.ttf corbelb.ttf corbeli.ttf corbelz.ttf )

fc-cache -fv ~/.fonts


```

Then open up a text editor and copy and paste the script into that file.

**Do a chmod a+x ~/vista-fonts-installer.sh to make the file/script executable.**

Then run the script using:

**$ ~/vista-fonts-installer.shsudo apt-get install cabextract**

**The script downloads the Powerpoint Viewer installer from microsoft.com, and then extracts the Vista cleartype fonts using cabextract. These fonts are then installed in the ~/.fonts directory.**

Please remember that the ClearType Vista fonts are not free as in they are not GPL-ed or made available under a re-distributable license. Since you are downloading the fonts from the MS website, and since you might already have a Windows XP/Vista license, this is not a crime, but consider yourself warned against the perils of supporting closed systems

---

### Post by cvaty on 2007-09-16
```

cvaty@c:~$ sudo chmod a+x ~/vista-fonts.sh
[sudo] password for cvaty:
cvaty@c:~$ ~/vista-fonts.sh sudo apt-get install cabextract
There is no .fonts directory in your home.
Is fontconfig set up for privately installed fonts?
cvaty@c:~$ fontconfig
bash: fontconfig: command not found

```

how does one setup fontconfig for privately installed fonts?

---

### Post by por100pre1 on 2007-09-16
Just create a /.fonts folder in your home directory:

```
mkdir .fonts
```

and put your fonts in there, logout or reboot.

---

### Post by cvaty on 2007-09-16
cvaty@c:~$ ~/vista-fonts.sh
trap: 47: SIGINT: bad trap


TMPDIR=`mktemp -d`
trap 'rm -rf "$TMPDIR"' EXIT SIGINT SIGQUIT SIGTERM

^^^ Apparently my system doesn't like that trap

---

### Post by alexeyten on 2007-09-22
Change following line
```
cabextract -L -F '*.TTF' -d ~/.fonts "$TMPDIR/ppviewer.cab"
```
to
```
cabextract -L -F '*.TT?' -d ~/.fonts "$TMPDIR/ppviewer.cab"
```
to get cambria.ttc file, which is a Cambria roman font.

Also you should change line
```
	cambriab.ttf cambriai.ttf cambriaz.ttf \
```
to
```
	cambria.ttc cambriab.ttf cambriai.ttf cambriaz.ttf \
```

---

### Post by alexeyten on 2007-09-22
Simply remove SIGINT from this line.
Actually, you cound even remove this line at all, but after the script executes you will have to manually remove this temporary directory.

---

