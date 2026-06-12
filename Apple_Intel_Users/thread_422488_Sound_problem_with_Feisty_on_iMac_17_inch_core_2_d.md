---
title: "Sound problem with Feisty on iMac 17 inch core 2 duo"
date: 2007-04-25
forum: Apple Intel Users
---

### Post by ashokcm on 2007-04-25
I had installed ubuntu edgy successfully in an iMac 17" core 2 duo. But with no success in sound. Recently I upgraded to Feisty hoping that it will be fixed. But I was disappointed! 
It seems to me that it is a problem with the sound control and not the actual drivers. When I play music / video files, it does not give any errors. It just does not make any sound. Please if someone had a similar experience, please can you post your alsa configuration?

---

### Post by nicfagn on 2007-04-25
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=418681]("http://ubuntuforums.org/showthread.php?t=418681")

Perhaps you can spot something useful. I did not, unfortunately. :(

---

### Post by nicfagn on 2007-04-27
I found a possible solution explained in this post:

[INDENT][http://ubuntuforums.org/showpost.php?p=2549232&postcount=13]("http://ubuntuforums.org/showpost.php?p=2549232&postcount=13")
[/INDENT]
I hope this can help.


Bye

---

### Post by ashokcm on 2007-07-31
After months of toiling, I gave up. But then the other day I decided to turn off alsa and use oss. And all of a sudden I started hearing music flowing out of the front speakers. xmms plays perfectly well now. Loud and clear. But still none of the other applications seem to work.:(

---

### Post by cyberdork33 on 2007-07-31
as far as I know there are no issues on your model iMac. (The 24" might be another story.) On edgy, there was an issue about which channel was used to output sound, but that was more of a control issue (which was easily fixed).

try opening a terminal, and running alsamixer (with your system set to use alsa instead of OSS). there are many many channels and switches that you can mess with to find the right channel to get your sound working correctly.

---

