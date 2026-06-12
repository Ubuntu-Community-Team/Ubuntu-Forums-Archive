---
title: "problems with wine"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by pluskwa on 2007-01-26
Hi 
Im new to ubuntu and i've got a problem. i've installed wine but i can't copy anything to Program Files. I tried to change permission, but i can't changed it for Program Files. I get a message that's 
chmod: cannot access `/home/cis/.wine/drive_c/Program': No such file or directory
chmod: cannot access `Files': No such file or directory

What can I do

---

### Post by pizzutz on 2007-01-26
The shell does not recognize the whitespace as part of a file name.  you need to escape the space.  try ~/.wine/drive_c/Program\ Files and it will work

Any time a file name contains a character that the shell uses, such as *, \, [, ], (, ), a space or several other characters it needs to be "escaped" or preceded with a \ so the shell can recognize it as part of a filename.

Alternately, you can use tab completion and the shell will escape characters for you.  If you got as far as chmod 777 ~/.wine/drive_c/Pr   and then hit the tab key, the shell will finish Program\ Files for you.


Also this same problem is likely why you weren't able to copy into Program Files.  You should already have permissions to modify that directory as it is a subdirectory of you home folder.

---

### Post by pluskwa on 2007-01-26
thanks a lot,
one more question, 
i don't really know which chmod command is the best,
last time i put sth wrong and i'd screwed the system

---

