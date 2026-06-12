---
title: "scripting: adding filename to end of cat line"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by ki1ian on 2007-12-20
Hi,

I'm using the cat command to concatenate a load of m3u playlists into one file and I was wondering if it's possible to add the filename to the end of each line separated by a symbol like '{'?

e.g.

in playlist1.m3u there are two lines:
/path/file.mp3
/path/file2.mp3

in playlist2.m3u there are two lines:
/path2/file3.mp3
/path2/file4.mp3

If I then type cat *.m3u > output.txt

I get in the output.txt file:
/path/file.mp3
/path/file2.mp3
/path2/file3.mp3
/path2/file4.mp3

But what I'd like to achieve is:
/path/file.mp3{playlist1.m3u
/path/file2.mp3{playlist1.m3u
/path2/file3.mp3{playlist2.m3u
/path2/file4.mp3{playlist2.m3u

Thank you in advance,
Ki1ian

---

### Post by PeterJS on 2007-12-21
```

#!/bin/bash

FILENAMES=`ls *.m3u`

for FILE in $FILENAMES
do
    awk "{print \$0 \" [$FILE]\"}" $FILE
done

```

That should do it, Let me know if I didn't get something right.

---

### Post by ki1ian on 2007-12-21
An error message comes up saying:

line 4: syntax error near unexpected token `do
line 4: `do


Although this is the first time I've run a script so I might not be doing this right:

paste the code into an empty file called 'script' in the directory with all the m3u files.
type chmod 700 script in a terminal to make the script executable
then type bash script to run??

---

### Post by jordanmthomas on 2007-12-21
Try this:  it should at least run (though I am too tired to check if it does it correctly and I don't have any m3us handy to check)
```
#!/bin/bash

FILENAMES=`ls *.m3u`

for FILE in $FILENAMES; do
    awk '{print $0 " [$FILE]"}' $FILE
done
```

edit
This is really the same thing as above

---

### Post by nick_h on 2007-12-21
It would be better to use the awk FILENAME variable.

Try this:
```
awk '{ print $0 "{" FILENAME }' *.m3u > output.txt
```

---

### Post by ki1ian on 2007-12-21
Thank you all for your posts.

@ jordanmthomas: the script isn't fetching the filename and adds the text [$FILE] somewhere along the line.


@ nick_h:

Almost there, it's putting the filename on a new line (like)

/path/file.mp3
{playlist1.m3u
/path/file2.mp3
{playlist1.m3u
...

I could fix it afterwards with a find and replace but is there a way to tack on the end?

---

### Post by jordanmthomas on 2007-12-21
> **ki1ian said:**
> Thank you all for your posts.

@ jordanmthomas: the script isn't fetching the filename and adds the text [$FILE] somewhere along the line.


@ nick_h:

Almost there, it's putting the filename on a new line (like)

/path/file.mp3
{playlist1.m3u
/path/file2.mp3
{playlist1.m3u
...

I could fix it afterwards with a find and replace but is there a way to tack on the end?

I'm still not sure *exactly* what you're after, but this will help some.  I'm not tired any more so perhaps I can help now.
Alright, we'll use nick_h's and fix the newline problem.
```
awk '{ printf "%s\{%s\n", $0, FILENAME }' *.m3u > output.txt 
```

If you want a closing } just put \} before the \n (so the string will be "%s\{%s\}\n". ) You didn't mention you wanted one, but I think it belongs.  :)
This gives me output like what you said you wanted (hopefully it will for you too.  :lolflag:)


**EDIT**
Also, the reason what PeterJS posted didn't work is that $FILE wasn't  a variable in awk, but in bash.

---

### Post by nick_h on 2007-12-21
> I could fix it afterwards with a find and replace but is there a way to tack on the end?
Were the m3u files created in Windows?

Windows uses a CR+LF pair as an end of line character, but Linux and awk assume a single LF by default.  If this is the case you will be getting an extra CR (sometimes displayed as ^M) in each line.

You can test this with:
```
less output.txt
```

You can change the record separator in awk with the following:
```
awk -v RS="\r\n" '{ print $0 "{" FILENAME }' *.m3u > output.txt
```

An alternative would have been to substitute the CR with an empty string before output.

---

### Post by ki1ian on 2007-12-22
Folks it worked!

The files were created in windows.  Why does m$ have to make things so complicated?


Should anyone else in the forums find themselves in the same predicament(!), the final script is:


```
#!/bin/bash

FILENAMES=`ls *.m3u`
for FILE in $FILENAMES; do
awk -v RS="\r\n" '{ print $0 "{" FILENAME }' *.m3u > output.txt
done
```


I cannae tell you how much time these 5 lines have saved me.  Much appreciated guys, thank you!

---

### Post by nick_h on 2007-12-22
I'm glad that it works.

You don't need the loop now - the awk line will work on its own.  What you are doing is just running the same command multiple times.

---

