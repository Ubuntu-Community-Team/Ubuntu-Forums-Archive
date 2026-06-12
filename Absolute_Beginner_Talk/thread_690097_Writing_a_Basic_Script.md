---
title: "Writing a Basic Script"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by helixed on 2008-02-07
Hello everybody,

I've never tried to do any scripting before.  I was wondering if it would be possible for a script to search through my /home/helixed directory for any files ending with .log or .list and move them to a folder at /home/helixed/.logs.  

Thanks,

Helixed

---

### Post by talsemgeest on 2008-02-07
Just use a nice and simple shell command.
```
mv ~/helixed/*.log ~/helixed/.logs/
```Just change *.log to *.list for the .list files. There is a command that can do both but I cant remember how it goes.

Hope this helps :)

---

### Post by apetresc on 2008-02-07
> **talsemgeest said:**
> Just use a nice and simple shell command.
```
mv ~/helixed/*.log ~/helixed/.logs/
```Just change *.log to *.list for the .list files. There is a command that can do both but I cant remember how it goes.

Hope this helps :)

There's a slight typo in your command. ~/helixed will evaluate to /home/helixed/helixed . What you actually want (assume helixed is the user you're using) is
```
mv ~/*.log ~/.logs/
```

See? Even shorter :D

---

### Post by kpkeerthi on 2008-02-07
Run this 
```
find ~ -regex '.*(\.log|\.list)' 
```
command first and make sure it finds all .logs and .list files first. And then to move, run

```
find ~ -regex '.*(\.log|\.list)' -exec mv {} ~/.logs \;
```

PS: This command will search for all folders in your home **recursively**

---

### Post by talsemgeest on 2008-02-07
> **AdrianP said:**
> There's a slight typo in your command. ~/helixed will evaluate to /home/helixed/helixed . What you actually want (assume helixed is the user you're using) is
```
mv ~/*.log ~/.logs/
```See? Even shorter :D
Good point

---

### Post by lswest on 2008-02-07
~ is a variable for /home/[username] and the OP specified he wanted stuff in his /home/helixed/ folder, which translates to "~" apart from that, the commands above are pretty useful, and, you could write it into a script so that you just run the script and the commands are executed, if you plan on doing it frequently.

ah, looks like talsemgeest edited his post while i was writing this :P oh well, i'll leave the quick explanation of "~" there.

---

### Post by helixed on 2008-02-07
Hey, thanks for the help everybody.  I know this may sound like a stupid question but how could I get this script to run every minute or so?

Thanks,

Helixed

---

### Post by talsemgeest on 2008-02-07
There is a command called crontab that does exactly what you want, but I'm not sure how to use it. I'll see if I can figure it out.

---

### Post by talsemgeest on 2008-02-07
See if anyone can make any more sense of this than I could
[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

---

