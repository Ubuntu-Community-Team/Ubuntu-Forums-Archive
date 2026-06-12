---
title: "how to untar alsa file"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by awashington on 2008-03-29
anybody know the command to untar the alsa file once you download it from alsa project.org:x

---

### Post by Joeb454 on 2008-03-29
Yep, to use it you need to use CD to move to the directory...let's say it's on your Desktop.

```
cd ~/Desktop
tar -xzvf ./<name of the tarred file>

```

Where <name of the tarred file> is obviously the name ;)

---

### Post by awashington on 2008-03-29
got an error msg:  tar -xzvf ./alsa-driver-1.0.16.tar.bz2
                            tar: ./alsa-driver-1.0.16.tar.bz2: Cannot open: No such file or directory
                            tar: Error is not recoverable: exiting now
                            tar: Child returned status 2
                            tar: Error exit delayed from previous errors

---

### Post by Joeb454 on 2008-03-29
This'll sound really stupid, but you're sure you're in the correct directory?

---

### Post by awashington on 2008-03-29
not stupid at all...i'm not sure which directory it's in i'm at my home directory

---

### Post by Joeb454 on 2008-03-29
Where is the file located? Visually navigate to the file, and tell me where it is, and I'll give you the code to run :)

---

### Post by awashington on 2008-03-29
ok I guess i'm an idiot cuz I can't find it but i know it installed because it said to save to archive or something of the sort

---

### Post by Joeb454 on 2008-03-29
Download it again and save it to your desktop, then run the commands I posted above :) It'll be untarred then :)

---

### Post by Catalyst2Death on 2008-03-29
if it's firefox, and your running default settings, it would put it on the desktop.. in which case you would have to use the commands above.. however when I untar a tar it goes something like this:

cd <directory containing tar>
tar -xvf <file>.tar

I don't know why your using the ./ switch... it would generate errors right?!  I just tried it on my desktop using the above commands, and it extracted fine.
then you can cd into the directory

---

### Post by Joeb454 on 2008-03-29
Well I'm sure the OP can try it without the ./ if needs be :)

---

### Post by rkd on 2008-03-29
> **Catalyst2Death said:**
> 
I don't know why your using the ./ switch... it would generate errors right?

The ./ is not a switch.  It was ./filename -- a path.  The . is the symbol for the current directory. So ./filename is exactly the same as filename would be.  The ./ isn't necessary in this case, but there are times when if you don't give a path, a program will have some other directory in which it will look for a simple name, and it wouldn't find the file in the current directory.

---

### Post by awashington on 2008-03-29
Tri-Boot-Laptop:~$ cd /desktop
bash: cd: /desktop: No such file or directory
 

thats my error msg

---

### Post by rkd on 2008-03-29
Two errors in that command.  It should be

   cd ~/Desktop

Note: capitalization matters.

---

### Post by awashington on 2008-03-29
thanks catalyst2death. I think that worked so do i need to shut down now or should i work fine now

---

### Post by awashington on 2008-03-29
thanks that helped didn't think capitalization mattered

---

### Post by Catalyst2Death on 2008-03-29
I did not realize the detail about the ./ declaration (what is its formal name?) 

I didn't mean to upset anyone, I just had never encountered that particular syntax, and I naively thought that it may be a source of the errors.

---

### Post by Joeb454 on 2008-03-29
./ means current directory :)

---

### Post by rkd on 2008-03-29
No, Joe, ./ does not mean current directory.  The . by itself means current directory.  The / is just the usual separator between parts of a path.  You know, like /home/joe/Desktop

---

### Post by Joeb454 on 2008-03-29
:lolflag: Yeah that's what I meant :D But to use it to execute a file/app then you need ./ because . also means a hidden file ;)

---

### Post by rkd on 2008-03-29
Uhh, I don't think so.  A hidden file just is one that has a . as the first character of its name.  I think you can run such a file just by typing its name, dot and all.  The . only means current directory when it is the only thing in its part of a path.  And if you wanted to refer to that hidden file the longer way, you would have two dots: ./.filename  

(Similarly, .. as the only thing in its part of a path means the directory that is the parent of the current directory.)

Or did I misunderstand what you meant in your most recent post?

---

### Post by Joeb454 on 2008-03-29
No I was stating the use of .

Which is . The current directory

**AND**

.file A hidden file

---

### Post by rkd on 2008-03-30
Right, a . by itself is different than a . at the beginning of a filename.  A . at the beginning of a filename is just another character in the filename, just like the . in file.html is just another character in the filename.  It is just that ls, by default, doesn't list files whose names start with .  (but the -a switch overrides that).

But you said a few posts ago that one had to use ./ to run a file in the current directory because . at the start of a name meant it was hidden, and as far as I know, the latter part of that statement is incorrect.  

If you want to run file in the current directory, you often can't just type file because the current directory often is not in the search path.  So you type ./file to give a full path rather than a simple file name.  When you give a full path, it doesn't need the search path. Has nothing whatever to do with . at the start of a file name telling ls not to list it.

If the current directory is in the search path, you can type just file to run file, or you can type just .file to run .file and the initial . in that case has nothing to do with the current directory.

Does that make sense?

---

