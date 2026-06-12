---
title: "[SOLVED] delete all desktop.ini"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by laxmidd50 on 2007-10-25
I copied my music collection over from my windows computer and all the folders have dektop.ini files.  Does anyone know a command to go through and delete all of those files? (Theres way too many to do it individually).  The path is /home/nowa/Music.

---

### Post by TeaSwigger on 2007-10-25
Well in Kubuntu I'd open KFind and search the lot for desktop.ini; it'd list 'em, then I'd delete 'em from there. Can't remember the Gnome search for ubuntu off the top of my head but you should be able to do it similarly.

---

### Post by kebes on 2007-10-25
> **laxmidd50 said:**
> I copied my music collection over from my windows computer and all the folders have dektop.ini files.  Does anyone know a command to go through and delete all of those files? (Theres way too many to do it individually).  The path is /home/nowa/Music.

This should work:
```
cd /home/nowa/Music
for file in `find -name desktop.ini`; do rm $file; done
```


Explanation: The part `find -name desktop.ini` (important: those are backticks, not quotes!) finds all files in the current directory (and sub-directories) that have a name that matches "desktop.ini". Then the for-loop (for ... in ...; do ...; done) iterates over each one of those entries, and deletes that file (using the rm command).

Hope that helps.

---

### Post by MegaJim on 2007-10-25
Personally, I would use:

```
find /home/nowa/Music -name desktop.ini -exec rm -i {} \; 
```

it'll ask you before each delete (just to be on the safe side).  If you're confident however, remove the "-i" after the rm statement!

find (the find command) /home/now/Music (the path to search) -name (specifies the next word is the filename to search for) desktop.ini (the filename) -exec (passes the results of this find on to the next command) rm (the remove/delete command) -i (interactive mode, prompts on each file delete) {} (where the arguments collected by exec are placed) \ (ends the exec statement) ; (tells the shell to start work)

---

### Post by laxmidd50 on 2007-10-25
The first one semi-worked. It seems that it didn't work for any folders that have spaces in the name (which is most).

---

### Post by laxmidd50 on 2007-10-25
Megajim's command worked for the directories with spaces. Thanks everyone for the help!

---

### Post by MegaJim on 2007-10-25
You are welcome, please mark the topic as [solved]

---

