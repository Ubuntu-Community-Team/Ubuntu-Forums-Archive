---
title: "Copy only certain filetypes"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by 3zero2 on 2006-10-11
I wanted to ask this for quite a long time so here I go

I want to copy ONLY the mp3 files from a directory called WinMusic to another called Music. Both are in my HOME directory. Of course the command has to be recursive and copy the directory structure as well. Also there are no mp3 files in the WinMusic directory. All files are in subdirectories.

How can I do this? tried to use the cp command but i couldn't find a way.

any help would be appreciated. thanks

---

### Post by james.gornall on 2006-10-11
I believe it would be cp *.mp3 <directory>

the * being a wildcard and will match any file with .mp3 extension.

not sure though! I kno you will use a wildcard in there.

might wanna wait for more experienced reply first.

---

### Post by 3zero2 on 2006-10-11
> **james.gornall said:**
> I believe it would be cp *.mp3 <directory>

the * being a wildcard and will match any file with .mp3 extension.

not sure though! I kno you will use a wildcard in there.

might wanna wait for more experienced reply first.

thanks for your try but this would give me the following error:

```
cp: cannot stat `*.mp3': No such file or directory

```

---

### Post by james.gornall on 2006-10-11
err try it with the "." so just *mp3

---

### Post by 3zero2 on 2006-10-11
> **james.gornall said:**
> err try it with the "." so just *mp3

still no go. same error.

---

### Post by james.gornall on 2006-10-11
ah ok then, ill just give up.

I think I along the right lines ^^  ](*,)

---

### Post by 3zero2 on 2006-10-11
> **james.gornall said:**
> ah ok then, ill just give up.

I think I along the right lines ^^  ](*,)

thanks for your time anyway. it's much appreciated.

---

### Post by .t. on 2006-10-11
Some combination of for, cp, find and grep, I'd guess. I'm not too good at scripting, and I'm finding it hard to wrap my head around this... So, I'd like to know as well!

---

### Post by devnulljp on 2006-10-11
> **3zero2 said:**
> thanks for your time anyway. it's much appreciated.

Can you do ls on the directory containing the mp3 files?
Do you see output like 
file1.mp3
file2.mp3
 
cp *.mp3 should work, unless their names are all in caps or you're not actually in that directory or sthg.

---

### Post by james.gornall on 2006-10-11
oo so I was right, im so proud of my self!

lol I'm giving my self a cookie... 8) 


> thanks for your time anyway. it's much appreciated.

Np mate, I'm at work.  not doing anything interestin!

---

### Post by devnulljp on 2006-10-11
> **3zero2 said:**
> I want to copy ONLY the mp3 files from a directory called WinMusic to another called Music. <snip>

Just re-read your post properly and saw that you're trying to copy mp3 files in subdirectories not loose in the cwd.

try this from your home directory:

```
find WinMusic -type f -name '*.mp3' | xargs -n 10 -i cp {} Music

```

Although that will dump them all loose into your destination directory

How about copying the whole WinMusic directory to Music then deleting everything in Music that's not mp3?

```
cp -r WinMusic Music;
find Music -type f | grep -v 'mp3' | xargs rm

```

The only other alternatives I can think of are complicated shell functions or perl/python scripts

---

### Post by 3zero2 on 2006-10-12
thanks all for your help

i have done it using the robocopy utility in windows!!

I'm sorry i didn't manage under linux - seems to be a bit more complicated than a ```
ROBOCOPY /E E:\WinMusic E:\Music *.mp3
```

will try to find a robocopy for linux - there MUST be something.

---

### Post by anaconda on 2006-10-12
How about this?
cp -R ~/WinMusic/*.mp3 ~/Music

---

### Post by devnulljp on 2006-10-12
How about rsync?
```
rsync -ravz --exclude=*.ogg --exclude=*.jpg --include=*.mp3 WinMusic/  Music

```

That'll do it (with additional --excludes for any other filetypes in there, like m3u, wav, flac, whatever)

---

### Post by .t. on 2006-10-12
Never mind. I'm a tad late...

---

### Post by 3zero2 on 2006-10-12
yes i was reading that rsync is the equivalent of robocopy. will give it a try just to learn

---

### Post by 3zero2 on 2006-10-13
> **devnulljp said:**
> How about rsync?
```
rsync -ravz --exclude=*.ogg --exclude=*.jpg --include=*.mp3 WinMusic/  Music

```

That'll do it (with additional --excludes for any other filetypes in there, like m3u, wav, flac, whatever)

you're the man. that works. cheers.

---

