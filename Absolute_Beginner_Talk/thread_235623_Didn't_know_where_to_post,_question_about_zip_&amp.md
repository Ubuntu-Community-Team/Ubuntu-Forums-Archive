---
title: "Didn't know where to post, question about zip &amp; co."
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by theFallen on 2006-08-13
Hi,

I have a set of folders and I'd like to zip each folder as a seperate zip-File. Can anybody tell me how to do it without retyping the command for every folder?

Example:
Folders: 001, 002, 003 .....
Archives: 001.zip, 002.zip....

---

### Post by kebes on 2006-08-13
Make a shell script to do it for you. Something along the lines of:

1. Go to the directory in question, open up a text file, like:
```
nano batch_zip.sh
```

2. In the text file, make a bash script for looping through the directories:
```

#!/bin/bash

FIRSTDIR=1
LASTDIR=10
pad=""

while [ "$CURDIR" -le "$LASTDIR" ]
do
  # Determine number formatting...
  if (( $CURFILE < 100 ))
      then
      if (( $CURFILE < 10 ))
          # The number is 0-9 ...
          then
          pad="00"
      else
          # The number is 10-99 ...
          pad="0"
      fi
  else
      # The number is 100 or more ...
      pad=""
  fi


  # Zip each dir...
  zip $pad$CURDIR.zip $pad$CURDIR/ -r

  # Increment the counter...
  CURDIR=$(($CURDIR+1))

done


```

3. After saving changes (Ctrl+X and then 'Y' in nano), make the script executable:
```

chmod +x batch_zip.sh
```

4. Run the script:
```

./batch_zip.sh
```

5. The script should loop through the directories.


Note that the above script is an example. I just wrote it out from memory and didn't check it. There are probably some errors, but hopefully it will get you going in the right direction. The great things about writing little scripts like this is that if you keep them around, you'll find lots of times when you can use them (with quick modifications maybe).

I hope that helps. If you're not comfortable playing around with shell scripts then there may be a neat command-line way of doing it, such as piping the output of "ls" into zip...

---

