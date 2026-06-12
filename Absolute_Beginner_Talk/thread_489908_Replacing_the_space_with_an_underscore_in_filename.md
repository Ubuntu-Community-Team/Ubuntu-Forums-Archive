---
title: "Replacing the space with an underscore in filenames"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-07-01
I would like to do this to my entire music collection. Obviously, doing this individually is impractical, so I was looking for solutions.

I found Krename, but I'm currently on a slow internet connection, and it says it will be an 80 MB download (probably kde libraries, I use fluxbox).

Is there an easier (safe) way to do this? It's pretty important that no files get deleted or marred. 

-Andrew

---

### Post by oldmanstan on 2007-07-02
check out the package renameutils, it's command line but it lets you use a text editor to rename files in a directory, so you can just use the find-replace function

EDIT: also check this out, it might be overkill though [http://debaday.debian.net/2007/06/13/mmv-mass-moving-and-renaming-files/]("http://debaday.debian.net/2007/06/13/mmv-mass-moving-and-renaming-files/")

also, i got curious and did a short writeup on renameutils, [http://www.wellactually.net/code/2007/07/renameutils/]("http://www.wellactually.net/code/2007/07/renameutils/")

---

### Post by Atreus12 on 2007-07-02
After your suggestion, I looked at renameutils, and it looks pretty cool. Can it work on full file paths? Some of my directories have spaces in them. 

If it could, then that would be great, because you can just write the files to a text document, and then run it through

```
sed 's/ /_/g' file.txt
```

and that will replace the spaces with underscores.

---

### Post by oldmanstan on 2007-07-02
you don't even need sed, follow the directions i posted (link in last post) but at the end of the command add the '-R' option and the text file created will contain an entire directory structure (spaces included) at which point you can just use find/replace to replace all the spaces with an underscore in the whole file

you could prolly send the output to sed with a pipe but that's not really necessary, the file created is a temporary file and you don't get a chance to edit it outside the context of qcp/qmv so i'm not sure how well that would work

in any event, what you're trying to do is perfectly possible (and easy) using the method i described on my page :)

p.s. let me know if you come up with any nifty tricks to make it easier (such as piping it into sed)

---

### Post by arsenic23 on 2007-07-02
Could you go to the root of your music directory and use
```
find -type f -exec rename 'y/\ /\_/' {}  \;
```?

---

### Post by oldmanstan on 2007-07-02
if you did a specific type of replacement commonly you could do something like this:

create a shell script as such, call it say... replace.sh for instance (tested it and it works but kinda rough around the edges...)

```
#!/bin/bash
echo $*
sed 's/_/ /g' $* > temp_file_for_replace.txt
cat temp_file_for_replace.txt > $*
rm temp_file_for_replace.txt
```

put it in your path then run qcp or qmv like so:

```
qcp -R -e replace.sh -f do
```

which would then automate the task of substituting '_' for ' ' (in this case since my test files had underscores in them not spaces

just a thought, someone with more shell scripting knowledge could prolly find a way that you could pass your substitution rule from the qmv or qcp line which would let you create rules on the fly

---

### Post by Atreus12 on 2007-07-02
> **arsenic23 said:**
> Could you go to the root of your music directory and use
```
find -type f -exec rename 'y/\ /\_/' {}  \;
```?

Is it really this easy? :KS

wow, I need some more command line learnin then

Edit: no, I don't think it's that easy

---

### Post by oldmanstan on 2007-07-02
the beauty and bane of linux all in one: 1 simple problem, 17,000 different ways to solve it :) (ok maybe not quite that many but still...)

---

### Post by arsenic23 on 2007-07-03
> Edit: no, I don't think it's that easy

I'm wondering what kind of errors you got just using the find command?  I went ahead and tried it on my music folder and it worked flawlessly.

---

### Post by Atreus12 on 2007-07-03
```
user@box:~/dir with spaces$ find -type f -exec rename 'y/\ /\_/' {}  \;
Can't rename ./test dir/files with spaces2.mp3 ./test_dir/files_with_spaces2.mp3: No such file or directory
Can't rename ./test dir/files with spaces1.mp3 ./test_dir/files_with_spaces1.mp3: No such file or directory
Can't rename ./test dir/files with spaces3.mp3 ./test_dir/files_with_spaces3.mp3: No such file or directory
Can't rename ./test dir/files with spaces4.mp3 ./test_dir/files_with_spaces4.mp3: No such file or directory
Can't rename ./test dir/files with spaces5.mp3 ./test_dir/files_with_spaces5.mp3: No such file or directory
```

I just made a test directory that goes like this:
```

dir with space:
     file with spaces.mp3
     test dir:
          files with spaces1.mp3
          files with spaces2.mp3
          files with spaces3.mp3
          files with spaces4.mp3
          files with spaces5.mp3
     test2 dir:

```
The command works fine, it just doesn't work on directories

---

### Post by arsenic23 on 2007-07-03
Sorry about that - I guess it doesn't work inside of directories with spaces in their name....

If I was going to do this with in an environment with nested directories with spaces in their names, I'd first remove those spaces by running this repeatedly untill it fails to produce errors:
```
find -type d -exec rename 'y/\ /\_/' {}  \;
```

After those spaces are removed then the original find command will work with just one shot.  Then if you wanted to place the spaces back into your directory names you can just run
```
find -type d -exec rename 'y/\_/\ /' {}  \;
``` to put the spaces back in.

---

### Post by Atreus12 on 2007-07-03
Well, both methods work (post #6, #11)

#11 is probably easier, but a little messy (you have to keep running it until you get no error messages)

Thanks for the help, when I get brave enough to run it 'for real', I'll post back with the results

-Andrew

---

### Post by Atreus12 on 2007-07-04
Well, I did it.

As far as I can tell, everything went fine

I ran 
```
find -type d -exec rename 'y/\ /\_/' {}  \;
```

a couple of times until no errors showed up

and then ran

```
find -type f -exec rename 'y/\ /\_/' {}  \;
```

once and it was all done.

It did take a little while though, 600 Mhz doesn't get you as far as you would think ;)

To update my playlist, I ran:

```
sed 's/ /_/g w playlist_new.m3u' playlist_old.m3u
```

and everything works.

Thanks for the help!!

---

