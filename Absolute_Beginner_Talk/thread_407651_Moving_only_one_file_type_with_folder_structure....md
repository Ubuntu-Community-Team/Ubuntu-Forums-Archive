---
title: "Moving only one file type with folder structure..."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by rich.bradshaw on 2007-04-12
Hi,

I have lots of folders containing a mix of files.

I would like to find all the .png files and move them into a different folder, but stil in the folders they were in before so I end up with a folder full of folders of pngs. I want to do this because there are many with the same name, so otherwise I won't know which is which.

I have tried:
```

find ./ -name *.png -type f -print | xargs -n1 -i cp {} /media/CRUZER/Proper\ Data/
```

Which gets all the pngs into a folder, but it doesn't keep the folder structure, so I can't tell which png is from which destination...

Any ideas?

---

### Post by kidders on 2007-04-13
Hi there,

How about something like this...

```
IFS=$'\n'
for i in $(find /usr/share -type f -iname "*.png"); do
        echo mkdir -p "/media/CRUZER/Proper Data`dirname $i`"
        echo mv "$i" "/media/CRUZER/Proper Data$i"
done
```

I should really have tried harder to avoid using **for** (since you didn't use it), but this was just easier hehe. Two minor (and possibly irrelevant) suggestions...

[LIST]
[*]You may want to consider using **sudo** for the move, to guarantee you will have permission to delete things.
[*]Sometimes, **-iname** is safer than **-name**, since it protects against skipping "file.pNg".
[/LIST]

An alternative suggestion (if you had wanted to copy, rather than move) is to tarball the PNG images (thereby retaining the directory structure), and un-tar them into the desired destination.

---

### Post by bashologist on 2007-04-13
Maybe if you want to copy and keep the structure you could do this:

```
start="$HOME" #change this
destination="/tmp/testpng/" #change this

mkdir "$destination"; cd "$start"
find . -type f -iname "*.png" -exec cp --parents {} "$destination" \;
```

---

### Post by rich.bradshaw on 2007-04-14
Thanks a lot,

I love these things - in Windows you just do everything by hand, becauase you know there is no way to do it differently...

In Linux you know it is possible, just have no idea how to do it!

---

