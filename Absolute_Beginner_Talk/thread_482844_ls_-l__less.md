---
title: "ls -l | less"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-24
The strait line between -l and less. How do I make it? I don't see a key for it on my keyboard. What is this line called?

---

### Post by jnorthr on 2007-06-24
on my keyboard it looks like 2 short vertical lines one over the other and is above the \ key on my keyboard.
it should look like |
                            |

---

### Post by swoll1980 on 2007-06-24
Looks like | got it. Thanks

---

### Post by scxtt on 2007-06-24
it's a "pipe" which is basically a way to send output from program 1 --> input of program 2 ...

for what you posted, that's a "long list piped through less" - and less is a terminal text viewer ...

---

### Post by swoll1980 on 2007-06-26
just learning different commands

---

### Post by jw5801 on 2007-06-27
A question along a similar vein. I just copied a whole bunch of my files across from my Windows machine, and as XP does sometimes, there are quite a few random "desktop.ini" files scattered throughout. I'm just wondering if there's a quick commandline method to delete a number of files with the same filename? I tried:
locate desktop.ini | rm; which returned errors saying that there were no inputs to rm, and also:
rm `locate desktop.ini`; which doesn't work as some of the directory listings have spaces in them so rm cannont read the output from locate correctly. If i could get locate to print each output in quotation marks that would work but i'm sure there's a better method.
Enlighten me O Great Ones!

---

### Post by scxtt on 2007-06-27
how about:

find / -name desktop.ini -exec rm {} \;

or maybe:

find / -name desktop.ini | xargs rm

in either case you can replace the / with a better starting directory ...

---

### Post by jw5801 on 2007-06-27
Cheers! The second option returned an error for the same reason:
rm `loacate desktop.ini`
did. However the first option worked like a charm!

---

### Post by pmg on 2007-06-28
A variation on the second find command above that would work is:
```
find / -name desktop.ini -print0 | xargs -0 rm
```
The **-print0** on the find is telling it to print a null character (i.e. 0x00) after each filename rather then a space, which is what the **-0** on xargs is expecting.  This can handle spaces or other shell metacharacters in filenames (e.g. quotes.)

Another safe thing to do is preceed the **rm** in the above with **echo** and do a test run to make sure it's really what you want. In this case it would be
```
find / -name desktop.ini -print0 | xargs -0 echo rm
```
which would simply write out all the rm commands, so you could verify it's really going to do what you want before you actually do it.

---

### Post by scxtt on 2007-06-28
cool :) ... i'm no fan of "Spaces in filenames.txt" so i rarely run into that problem, and when i tried it on my own to remove some txt files, it worked ... but that flag for xargs should prove handy ...

---

### Post by Arndt on 2007-06-28
> **swoll1980 said:**
> The strait line between -l and less. How do I make it? I don't see a key for it on my keyboard. What is this line called?

It's usually called "vertical bar".

---

### Post by jw5801 on 2007-06-28
> **scxtt said:**
>  ... i'm no fan of "Spaces in filenames.txt" ...

It's around 30GB worth of music from someone who lets iTunes organise the filesystem :(
There's quite a few .m3u playlists and the like made up from it as well and I have the funny feeling that it would be far too much effort to fix it all. 
Cheers for the pointers! I'm fairly new at this Linux thing so I'm still learning all the associated syntax and the like.

---

