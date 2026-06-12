---
title: "For Each File in Directory..."
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by dpatel on 2007-07-24
Hi -

I am trying to use mp3splt to split every mp3 file I have in a directory into 30 minute chunks.

For example: mp3splt -t 30.00 VachAn25.mp3

Does anyone now how I can automatically run this command for each mp3 file in a folder (and ideally output to a new folder) rather than me laboriously run this command manually for each file.

It would be better still if I could cycle through all sub-folders and do the same thing.

Thanks!!

---

### Post by Cypher on 2007-07-24
As a quick start
```

#!/bin/sh

for file in `ls *.mp3`; do
   mp3splt -t 30.00 $0/$file
done

```
Put that into a file in your ~/bin directory. Do "chmod 755 <script>" and execute it as
```

<script> <destination directory>

```
in the directory that contains the mp3 files.

To decend into each sub-folder, the script would have to be a little more elaborate..

---

### Post by rogueluke on 2007-07-24
not sure if this does what you want but 

```
mp3splt -t 30.00 `ls | grep .mp3` 
```

might work  the ` is the one next to the 1 on a qwerty keyboard

---

### Post by Mornedhel on 2007-07-24
rogueluke, if that works, why not mp3splt -t 30.00 *.mp3 ?! (Unfortunately, mp3splt looks like it accepts only single files as arguments.)

And dpatel : there's a -d DIRECTORY argument you can use to output the result file to DIRECTORY instead of the current directory. So what we need is for Cypher to add a level of recursion to his script...

---

### Post by dpatel on 2007-07-24
All -thanks!

Cypher - I've done what you state butI get the following error output (as a part example):

/bin/mp3splitter/VachAn25.mp3: Not a directory

I think I might be getting this bit wrong "<script> <destination directory>" - What do you mean by <destination directory>? (I am running the script from the directory where the mp3 files are).

I've tried changing $0/$file to just /$file to get mp3splt to look in current directory but obviously not really sure what I'm doing!!

---

### Post by Mornedhel on 2007-07-24
dpatel,

In Cypher's script, $0 is the first argument provided : the <destination directory> of the example. When you're in the directory containing your MP3s : "<script> ." (yes, that's a dot) When you're one level higher in the tree : "<script> name_of_the_directory_where_your_files_are_stored" When you're, uh, basically anywhere : "<script> full_path_to_the_directory_not_to_an_MP3_file"

---

### Post by dpatel on 2007-07-24
Thanks Mornedhel. Not sure what if I've done something wrong but I had to change it $1 before it worked. Anyway, it working - great!!! First time posting, so great to get help so quickly!!

:)

---

### Post by rogueluke on 2007-07-24
Oh yeah

```
find . -name *.mp3 -exec mp3splt -t 30.00 \{\} \;
```

should work and is recursive

---

### Post by Mornedhel on 2007-07-24
> **dpatel said:**
> I had to change it $1 before it worked Ah, true !! $0 is the command itself, shame on me (and Cypher) for such a basic mistake.

---

### Post by Cypher on 2007-07-25
Oops..what can I say, I was coding on the fly as a guide..not fully tested..:)

---

### Post by Sciamano on 2008-03-16
Ehm... I know this is stupid but I'm encountering a problem when filenames include spaces.

My script is basically the same as the one suggested:

```
#!/bin/sh

for file in `ls *.mp3`; do
   mp3splt -a -t 8.00 $1/$file
done
```

But, as I said, if the source filename contains spaces it won't work.
How can I solve? I've tried putting quotes almost everywhere but I did not succeed! :(
Thanks!

---

