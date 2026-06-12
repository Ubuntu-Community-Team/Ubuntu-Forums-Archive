---
title: "downloaded file opens wrong app"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by K_Soze on 2007-07-16
I have changed my preferences in FF to open torrent files with Azureus (script file in user/bin). I hope that is the correct file. But it still tries to open with both bit torrent and azureus but azureus doesn't do anything. The file extention is ".torren".

What the heck do I do?  :confused:

---

### Post by AlexenderReez on 2007-07-16
for me i just need to right click particular thing(example torent) ...then properties --->open with ....select application....if not there choose custom command then

> /usr/bin/azureus


---

### Post by SlackLagg on 2007-07-17
you may need to change your script file (especially if you just copied and pasted from the "how-to" listed here. I had trouble with that one)


This is what I have 

```


#!/bin/bash

echo $# 
if [ $# -ne 0 ]
then
/usr/lib/azureus/azureus "$*"
else
/usr/lib/azureus/azureus
fi


```

Basically that just checks to see if there are any parameters, and then runs command based on that.

---

### Post by K_Soze on 2007-07-17
right now I'm just I've deleted the file type in FF and just save the torrent to desktop. Then, I open Azureus to open the torrent.

I'll give your suggestions a go tonight.

Thanks...

---

