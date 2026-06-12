---
title: "edit filenames in bash shell script loop"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by diafygi on 2007-07-18
Hey everyone, I'm trying to write my first bash script, but I'm in a spot of trouble.

I have a folder with bunch of text files that follow a naming pattern:
```

part1_file1.txt
part1_file2.txt
part1_file3.txt
part2_file1.txt
part2_file2.txt
part2_file3.txt

```

I'm trying to rename the files to the following pattern:
```

file1_part1.txt
file1_part2.txt
file2_part1.txt
file2_part2.txt
file3_part1.txt
file3_part2.txt

```

So far, I've got a loop, but I don't know what to put inside it:
```

#! /bin/sh
for i in *.txt; do
 some_command
done

```

In C++, I would just get the variable for the filename string, cut it up into two variables using substrings, and combine them back together. But I've been unable to find a way to modify the "$i" string in bash.

So my question:
-How can I modify "$i" or cut "$i" up into different variables?

---

### Post by Cypher on 2007-07-18
Give this a shot.
```

#!/bin/sh

for file in `ls *.txt`; do 
     prefix=`echo $file | cut -d'_' -f1`; 
     suffix=`echo $file | cut -d'_' -f2 | cut -d '.' -f1`; 
     f2=$suffix"_"$prefix; 
     mv $file $f2.txt; 
done

```

---

### Post by asmoore82 on 2007-07-18
```

#!/bin/bash

for filename in *_file*.txt
do

   file="${filename%.txt}"
   file="${file##*_}"

   part="${filename%%_*}"

   mv "$filename" "${file}_${part}.txt"

done

#End of File

```

---

### Post by bashologist on 2007-07-18
rename "s/file/part/;s/part/file/" *.txt

---

### Post by diafygi on 2007-07-18
> **Cypher said:**
> ```

     prefix=`echo $file | cut -d'_' -f1`; 
     suffix=`echo $file | cut -d'_' -f2 | cut -d '.' -f1`; 

```
I'm sorry, I guess I simplified my problem too much. The filenames are actually quite a bit longer than I mentioned. They are more along the line of 'part1_some_other_info_file1.txt'. The 'cut' command will only allow a single character to cut around, so I can't say 'cut -d"_some_other_info_" -f2'.


> **asmoore82 said:**
> ```

   file="${filename%.txt}"
   file="${file##*_}"
   part="${filename%%_*}"

```
I don't really understand the syntax inside the braces {}. Is there some documentation somewhere where I could learn what all the #s and %s and *s mean?

Thanks for the quick replies! This forum has made the jump a heck of a lot easier.

---

### Post by bashologist on 2007-07-18
[QUOTE=diafygi]I don't really understand the syntax inside the braces {}. Is there some documentation somewhere where I could learn what all the #s and %s and *s mean?
[/QUOTE]

[http://wooledge.org/mywiki/BashFAQ?action=show&redirect=BashFaq#faq73](http://wooledge.org/mywiki/BashFAQ?action=show&redirect=BashFaq#faq73)
In a terminal "man bash" then type "/", "Parameter Expansion", "n"...

---

### Post by diafygi on 2007-07-18
Thanks a bunch everyone! I managed to get it working with the following script:

```

#!/bin/bash
for filename in *_file*.txt; do
   file="${filename%.txt}"
   file="${file##_some_other_info_}"
   part="${filename%%_some_other_info_}"
   mv "$filename" "${file}_some_other_info_${part}.txt"
done

```

This obviously isn't the exact code I used, but it is the same amount of commands and everything. :)

---

### Post by annda on 2007-07-18
in case you are interested in batch renaming files (but keep on scripting!) - there are nice apps to do that: gprename (my favorite so far), purrr (limited but simple for pattern rename) and krename (useful for renames based on meta info). they are all in the repositories. they are not perfect but very useful if you rename files all the time. sometimes writing a quick script will be the most efficient way, sometimes using one of those is faster.

---

