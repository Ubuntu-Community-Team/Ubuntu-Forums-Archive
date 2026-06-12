---
title: "how do I unzip multiple files at once?"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by mlwalla on 2006-12-02
this is probably a really stupid question, but I have a directory with a whole bunch of .zip files in it that I would like to unzip all at once.
the command ```
unzip *.zip
``` in the directory just returns a long list of  ```
caution: filename not matched:  xyz.zip
```  am I doing something wrong?

---

### Post by Jussi Kukkonen on 2006-12-02
unzip doesn't allow many filenames as input. Try this:
```
for file in `dir *.zip` do 
unzip $file
done
```

---

### Post by lamego on 2006-12-02
The command that you were using was doing:
unzip file1.zip file2.zip...
which means it should extract file2.zip from file1.zip, thats not what you want.
You can call unzip for each *.zip file with:
```
ls *.zip | xargs -n1 unzip 
```
Make sure you keep te space at the end of the line (after the unzip command).

---

### Post by mlwalla on 2006-12-02
Thanks for the input, but I still don't quite have it yet..

Jussi, when I use your suggestion I get 
```
bash: syntax error near unexpected token `unzip'

```  

lamego, when I tried yours I got ```
No zipfiles found.
xargs: unmatched single quote; by default quotes are special to xargs unless you use the -0 option
```
basically all the files have spaces in their names which the xargs man page says is problematic, but adding option -0 by typing ```
ls *.zip | xargs -n10 unzip
``` came back with basically the same error ( both times it also spits out unzip's info page and seemed to be looking for the last word in the file +.zip.  If the file were "ab c.zip" it would look for "c.zip")

am I using the option syntax wrong?  Or would it be easier to just rename all the files to remove spaces- and if so how do I do that?

Thanks again for the help

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-12-16
> **lamego said:**
> The command that you were using was doing:
unzip file1.zip file2.zip...
which means it should extract file2.zip from file1.zip, thats not what you want.
You can call unzip for each *.zip file with:
```
ls *.zip | xargs -n1 unzip 
```
Make sure you keep te space at the end of the line (after the unzip command).

Thanks man! Worked perfectly!

---

