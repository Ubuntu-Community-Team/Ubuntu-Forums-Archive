---
title: "need a little command help"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by cryo4.rm on 2007-08-02
sorry.--- i've just about got used to linux but im still not quite up to writing my own codes... but i will put my head to it soon

 i need a little command...

 have a big music library full of MP3s and AACs all mixed up -- want to convert it all to MP3 so it will play on my MP3-portable thing, i need a code to find all the AACs and stick em in a new, separate folder so i can  convert them

 any one able to help??

 thankyou... joe

---

### Post by Papi-KB7VGW on 2007-08-02
It has been awhile but from cli

[HTML]mv /my/old/dir/*.aac /my/new/dir/*.aac[/HTML]

or in Nautilus show the files as list then sort on file type to separate them.  Then cut and paste into new dir.  

If you decide on the first one, let me know how it worked.:)

---

### Post by Rocket2DMn on 2007-08-02
I'm not sure that command will work, I don't think you can use the * wildcard as a destination.  You will need a shell script to do that.  I suggest just using nautilus if everything is in one folder.

---

### Post by cryo4.rm on 2007-08-02
sorry.... 

 i wasn't specific enough ----- the files are actually distributed throughout a plethora of subdirectories (artist, album ETC) .. 

 can i get nautilus to list all the files contained in all the subdirectories of a single folder?

---

### Post by Papi-KB7VGW on 2007-08-02
Since they are all over.  You could use the search function to find them but I think that you can only open the folder to cut & paste.  I'm sure that a script would work but that part of my knowledge base is very small..

---

### Post by asmoore82 on 2007-08-02
```
~ $ find music/ -iname '*.aac' | tee aacfiles.txt
```

will get you started...

---

