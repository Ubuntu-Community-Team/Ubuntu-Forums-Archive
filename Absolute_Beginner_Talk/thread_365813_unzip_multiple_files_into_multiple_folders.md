---
title: "unzip multiple files into multiple folders"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Ashrael on 2007-02-20
A good day to you all!

I'm trying to figure out how to unzip multiple files into multiple dirs, where the dir's name is filename... I looked around on the net for a while, studied man unzip, tried all sorts of things, and still i'm not anywhere near ](*,) 

anybody know how to do this? would be appreciated.....


Ashrael

---

### Post by Jussi Kukkonen on 2007-02-20
> **Ashrael said:**
> A good day to you all!

I'm trying to figure out how to unzip multiple files into multiple dirs, where the dir's name is filename... I looked around on the net for a while, studied man unzip, tried all sorts of things, and still i'm not anywhere near ](*,) 


Your spec is not entirely industrial scale (I'm not sure which filename you wanted to use as the dirname), but if it was the zip name that was supposed to be used this script will get you started in the right direction:

```
#!/bin/sh
for FILE in *.zip; do 
        DIR=$(basename "$FILE" .zip)
        mkdir "$DIR"
        unzip "$FILE" -d "$DIR"
done

```

---

### Post by Ashrael on 2007-02-20
THANX! works like a charm! Had to canibalise your script , because some archives were damaged, so i changed it to test zips...so here it is: 

#!/bin/sh

for FILE in *.zip; do
   unzip -tqq $FILE
done

So for all you like me: 

1) create 2 files using texteditor, ziptest.sh and batchunzip.sh (name them whatever you like)
2) copy Jussi's script, save as batchunzip.sh in the directory containing your zip files.
3) copy above script, save as ziptest.sh, in the same dir.
4) copy some zip files and the two scripts to a test folder (just to avoid a mess, ;) )
5) open a terminal window and type:  chmod a+r ziptest.sh && ./ziptest.sh (it will go off, and only give you output on damaged zip files, remove them from the dir)
5) in the testfolder again...type:   chmod a+r batchunzip && ./batchunzip.sh
 If all goes well, you wil have folders named after the zip files containing the files from the zipfile...
6) now give step 5 a try in your original zip dir....

...... ;) must learn, must learn, must learn... :) I mean: they can be put togheter, but i'm happy already...it worked for me....

---

### Post by Ashrael on 2007-02-20
Still rewriting the script

```
#!/bin/sh


for FILE in *.zip; 

do
	if  zip "$FILE" -d "$DIR" > /dev/null 2>&1
	then echo $FILE" is defective"
	elif ! zip "$FILE" -d "$DIR" > /dev/null 2>&1
	then DIR=$(basename "$FILE" .zip);  mkdir "$DIR"; unzip -qq "$FILE" -d "$DIR"
	
	fi
done
```

I haven't figured out why the echo $FILE isn't working...But at least it does what it's supposed to unzip wise.. tips are still welcome... :lolflag:

---

### Post by Sutur on 2008-01-20
There is a faster way I found [here]("http://www.cyberciti.biz/faq/linux-unix-shell-unzipping-many-zip-files/").

So instead of:

```
unzip *.zip -d DIRECTORY
```

Just add quotes so the bash ignores the wildcard:

```
unzip '*.zip' -d DIRECTORY
```

Done.

---

### Post by ranpha on 2008-05-19
Is it also possible to unzip files in subdirectories and that they unzip in that subdirectory

I foudn this
find -name *.zip -exec unzip {} \; 

But that will find everthing then unzip everthing in one big directory which i don't want

With the script above i get error messages that the *.zip has not been found

---

### Post by vanadium on 2008-05-19
use the option "execdir" instead.

---

