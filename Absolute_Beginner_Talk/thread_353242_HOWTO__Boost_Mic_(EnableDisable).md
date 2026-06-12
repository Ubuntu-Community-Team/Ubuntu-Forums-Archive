---
title: "HOWTO : Boost Mic (Enable/Disable)"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by ashmew2 on 2007-02-04
> This HOWTO is for anyone you uses their microphone a lot and is frustrated with the long sequence of clicks required to turn the 'Mic Boost' on or off. I will show you a simple shell script that determines the current value of the 'Mic Boost' setting and toggles it.

First, you need to determine the numid of your 'Mic Boost' control. As far as I know, this id varies from installation to installation. If I am wrong, someone please let me know.
amixer controls | grep 'Mic Boost'
Now open your favorite text editor and paste in the following text:

#!/bin/sh
if amixer cget numid=17 | grep on; then
amixer cset numid=17 off
else
amixer cset numid=17 on
fi

and then replace all occurrences of 17 with your own numid. Save this text file wherever you like (this will be it's permanent resting place). Open a terminal and, after changing to the directory of the new file, make the file executable with the following command:
chmod a+x <filename> where <filename> is the name of your file.

Finally, just make a launcher on the desktop or wherever that points to this file. Now if you ever want to turn on 'Mic Boost' quickly (for example: your receiving a call on the computer and you want to get the boost on before answering) all you need to do is run the launcher!

This was my first HOWTO and my first shell script ever so if it's awful please let me know.


I found that here : [http://ubuntuforums.org/archive/index.php/t-118916.html](http://ubuntuforums.org/archive/index.php/t-118916.html)
And i thought that it might help some people cuz it certainly helped me :)
Hope it helped

---

### Post by ashmew2 on 2007-02-04
Some1 guna plz remove this thread , i thought no1 has posted his solution but its already there : [http://ubuntuforums.org/showthread.php?t=118916&highlight=howto+mic+boost](http://ubuntuforums.org/showthread.php?t=118916&highlight=howto+mic+boost)

My bad , sorry people :oops:

---

