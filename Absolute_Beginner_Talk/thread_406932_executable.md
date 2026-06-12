---
title: "executable"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-04-11
Hey all i was wondering how to make an executable file that will open up a picture and play a sound file.  If anyone knows how or has a tutorial that would be great.
Thanks.

---

### Post by Bachstelze on 2007-04-11
Just make a simple shell sript that runs the coommand for you, for example :


```
#!/bin/bash

firefor /path/to/image.jpg
```

will open said image in Firefox when run.

---

### Post by endlessurf on 2007-04-11
My next question is that, will I just put that into a file and save it as a specific extension?

---

### Post by Bachstelze on 2007-04-11
no specific extension. Save the file with any name you want and run it with

```
bash nameOfFile
```

---

### Post by chamberlain2006 on 2007-04-11
You don't need to use a file extension for executables.  Simply /path/to/file/fileandsound will do.  Also, to make it executable, go into terminal and type:  "sudo chmod +x /path/to/file/fileandsound".  Thats it!

---

### Post by endlessurf on 2007-04-16
Thanks for the help,  my next question is how do I kill the program from with in the terminal.

---

