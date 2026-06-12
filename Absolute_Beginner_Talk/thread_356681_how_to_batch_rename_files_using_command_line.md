---
title: "how to batch rename files using command line?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by annda on 2007-02-08
i've had some success with regular expressions in different programs and i like to think that i understand the principles. but i probably don't,  since i can't do this very simple thing.

i have a few files called somestring_datedigits.someextension in a directory. i would like to rename them to datedigits_something.differentextension. 

i would be very happy if someone could point me to the right online guide and/or tell me how exactly i need to tell my computer to do that. (and please elaborate, i would like to know what i'm doing and what rules i'm applying).

---

### Post by LotsOfPhil on 2007-02-08
s/\([a-zA-Z0-9]*\)_\([a-zA-Z0-9]*\)\.EXTENSION/\1_\2\.NEWEXTENSION/

Is the regular expression that would do it, I believe.

---

### Post by hmLyons on 2007-02-08
Here's a one liner that I found [here]("http://webtools.live2support.com/linux/mv.php") that does what you're talking about. It renames files with the extension txt to htm in the current directory.

```
for f in *.txt; do mv ./"$f" "${f%txt}htm"; done
```

That works as a nice one-liner, but to make its behavior clearer here is it as a batch file.

```

#!/bin/bash

for f in *.txt; 
do 
	mv ./"$f" "${f%txt}htm"; 
done

```

Most of the above code is pretty straight forward. You can read more from the [beginner]("http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html") and [advanced]("http://tldp.org/LDP/abs/html/") bash guides.

The actual string manipulation is probably the more difficult part of this script (I had to look it up myself ;)). Basically the code ${f%txt} takes the string represented by f (the current filename) and chops off the txt part from the back of the string.

You can read more about string manipulation [here]("http://tldp.org/LDP/abs/html/string-manipulation.html").

Hope that helps.

---

### Post by hmLyons on 2007-02-08
Here is a slight variation of the above script that will rename all files in the current directory as well as its subdirectories. 

```

#!/bin/bash

find . -name "*.txt" | while read f
do
	mv ./"$f" "${f%txt}htm"; 
done

```

I tested this quicky and it works, but I haven't used this before, so I take no responsibility if this destroys your entire computer :(

---

### Post by LotsOfPhil on 2007-02-09
Okay. I looked back at your post and adapted hmLyons code a little. Here goes:
```

#!/bin/bash
                                                                                
oldex='txt'
newex='htm'
echo ""
echo "Syntax is ./rename-reorder.sh <old extension> <new extension>"
echo "Defaults are txt and htm, respectively"
echo ""
                                                                                
if [ $1 ]
then
        oldex=$1
        echo "Old extension set to $1"
fi
if [ $2 ]
then
        newex=$2
        echo "New extension set to $2"
        echo ""
fi
                                                                                
find . -name "*.$oldex" | while read f
do
        under=`expr index $f _`
        if [ "$under" -gt 0 ]
        then
                first=${f%%_*}
                directory=$first
                first=${first##.*/}
                second=${f#*_}
                second=${second%.$oldex}
                directory=${directory%/*}/
                echo mv "$f" "$directory""$second"_"$first".$newex
        else
                echo mv "$f" "${f%.$oldex}.$newex"
        fi
done

```

I'll explain in the next post so this isn't too long.

---

### Post by LotsOfPhil on 2007-02-09
$1 and $2 are the shell variables passed in. So if you type "./script html doc" $0 is ./script, $1 is html and $2 is doc

The script looks at all the files with the right extension. `expr index $f _` returns the position of the underscore. It is zero if there is no underscore.
Then I made two variables, first and second. I end up getting something where the filename is first_second.extension
first=${f%%_*} strips the underscore and everything after it. 
first=${first##.*/} strips off the path (this comes from using find).

---

### Post by jongkind on 2007-02-09
Or use this:

[http://ubuntuguide.org/wiki/Dapper#How_to_rename_all_files_in_directory_at_once]("http://ubuntuguide.org/wiki/Dapper#How_to_rename_all_files_in_directory_at_once")

---

### Post by annda on 2007-02-10
good, i can keep on learning! thanks a lot for the info, scripts and links.

i just quickly tested changing extensions and of course it works great. i'll try to read and understand more in order to change filenames too, not only extensions.

thanks again!

---

### Post by Marsolin on 2007-02-10
You could always use mrename.  It's downloadable from the repos.

---

