---
title: "Listing and Comparing files"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Gwasanaethau on 2007-08-08
Hi all!

I have two directories on my computer with some similar files in them. Most have identical filenames, but I want to find out whether their contents are also identical. I tried using the commands:
```
for i in $(ls -Q)
do FILE=$(ls -Q /second/directory | grep "$i")
if [ "$FILE" = "" ]
then echo "$i not found"
else echo "$i found"
     cmp "$i" /second/directory/"$i"
fi
done

```
I ran this from within one of the directories whose files I wanted to compare. This works fine provided there are no spaces in the filenames. Does anyone know a way of getting files with spaces to work too (without changing the filenames)?

(The root of the problem seems to stem from the 'for' command using a space to signal the end of one variable and the start of the next).

---

### Post by garlito on 2007-08-08
> **Gwasanaethau said:**
> Hi all!

I have two directories on my computer with some similar files in them. Most have identical filenames, but I want to find out whether their contents are also identical. I tried using the commands:
```
for i in $(ls -Q)
do FILE=$(ls -Q /second/directory | grep "$i")
if [ "$FILE" = "" ]
then echo "$i not found"
else echo "$i found"
     cmp "$i" /second/directory/"$i"
fi
done

```
I ran this from within one of the directories whose files I wanted to compare. This works fine provided there are no spaces in the filenames. Does anyone know a way of getting files with spaces to work too (without changing the filenames)?

(The root of the problem seems to stem from the 'for' command using a space to signal the end of one variable and the start of the next).


Try this, assuming you are using bash:

```
for i in *; do
   file=/second-directory/$i
   if [[ -e $file ]]; then
      cmp "$i" "$file"
   else
      echo "$i" not found
   fi
done

```

---

### Post by Gwasanaethau on 2007-08-09
> **garlito said:**
> Try this, assuming you are using bash:

```
for i in *; do
   file=/second-directory/$i
   if [[ -e $file ]]; then
      cmp "$i" "$file"
   else
      echo "$i" not found
   fi
done

```

I made a work-around by creating a textfile that listed all the files in the first directory, and then used that to feed them into a while loop. However, your suggestion makes an awful lot more sense! Thanks a million!

---

