---
title: "cp - target is not a directory"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by bpdp on 2006-10-31
Hello
I'm taking a Linux class and were writing some bash scripts. Though they may not be the most useful scripts;) 

anyway i was wondering if someone could have a look at my file and let me know what i'm doing wrong. 

when it jumps to the else statement i get an error: target "filename.txt" is not a directory.

Thanks for any help you could give me.

```
#!/bin/bash
#
############################
#Backup files user inputs
#file extension
#####################
#
echo "Enter a file extension: "
read fileEx
echo "Creating backups of: "
#
ls *.$fileEx
buFiles=$(ls *.$fileEx)
#
echo "Would you like to tar these files: "
#
read uInput
if [ $uInput == y ]; then
   myDate=$(date +%m_%d_%Y)
   tar -cvf backUp-$myDate.tar $buFiles
else
   cp $buFiles ${buFiles}.bu 
fi
#



```

---

### Post by Marsolin on 2006-10-31
It looks like you are trying to copy files to files instead of to a directory. What do you want to do with the cp command. Adding a .bu extension to the target won't work.

---

### Post by bpdp on 2006-10-31
Thanks for your reply.
The script is to ask the user for a file ext and then make a copy of all the files (in the current directory) with that ext and add the .bu

ex:
"enter a file extension:"
USER INPUTS: txt
"a backup will be made of these files:"
fileone.txt
filetwo.txt
filethree.txt
"would you like to tar them:
USER INPUTS: n
-- this is were i get the error

if everything worked an ls should show:
fileone.txt filetwo.txt filethree.txt
fileone.txt.bu filetwo.txt.bu filethree.txt.bu

Does that make any sense. Again Thank you for your time.

---

### Post by po0f on 2006-10-31
bpdp,

You will have to move the files one by one into their *.bu file, not all in one go.  If more than two files/directories are listed as arguments to cp, all of the arguments except the last one are moved into the last one;  that is why you are getting the "target is not a directory" error, you can't move multiple files into another file.

I don't know bash very well, but maybe the following would work (very untested :D):
```
for file in $buFiles
  cp $file $file.bu
done
```

---

### Post by bpdp on 2006-10-31
That makes almost too much sense. I can't believe I didn't think of that, It's been driving me crazy. I'll test it when i get home. thank you very much!!!!

---

