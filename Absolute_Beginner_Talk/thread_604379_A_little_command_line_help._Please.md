---
title: "A little command line help. Please"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-11-06
I have a folder "x"  it has many sub-folders in it "a-z" I want to produce a list of all the files that are in a-z without the names of the individual sub-folders appearing in the list its, so that it would appear in the list as if all the files came from only one folder, and output the results of the list into a text file.
Is there anyone that can help me with this?

---

### Post by dwhitney67 on 2007-11-06
See if this will meet your needs:

```
$ find <dir> -type f -exec basename {} \;
```

where <dir> is the directory you want to search.

---

### Post by swoll1980 on 2007-11-06
no thats not going to do it thanks for the help though. My solution is going to have a
 "ls -r -f | " in it though I don't know the exact command it should contain these I'm thinking " ls ~/x -R -f | ~/abc.txt " not sure though

---

### Post by dfreer on 2007-11-06
So you want the list of all the files under the X directory, including sub-folders, in a text file correct?
This should help somewhat
```
find . -type f -exec echo {} \; > text.txt
```
You'll probably want to edit it further to get rid of the folders on each line, but it's a start!

EDIT: I didn't post quick enough again, I see...
How about:
```
ls -R -f ~/x/ > ~/myfile.txt
```

---

### Post by hyper_ch on 2007-11-06
```

ls -rf > output.txt

```

---

### Post by dwhitney67 on 2007-11-06
> **bloor75 said:**
> no thats not going to do it thanks for the help though. My solution is going to have a
 "ls -r -f | " in it though I don't know the exact command it should contain these I'm thinking " ls ~/x -R -f | ~/abc.txt " not sure though

Your opening post indicated that you want to list all of the files from a directory and its subdirectories, not including the listing of the subdirectory names, _and_ output the list to a file.  This should work:

```
$ find <dir> -type f -exec basename {} \; > listing.txt 
```

Earlier, I had forgot about saving the results to a file.  If there are additional requirements, you should list them.

---

### Post by swoll1980 on 2007-11-06
> **hyper_ch said:**
> ```

ls -rf > output.txt

```

This listed the sub-folders but not the files in them. I want to list the files in them without listing the sub-folders themselves thanks for helping though

---

### Post by dfreer on 2007-11-06
I think the issue is the output of that find command ends up looking something like this:
```

./x/a/a1.file
./x/a/a2.file
./x/a/a2.file
./x/b/b1.file
./x/b/b2.file
./x/b/b3.file

```

Where the OP wants something like this:
```

a1.file
a2.file
a3.file
b1.file
b2.file
b3.file

```

Am I correct? In which case, a find command should work, if we cut out everything but the actual filename itself.

---

### Post by swoll1980 on 2007-11-06
I just tried " ls ~/x -R -f > ~/abc.txt " this almost worked but listed the sub-folders in the text file

---

### Post by swoll1980 on 2007-11-06
I want a list of all files under "x" to appear in a txt file as if they all came from one folder the 
way i'm doing it  is listing the sub-folder and then the files in it "x" has about 200 sub-folders in it so having them all appear in the list is overwelming when all I want is a list of the name of the files not witch sub-folder they are in

---

### Post by dfreer on 2007-11-06
I'm don't have my linux machine in front of me, but I'm thinking the find command would still be the best solution:
Basically, *find . -type f -exec echo {} \; * currently gives you what you want, but it has the path at the beginning of each file like so:
./x/a/a1.file

But if all of your files are in this format:
*some_text***.***some_extension*

You should be able to use find and cut together, to only grab the last two fields seperated by a period.
```

find ~/x/ -type f -exec echo {} \; | **the_cut_command_here** > ~/abc.txt

```
See what I mean? Probably not, because it's 4 am here and I don't have my scripts on my linux machine to copy the exact command out of.

EDIT: 
```

find ~/x/ -type f -exec echo {} \; | cut -d'.' -f2,3 | cut -d'/' -f3 > ~/abc.txt 

```
This might work, but you're going to have to double-check me. Probably need to use gawk or awk or whatever it's called ;)

---

### Post by swoll1980 on 2007-11-06
That almost worked but a lot of the files had only the extension left on them. Some of them came out ok though for example the list came out like this 
abc.jpg
def.jpg
bbb.jpg
.jpg
.jpg
ghi.jpg
None of the sub-folders showed up in the list though witch is good. We're almost there

---

### Post by dfreer on 2007-11-06
Well, this would be a bit easier if I could cut the files from right to left, instead of left to right. Then I could grab the first two fields, well "first" being the rightmost two fields, seperated by a '.' (so the filename and the extension). Right now it's working from left to right, so:
*./xfolder/subfolder/myfile.jpg* gets saved correctly, but *./xfolder/myfile.jpg* is probably getting saved wrong.

I'm going to bed for now, maybe someone will figure this out while I sleep lol.

---

### Post by swoll1980 on 2007-11-06
Thanks for the help

---

### Post by dwhitney67 on 2007-11-06
> **dfreer said:**
> I think the issue is the output of that find command ends up looking something like this:
```

./x/a/a1.file
./x/a/a2.file
./x/a/a2.file
./x/b/b1.file
./x/b/b2.file
./x/b/b3.file

```

Where the OP wants something like this:
```

a1.file
a2.file
a3.file
b1.file
b2.file
b3.file

```

Am I correct? In which case, a find command should work, if we cut out everything but the actual filename itself.
I know... that is why there is an "-exec basename {} \;" included within the 'find' statement I provided earlier.

---

### Post by swoll1980 on 2007-11-06
> **dwhitney67 said:**
> See if this will meet your needs:

[CODE]$ find ~/x -type f -exec basename {} \; > ~/abc.txt

where <dir> is the directory you want to search.

That did it!!  Sorry I overlooked this tread earlier, this listed all the files like this
aaa.jpg
bbb.jpg
ccc.jpg
ddd.jpg

---

### Post by swoll1980 on 2007-11-06
Is there a way to set this up to automaticly add files to the list as I add them to the folder?

---

