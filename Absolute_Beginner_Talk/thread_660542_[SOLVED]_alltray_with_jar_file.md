---
title: "[SOLVED] alltray with jar file?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by gschoppe on 2008-01-06
I'm looking to run the command "java /home/gschoppe/Scripts/Ted/ted.jar" with alltray utilizing the icon "/home/gschoppe/Scripts/Ted/ted.png", but I can't get the command string to work out right...

would it be:

alltray java /home/gschoppe/Scripts/Ted/ted.jar -i /home/gschoppe/Scripts/Ted/ted.png

or:


alltray "java /home/gschoppe/Scripts/Ted/ted.jar" -i /home/gschoppe/Scripts/Ted/ted.png

or something else entirely?

---

### Post by SOULRiDER on 2008-01-06
I would go for the " option, just in case. Try it.

---

### Post by FuturePilot on 2008-01-06
I'm not sure about the alltray command but to run a .jar file with Java it needs to have the -jar option
```
java -jar /home/gschoppe/Scripts/Ted/ted.jar
```
Perhaps this
```
alltray java -jar /home/gschoppe/Scripts/Ted/ted.jar -i /home/gschoppe/Scripts/Ted/ted.png
```

---

### Post by SOULRiDER on 2008-01-06
The " have to be added or it will take each part as a different argument. IMHO it should be
```
alltray "java -jar /home/gschoppe/Scripts/Ted/ted.jar" -i /home/gschoppe/Scripts/Ted/ted.png
```
Another option would be to make a simple bash script that could just contain java -jar /home/gschoppe/Scripts/Ted/ted.jar and call that script.

---

### Post by gschoppe on 2008-01-06
Thank you, It finally works!!

the command was:

alltray 'java -jar /home/gschoppe/Scripts/Ted/ted.jar' -i  /home/gschoppe/Scripts/Ted/ted.png

next, I added the png (with the same name as the package) to the root level of the archive, using archive manager, and now I can just use:

alltray 'java -jar /home/gschoppe/Scripts/Ted/ted.jar'

to load Torrent Episode Downloader to the system tray !!

I finally worked around that glitch in TED that broke tray support in Ubuntu!

Thank you all.

now to add it to my session.

---

### Post by SOULRiDER on 2008-01-06
Thats good news :) Could you please mark the thread as solved? Thank you!

---

