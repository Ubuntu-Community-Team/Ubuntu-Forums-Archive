---
title: "How to &quot;run&quot; a .jar file?"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by PsycoGeek on 2007-09-02
The application is [Phex]("http://www.phex.org/mambo/").  I've downloaded the application and extracted the archive to a folder on my desktop.  I have also found that I have to run the phex.jar file with a java Runtime, but I have not been able to find out how to do that.

---

### Post by ThrobbingBrain66 on 2007-09-02
With the Phex folder extracted to the desktop,
```
cd ~/Desktop/phex_3.2.0.102/lib
```
Then, to run the jar file
```
java -jar phex.jar
```

---

### Post by PsycoGeek on 2007-09-02
I was able to get it to run.  Thank you ThrobbingBrain.

Now, next question... is there a way to make a desktop or panel icon for launch it?

---

### Post by Hospadar on 2007-09-02
Yeah, if you make a launcher on the panel, and make the launcher command ```
java -jar   ~/Desktop/phex_3.2.0.102/lib/phex.jar
``` that should do it.

It's possible that this command needs to be run from the containing folder, in which case you can write a little script, I can tell you how to do that if the above doesn't work

---

### Post by PsycoGeek on 2007-09-02
Thanks Hospadar... looks like a script is needed.

---

### Post by Paul133 on 2007-09-02
Bring up a terminal and type ```
cd /usr/local/bin
```
Then ```
gksudo gedit phexlauncher.sh
```
It will bring up gedit, a text editor. Now paste everything in the next code box into gedit 
```

#! /bin/bash
cd ~/Desktop/phex_3.2.0.102/lib
java -jar   ~/Desktop/phex_3.2.0.102/lib/phex.jar

```
Save and exit.
Back in the terminal, ```
sudo chmod +x /usr/local/bin/phexlauncher.sh
```
Then create an application launcher. The command should be ```
/usr/local/bin/phexlauncher.sh
```

Did that work? If not bring up a terminal and try ```
 /usr/local/bin/phexlauncher.sh
``` Does that work?

---

### Post by jordanmthomas on 2007-09-02
> **Paul133 said:**
> Could you just make a script that said 
```

#bin/bash
cd /home/USERNAME/Desktop/phex_3.2.0.102/lib
java -jar   ~/Desktop/phex_3.2.0.102/lib/phex.jar

```

Then make that executable and make a launcher for the script on the desktop? Or do you need to do more than cd to the directory the jar file is in and run the command? Oh, and if this sript works, replace USERNAME with your username.

or replace USERNAME with $USER
Sorry, couldn't resist. I love me some variables.  :)

---

### Post by PsycoGeek on 2007-09-03
That worked like a charm Paul133, with one exception... " /usr/local/bin" does not exist, so I just removed the "/bin" from the equation and it worked.

Thanks for the heads up on variables jordanmthomas.

---

### Post by Paul133 on 2007-09-03
OK. Glad that worked. I didn't know about $USER. The only bash variable I know is $PATH.

---

### Post by jobsonandrew on 2007-09-08
thanks for the tips, my jar fle ran in the terminal using the 'java -jar' command, but not when i double clicked it, so i made a script like you said and it works great :)

---

### Post by oni5115 on 2008-03-16
> my jar fle ran in the terminal using the 'java -jar' command, but not when i double clicked it

Is this a common issue?  I'm just curious because I am having the same problem with a small project I am working on.  (Strangely, some of the older stuff I did in windows does launch properly on a double click?)  but this new project does not.

I've made sure the jar is executable as well, but it just won't load on double click.  It does however, work perfectly from the command line.  So I was worried it might not work on windows or other machines.  (Haven't tested that yet.)

Out of curiosity, does windows by default call the jar from the current working directory?  If so, and if this is causing a lot of programs to require special scripts to run, why doesn't it act this way by default on Linux?

---

