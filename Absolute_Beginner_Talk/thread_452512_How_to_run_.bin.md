---
title: "How to run .bin?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-05-23
How do you run .bin files from the Terminal?

---

### Post by LaRoza on 2007-05-23
Navigate to their directory and type their name, for myFile.bin located in folderone on the desktop, type:

$ Desktop/myFile.bin

            OR

$cd Desktop
$myFile.bin

---

### Post by Sparkster185 on 2007-05-23
Do you mean binary executables?  If the directory is in your PATH, then simply type the name of the executable.  If not, you need to provide a path to the executable. Example:

/home/clarkb/programs/tester

or you can use relative paths

cd /home/clarkb
./programs/tester

---

### Post by bobbocanfly on 2007-05-23
Thanks :D

---

### Post by baseballguy on 2008-05-13
From my experience this is a dependency issue. The adobe bin does not tell us what the dependencies we need to install to make the bin application to run.



[http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?forumid=72&catid=677&threadid=1350557&enterthread=y#4909516](http://www.adobe.com/cfusion/webforums/forum/messageview.cfm?forumid=72&catid=677&threadid=1350557&enterthread=y#4909516)


AIR requires at least GTK 2.4.x to be installed. Could you try upgrading your system's GTK?

It will now install!!!

---

