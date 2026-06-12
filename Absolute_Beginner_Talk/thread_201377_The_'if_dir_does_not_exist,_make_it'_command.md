---
title: "The 'if dir does not exist, make it' command"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-06-21
Okay, you know how you try to copy something to a folder, but that folder does not exist?  Thus it would return with a error prompt.  How do I make it so that if it does not exist, just make it.

So lets assume this is what I have at home:
```

/bin
/notes
 file1
 file2
```

I want to copy file2 to '~/newfolder/subfolder/'.  This normally would require me to do
```

mkdir newfolder
mkdir newfolder/subfolder
cp file2 newfolder/subfolder
```

Is there a command that I can use that will copy file2 to ~/newfolder/subfolder, and it the folders do not exist, it would automatically make it.

So the result yield would be
```

/bin
/newfolder (with subfolder/file2 in it)
/notes
 file1
```

---

### Post by gerbman on 2006-06-21
[QUOTE=tux101]Okay, you know how you try to copy something to a folder, but that folder does not exist?  Thus it would return with a error prompt.  How do I make it so that if it does not exist, just make it.

So lets assume this is what I have at home:
```

/bin
/notes
 file1
 file2
```

I want to copy file2 to '~/newfolder/subfolder/'.  This normally would require me to do
```

mkdir newfolder
mkdir newfolder/subfolder
cp file2 newfolder/subfolder
```

Is there a command that I can use that will copy file2 to ~/newfolder/subfolder, and it the folders do not exist, it would automatically make it.

So the result yield would be
```

/bin
/newfolder (with subfolder/file2 in it)
/notes
 file1
```[/QUOTE]I don't think there is a way to do all that with the cp command, but if you pass the -p option to mkdir it will make all needed parent directories...might save you a step or two.

---

