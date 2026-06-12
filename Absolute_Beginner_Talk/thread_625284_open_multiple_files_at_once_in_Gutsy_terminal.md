---
title: "open multiple files at once in Gutsy terminal"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by nemesis8601 on 2007-11-27
How would I open multiple files at once in a terminal? For instance, I have music stored in folders, so how would I open all the contents of a folder into Amarok to play? I've been using the 'gnome-open' command to open files.

---

### Post by Six_Digits on 2007-11-27
Just a guess because I don't use this but...
Perhaps:
```
gnome-open "file1" | gnome-open "file2"
```
Without the quotes of course...
etc.?

---

### Post by jordanmthomas on 2007-11-27
You can add songs to amarok's playlist like this:
```
 amarok dcop playlist addMedia filename
```
I am having a hard time making it do more than one at a time, but this should get you started.

---

### Post by Six_Digits on 2007-11-27
Seems more professional than my approach.:)
What about:
```
 amarok dcop playlist addMedia "directory holding multiple files"
```

---

### Post by PeterJS on 2007-11-27
> **jordanmthomas said:**
> You can add songs to amarok's playlist like this:
```
 amarok dcop playlist addMedia filename
```I am having a hard time making it do more than one at a time, but this should get you started.

Here's an improvement
```

#!/bin/bash

MP3S=`ls *.mp3`
for MP3 in $MP3S
do
amarok dcop playlist addMedia $MP3
done

```

---

### Post by jordanmthomas on 2007-11-27
I had tried something like that, but it breaks up any files with spaces in the names.
For example, here's the contents of a directory I have:
```

7 Jam.mp3
Animal Farm.mp3
Big News II.mp3
Big News.mp3
Droid.mp3
Escape from the Prison Planet.mp3
I Have the Body of John Wilkes Booth.mp3
Rock & Roll Outlaw.mp3
Spacegrass.mp3
Texan Book of the Dead.mp3
The House that Perterbilt.mp3
Tight Like That.mp3
Tim Sult VS. the Gray.mp3

```
Here's the output of your script if I add an
```
echo "added $MP3"
``` in the for loop
```
added 7
added Jam.mp3
added Animal
added Farm.mp3
added Big
added News
added II.mp3
added Big
added News.mp3
added Droid.mp3
added Escape
added from
..and so on

```

I've tried fixing it with awk and sed, but I can't make it stop doing that.  The spaces always end up being there even if I remove them  :mad:

---

