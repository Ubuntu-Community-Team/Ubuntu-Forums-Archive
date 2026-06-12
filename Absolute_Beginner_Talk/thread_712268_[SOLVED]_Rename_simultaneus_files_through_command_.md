---
title: "[SOLVED] Rename simultaneus files through command line"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by jflarm on 2008-03-01
Hi,
I want to rename files named in this way:
" 23565_somefile.avi "
There are many files like this, so I want to strip the "23565_" part and just keep the name of the file.
There are more than 50 files like this, and I know it can be done through the command line....and please, no scripts, because I want to improve my command line skills.
Some pointers would be nice....thank you!!

---

### Post by jflarm on 2008-03-01
hello...anyone????

---

### Post by disturbedite on 2008-03-01
give it some time man.

i think (not 100% sure) gwenrename (a batch/mass renamer with a gui) has command line capability also.

UPDATE:
sorry, i checked to confirm or deny my previous statement, and it appears gwenrename does not have command line capability.  perhaps another batch/mass renamer does, such as krename.

---

### Post by owbizi on 2008-03-01
Well, look at [this](http://ubuntuforums.org/showthread.php?t=127740) and [that](http://www.go2linux.org/rename-bulk-files-with-linux-console-command)... a little more complicated, but still can do what you want, I think. :)

---

### Post by jflarm on 2008-03-01
Thank you, I'll check the links and will reply with resuts!!
=====================================
This rename utility is what I have to use!!!....thank you owbizi !!!

---

### Post by jflarm on 2008-03-02
for i in *.flv;do k=`echo $i|sed 's/^[0-9]*_//g'`;mv $i $k;done
I did this to strip the numbers and underscore from the beginning of file names.
And also did this other command to change the underscores for spaces:
for i in *.flv ;do k=`echo $i|tr '_' ' '`;mv $i "$k";done

I did this because I do not know perl, and the rename utility demanded some knowledge I don't have. Anyway, found my self something else to study....PERL !!!

---

