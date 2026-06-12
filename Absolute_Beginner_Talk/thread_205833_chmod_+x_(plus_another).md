---
title: "chmod +x (plus another)"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by bbales on 2006-06-29
I made a small script to start and stop my teamspeak server. It resides in the same folder as the startup script (however that also poses question 2)  

#!/bin/bash
exec ./teamspeak2-server_startscript start

I want to make this an executable so I don't have to use ./ts_start, just type in ts_start (no ./) I do this by $sudo chmod +x ts_start, which turns it green like other executables, but when I type ts_start in the same directory as the executable it says command not found. I also try it as sudo ts_start with the same result.

Question 2. I also want to move this script to a script directory in my home directory. However I cannot figure out how to use ./ and a path, i.e. /home/ts-server/./teamspeak2-server_startupscript start or ./home/ts-server/teamspeak2-server_startupscript start. Neither seems to work. 

Any help would be greatly appreciated :)

---

### Post by dmizer on 2006-06-29
my understanding of scripting is fairly limited so i can't be of too much help, but i believe the reason you have to use the ./ in front of your script is to tell ubuntu that the script you're trying to run is in the current directory.  otherwise, ubuntu thinks it doesn't exist.  this is why the command doesn't work in a different directory.

---

### Post by Arndt on 2006-06-29
[QUOTE=bbales]I made a small script to start and stop my teamspeak server. It resides in the same folder as the startup script (however that also poses question 2)  

#!/bin/bash
exec ./teamspeak2-server_startscript start

I want to make this an executable so I don't have to use ./ts_start, just type in ts_start (no ./) I do this by $sudo chmod +x ts_start, which turns it green like other executables, but when I type ts_start in the same directory as the executable it says command not found. I also try it as sudo ts_start with the same result.
[/QUOTE]
'chmod' was the correct first step. To be able to run your script without specifying where it is, you need to have its directory in your PATH variable. If you always want to be able to run scripts in whatever the current directory is, do:

```
export PATH=$PATH:.
```

If you want only the particular directory that happens to be the current directory now to be added, do:

```
export PATH=$PATH:`pwd`
```

> 
Question 2. I also want to move this script to a script directory in my home directory. However I cannot figure out how to use ./ and a path, i.e. /home/ts-server/./teamspeak2-server_startupscript start or ./home/ts-server/teamspeak2-server_startupscript start. Neither seems to work. 

Any help would be greatly appreciated :)

If the current directory is not involved, you don't need to refer to it using "./".

```
/home/ts-server/./teamspeak2-server_startupscript start
```
Here, the "./" does no harm, because it refers to what is the current directory at that point in the path (i.e., /home/ts-server), but it is also unnecessary. If /home/ts-server is where your script is, this ought to work. Try doing
```
ls -l /home/ts-server/./teamspeak2-server_startupscript
```
to see if in fact the script is there, and what its permissions are.

```
./home/ts-server/teamspeak2-server_startupscript start
```
This is wrong, because you don't refer to the directory /home, but to a local directory home under the current directory. Unless your current directory is / (the root directory), they are not the same thing.

---

