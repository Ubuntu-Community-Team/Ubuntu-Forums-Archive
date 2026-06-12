---
title: "bash script problem"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-03-14
How can I write a shell script that removes a file if it is found under a given directory? I want to check that if the file is a directory then all files within the directory are removed as well.

---

### Post by ComplexNumber on 2007-03-14
> **syalam said:**
> How can I write a shell script that removes a file if it is found under a given directory? I want to check that if the file is a directory then all files within the directory are removed as well.
something like this:
```
#!/bin/bash

cd "$1"

for i in *

do

if [ "$i" = "$2" ]
then

rm -R $i
echo "found it!"
 exit 0
fi

done


```supply 2 papareters to the program:
1st parameter = directory where you want the search to start
2nd parameter = what directory you are looking for

for example, if the program is called MyScript and you want to look for a directory called That_Directory starting at /home/<your-username>/Documents, then type in the following(assuming that you are in the same directory where the script is located):
**./MyScript[COLOR=White]....[/COLOR]/home/<your-username>/Documents[COLOR=White].....[/COLOR]That_Directory**

---

