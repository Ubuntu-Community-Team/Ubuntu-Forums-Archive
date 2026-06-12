---
title: "find and replace a word in all the files in a folder on the server?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-07-15
this might not be the best place to post this question. but it is a linux related query.

on a site hosted on a linux server. i need to replace a word/phrase with a new one.

the word need to be replaced with another word in all the php files located inside a particular folder.

i think there are tools in linux which can be used for exactly this purpose.

so what command would i be required to run on the server which i can access through ssh/putty.

any suggestions would be appreciated! 

thanks.

---

### Post by machoo02 on 2007-07-15
I think the command you are looking for is sed.```
man sed
``` for usage, or check out a [sed tutorial]("http://www.grymoire.com/Unix/Sed.html").

---

### Post by Sushubh on 2007-07-15
pretty cool... 

i with try to test it out. but if someone can give me a properly coded command to do what i need would be awesome...

---

### Post by Sushubh on 2007-07-15
>  find ./ -name "*.php" -type f -exec sed -i 's/string1/string2/g' {} \;



looks like this thing works for me!

---

