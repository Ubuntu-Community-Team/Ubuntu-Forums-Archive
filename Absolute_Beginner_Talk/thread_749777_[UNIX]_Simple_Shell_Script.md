---
title: "[UNIX] Simple Shell Script"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by xItachi on 2008-04-08
Hi I need a simple shell script to rename some files.  I have a folder filled with all *.mp3's and the filename of every *.mp3 has ".www.website.com" at the end of it, so it looks something like this:

Artist1 - Song1.[www.website.com.mp3](www.website.com.mp3)
Artist2 - Song2.[www.website.com.mp3](www.website.com.mp3)
Artist3 - Song3.[www.website.com.mp3](www.website.com.mp3)

I need a script that will take off the ".www.website.com" by renaming:

Artist1 - Song1.mp3
Artist2 - Song2.mp3
Artist3 - Song3.mp3

Thanks.

---

### Post by neurostu on 2008-04-08
I personally don't have script written that will handle that; however, it should be that difficult. I would recommend looking at this google query:
[http://www.google.com/search?aq=f&hl=en&safe=active&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=uJ4&q=shell+script+file+rename&btnG=Search&lr=lang_en%7Clang_fr](http://www.google.com/search?aq=f&hl=en&safe=active&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=uJ4&q=shell+script+file+rename&btnG=Search&lr=lang_en%7Clang_fr)
and reading the hits. They all touch on what you're trying to do and should shed some light on how to do it!

---

### Post by renewip on 2008-04-08
good luck!

```
for i in *.mp3; do mv "$i" "`echo $i | sed -e 's/www.website.com//gi'`"; done
```

---

### Post by checht on 2008-04-08
Hey,  this should generate a script to do what you want.

ls *.mp3 | sed 's/^\(.*\)www\.website\.com\.\(.*\)$/mv & \1\2/' > rename.sh 
bash rename.sh

ls *.mp3 lists all of your mp3s in whatever directory you're in, the listing is then piped to sed,
where a substitute is done; the match saves the first part leading up to [www.website.com](www.website.com), and the part after, the mp3.  The match is replaced with "move [match] firstpart.lastpart, which is then redirected to a script that you can run.  You can check to see that the script looks good before running it with "bash rename.sh," or you could add #!/bin/sh to the top, do a chmod +x on the file, and run it with ./rename.sh.

A nicer solution would have been to use the backquotes to run the listing as a command, but I couldn't get it to work in the little bit that I was checking out the problem.

`ls *.mp3 | sed 's/^\(.*\)www\.website\.com\.\(.*\)$/mv & \1\2/'`

That should have done all the moves automatically, but it was throwing some problems, didn't really try to look into it much.  I did this in z shell, but it should work in the default bash as well.

Good luck,

Chris

---

### Post by xItachi on 2008-04-09
> **renewip said:**
> good luck!

```
for i in *.mp3; do mv "$i" "`echo $i | sed -e 's/www.website.com//gi'`"; done
```

I tried this and it worked.  Thanks!

---

### Post by ghostdog74 on 2008-04-09
```

ls -1 *www.website* | awk 'BEGIN{q="\047"}
{
  oldfile=$0
  sub(".www.website.com","")
  cmd = "mv "q oldfile q" "q $0 q
  print cmd
  #system(cmd) #uncomment to use
}
' 

```

---

### Post by soeten on 2008-04-12
A bit off topic, but how can you create a loop or a goto in a shell script.
I want to goto the script to jump right back at the beginning when its done. (where I have a sleep command)

Thanks 
- Soeten

---

### Post by ghostdog74 on 2008-04-12
you use a loop
```

while true
do
  # code
done 

```
see the link Learning bash for more info on loops.

---

