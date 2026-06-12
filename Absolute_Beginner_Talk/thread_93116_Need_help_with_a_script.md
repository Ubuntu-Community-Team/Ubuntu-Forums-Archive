---
title: "Need help with a script"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by eighto2 on 2005-11-21
So i'm in class rite now, and our assignment is this:
You will write a script that will:
Request a new file name to be entered at the prompt
It will then create that file so that it contains the info in your home directory.
It will then sort the contents of the file alphabetically based on the names of files
It will then create a new file that contains only the names of the files
It will then print out the original file created, the file that is just the list of file names, and your script file I'm tottaly clueless here, and my instructor says we're on our own, help please :)

---

### Post by xmastree on 2005-11-21
Start with #!/bin/sh

:)

---

### Post by eighto2 on 2005-11-21
edit: nevermind people. Here's my finished product:
echo -e "Please enter a file name"
read output
ls -l > $output
echo -e "Please enter ANOTHER file name"
read output2
ls > $output2
date >> $output
date >> $output2
date >> script
echo "Made by Frank" >> $output
echo "Made by Frank" >> $output2
echo "Made by frank"  >> script
lp -d lp2 $output
lp -d lp2 $otuput2
lp -d lp2 script

---

