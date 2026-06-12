---
title: "one of the newbiest things ever"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by tadada on 2007-07-29
How do I use a script. I find a script I want and go to use it but when I click the link alot of times it brings up another web page with text. how do I use said script then?

do I have to save it into a special txt file?

---

### Post by walkerk on 2007-07-29
> **tadada said:**
> How do I use a script. I find a script I want and go to use it but when I click the link alot of times it brings up another web page with text. how do I use said script then?

do I have to save it into a special txt file?

save as a .sh .. example: yourscript.sh

in terminal go to the directory your script is in. for example:
```
cd /home/yourname/scripts
```

ensure its executable:
```
chmod +x yourscript.sh
```

to run it:
```
./yourscript.sh
```

---

### Post by tadada on 2007-07-29
and if the site gives the command to run it then save it and use their code to run it?

---

### Post by walkerk on 2007-07-29
what exactly are you trying to do? i presume you are downloading a script from a website..? if so, download it. in a terminal window cd to the directory in which you downloaded it to. now just type:
[code]./*script_you_downloaded.sh*[code]

where *script_you_downloaded.sh* is the filename.

is it a shell script? or is it a bin?

---

### Post by rillip on 2007-07-29
Unless you know exactly what it's going to do, I advise caution on any downloaded scripts.  It should be from a trusted source, or else they can do anything that you could do, including remove files.

---

