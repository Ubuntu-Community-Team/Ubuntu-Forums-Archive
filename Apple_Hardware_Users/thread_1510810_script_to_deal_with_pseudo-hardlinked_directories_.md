---
title: "script to deal with pseudo-hardlinked directories in Time Machine backups"
date: 2010-06-16
forum: Apple Hardware Users
---

### Post by applesucks on 2010-06-16
Hi folks. Just wanted to share a script that I wrote to migrate data off of a Time Machine backup. As anyone who's tried this knows, it's not straightforward because most directories are pseudo-hardlinked according to some hare-brained scheme Apple came up with.

(Hard-linked directories actually show up as zero-length regular files with bizarre link counts greater than 128. The link count corresponds to a directory called "[FONT=Courier New]dir_$N[/FONT]" (where [FONT=Courier New]$N[/FONT] is the link count) inside of a special directory at the root of the Time Machine volume called "[FONT=Courier New].HFS+ Private Directory Data^M[/FONT]" (where the [FONT=Courier New]^M[/FONT] is a literal carriage-return character).)

Here's the script (it's also attached, for convenience). It works pretty much the same as "[FONT=Courier New]rsync -av <SRC_DIR> <DST_DIR>[/FONT]" would, if the pseudo-hardlinks weren't in the way. In other words, it just recursively copies the first directory to the second.

So the first argument (the source directory) is typically something like

[FONT=Courier New]/media/<TIME_MACHINE_VOLNAME>/Backups.backupdb/<HOSTNAME>/Latest/<VOLNAME>[/FONT]

if you want the entire latest backup. It can also be a relative path, if you've already changed to a directory inside the backup.

```

#!/bin/bash

# This is a script for a Linux machine to copy the contents of a Time Machine
# backup.

tm-usage() {
echo
echo "Usage: $(basename "$0") <source_directory> <destination_directory>"
echo "  where <source_directory> is inside a Time Machine volume"
echo
exit 1
}

[ $# -eq 2 ] || tm-usage

SRC=$(readlink -f "$1")
DST=$(readlink -f "$2")

[ -d "$SRC" ] || {
echo
echo "$SRC is not a directory"
tm-usage
}

[ -d "$DST" ] || {
echo
echo "$DST is not a directory"
tm-usage
}

# Awful hack for finding the special directory which contains the pseudo-
# hardlinked directories.
HLDIR=$(echo "$(df "$SRC" | tail -1 | awk '{ print $6 }')"/.HFS+\ Private*)
[ -d "$HLDIR" ] || {
echo
echo "I couldn't find the special directory with pseudo-hardlinks."
echo
echo "Are you sure that"
echo "  $SRC"
echo "is inside a Time Machine volume?"
echo
echo "If so, don't give up; you probably just need to make some trivial"
echo "modification to this script to make it work."
echo
exit 2
}

tm-copy() {

local SRC="$1"
local DST="$2"

# Copy the regular stuff
rsync -av "$SRC" "$DST"

cd "$SRC"
DST="$DST/$(basename "$SRC")"

# Find all the pseudo-hardlinked directories and invoke ourself recursively to
# copy their contents
find . -links +127 -printf "%P\n" | {
while read DIR; do

local DIRNUM=$(stat -c %h "$SRC/$DIR")
local DSTDIR="$DST/$(dirname "$DIR")"
local NAME="$DSTDIR/$(basename "$DIR")"

[ $(stat -c %s "$NAME") -eq 0 ] || {
echo
echo "Sanity check failed. Bailing out."
echo
exit 3
}

rm "$NAME"
tm-copy "$HLDIR/dir_$DIRNUM" "$DSTDIR"
mv "$DSTDIR/dir_$DIRNUM" "$NAME"

done
}

}

tm-copy "$SRC" "$DST"

```

---

### Post by paul0075 on 2011-07-07
Am total n00b at this and need some help please. I havent got a clue how execute this script, and when I try I am getting this error:

time-machine-copy: 6: Syntax error: Bad function name

Any suggestions appreciated. Thanks

---

### Post by alexmurray on 2011-07-08
There is also a fuse module which supports reading time machine backups and presenting them in a much more logical manner. Was recently covered on phoronix [http://www.phoronix.com/scan.php?page=news_item&px=OTY0NQ](http://www.phoronix.com/scan.php?page=news_item&px=OTY0NQ) or you can try grab it from github and test it yourself [https://github.com/babali/tmfs](https://github.com/babali/tmfs)

---

