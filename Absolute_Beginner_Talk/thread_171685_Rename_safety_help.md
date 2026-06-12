---
title: "Rename safety help"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-05-07
I need some help writing some kind of safety mechanism for renaming files in order to avoid overwriting existing files.

Lets assume there is a file in the directory called 'tux100.foo' that I am not aware off.  While there is another file that I would like to rename to 'tux100.foo' by using 'mv whatever.foo tux100.foo'  This normally would overwrite it and I would not be aware of it!

I know I can just use 'mv -i' instead as a safety precaution.  But I would like to take it to the next step and have it do it automatically.

So how can I make it if there is an existinting file of the same name it would then automatically rename it to something +1?  So assume again there is the 'tux100.foo', I would want to rename another file to 'tux100.foo', but I get prompted that there is an existing file, so it automatically renames it to 'tux101.foo' for me.

How would I do the +1 thing along with making a custom message telling me there is already a file of the that name so it has automatically changed to whatever?

---

### Post by Nikusan on 2006-05-07
You want a bash alias. Try [this thread]("http://ubuntuforums.org/showthread.php?t=169454").

---

### Post by kabus on 2006-05-07
My attempt. I chose to just append a number to the filename because it's easier and less filename-specific.
A general mv safety wrapper that can rename files from 'tux100.foo' to 'tux101.foo' will only work if you stick to a strict filenaming convention for all your files or if you write a very clever script. :)


```
#!/bin/bash
source="$1" #  file to be renamed = first command line argument
target="$2" #  target filename = second command line argument
i=0
if [ -f "$target" ]; then # if filename is already used append a number
  echo "File $target exists !"
  until [ ! -f "$target.$i" ]; do
    i=$(( $i + 1 ))
  done
  echo "Moving $source to $target.$i"
  mv  "$source" "$target.$i"
else # otherwise just do a normal mv
  mv  "$source" "$target"
fi
```

---

