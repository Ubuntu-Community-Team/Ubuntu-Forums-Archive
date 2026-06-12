---
title: "a command to dump ALL file names (incl. subfolders) into text file"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by molly_001 on 2007-06-25
Hello --

Is there a command I could use in terminal (or a handy gnome apt maybe)
to dump to a text file or on-screen display, of *ALL* the files in a device
or high-level directory.

For instance, let's say I have this:


   ext3
     |
      \
        --  /home
.  .  .       |
.           .  . |-  important_docs  (folder) ( 7 files)
. . . |-  wedding_pics     (folder) ( 30 files)
                   . . . |-  passport_stuff    (folder) ( 10 files)

What I am looking for is a way to dump to text file or other on-screen display,
of a listing of all 47 files in that entire directory to look at all 47 lines at once.

Thanks !!!!!!

---

### Post by punx45 on 2007-06-25
i think ls has a recursive switch, which would dive down into all subdirectories.   i dont have a shell at the moment so i cant double check that.   read the man page for ls and look for a -r or -R option.   

then you can redirect the output into a file with >

so it would hypothetically look like:
```
ls -R /dir > file.txt
```

thats if you want to keep the list. if you just want to read it you can pipe the output into less or more with a |
which would look like:
```
ls -R /dir | less
```

this would allow you to scroll through the output by the line or screen, as well as search through it.   read the man page for less (or more) for details on how to use them.   they are very handy!

---

### Post by Rocket2DMn on 2007-06-25
That is indeed correct, I have just checked it for you.

---

### Post by molly_001 on 2007-06-25
Thanks to you both - that is incredibly helpful of you.

---

### Post by HermanAB on 2007-06-25
The find command is very good for recursing through stuff and calling a command when a match is found.  The man page explains it quite nicely.

This example will recursively search for OGG files and convert them to MP3 using sox to do the conversion:
find . -name \*.ogg -print -exec sox {} {}.mp3 \;

Cheers,

Herman

---

### Post by punx45 on 2007-06-25
wow, i even got the case right :)

once just for fun i
 ls -R /    

after a few minutes of churning and scrolling text I put the poor process out of its misery.

---

### Post by _user1_ on 2007-06-26
_user1_ also thanks you.

---

### Post by olejorgen on 2007-06-26
sudo apt-get install tree
```

$ tree /var/lib/bandwidthd/
/var/lib/bandwidthd/
|-- htdocs
|   |-- 192.168.1.100-2-R.png
|   |-- 192.168.1.100-2-S.png
|   |-- 192.168.1.102-1-R.png
|   |-- 192.168.1.102-1-S.png
|   |-- 192.168.1.102-2-R.png
|   |-- 192.168.1.102-2-S.png
|   |-- 192.168.1.102-3-R.png
|   |-- 192.168.1.102-3-S.png
|   |-- 203.10.76.45-2-R.png
|   |-- 203.10.76.45-2-S.png
|   |-- Subnet-1-128.0.0.0.html
|   |-- Subnet-2-128.0.0.0.html
|   |-- Subnet-3-128.0.0.0.html
|   |-- Subnet-4-128.0.0.0.html
|   |-- Total-1-R.png
|   |-- Total-1-S.png
|   |-- Total-2-R.png
|   |-- Total-2-S.png
|   |-- Total-3-R.png
|   |-- Total-3-S.png
|   |-- Total-4-R.png
|   |-- Total-4-S.png
|   |-- index.html
|   |-- index2.html
|   |-- index3.html
|   |-- index4.html
|   |-- legend.gif
|   `-- logo.gif
|-- log.1.0.cdf
|-- log.2.0.cdf
|-- log.3.0.cdf
`-- log.4.0.cdf

1 directory, 32 files

```

---

### Post by molly_001 on 2007-06-26
Thanks to you all, this was very helpful.
I decided to install application "tree" but the ls command
information would also have done the trick.
Great learning for me -- again, thanks.

---

### Post by punx45 on 2007-06-26
tree looks prettier.   i was not aware of it, but now i think im gonna get it !

---

### Post by walmartshopper67 on 2008-01-10
Sorry to resurrect this old thread, but just for anyone searching for this in the future the command ```
ls -R
``` will go through recursively and list all the files **EXCEPT** hidden directories/files (with a dot (.) prefix), to do that you'll need the -a option (all) or -A (almost all, includes the dot but ignores the implied . and .. directories).

so it would be ```
ls -Ra
``` or ```
ls -RA
```

---

### Post by stchman on 2008-01-10
> **molly_001 said:**
> Hello --

Is there a command I could use in terminal (or a handy gnome apt maybe)
to dump to a text file or on-screen display, of *ALL* the files in a device
or high-level directory.

For instance, let's say I have this:


   ext3
     |
      \
        --  /home
.  .  .       |
.           .  . |-  important_docs  (folder) ( 7 files)
. . . |-  wedding_pics     (folder) ( 30 files)
                   . . . |-  passport_stuff    (folder) ( 10 files)

What I am looking for is a way to dump to text file or other on-screen display,
of a listing of all 47 files in that entire directory to look at all 47 lines at once.

Thanks !!!!!!

Do the following:

```
ls -lR > ~/files_list.txt
```
  
This will create a text file in your home folder with a list of all the files in whichever directory you are currently in.  The -lR is for list and recursive.  The > redirects the output to a file.

---

