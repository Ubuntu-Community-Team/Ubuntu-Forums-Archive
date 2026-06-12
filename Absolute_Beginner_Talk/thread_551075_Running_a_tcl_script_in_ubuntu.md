---
title: "Running a tcl script in ubuntu"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by silverace99 on 2007-09-14
Hi, I am learning tcl, and am running the one that comes with ubuntu.

From what I have read, once you have made a tcl script in a text file, all you have to do is type the text file in a terminal and it will run the script without you having to already be in the tcl environment, i.e. just type hello.tcl and the tcl script in hello.tcl will run.

however experimenting with it shows that doesn't happen. I have to type tclsh hello.tcl to get it running. But that doesn't make sense, because the first line in any tcl script is supposed to activate the environment automatically right?!

Is there maybe some setting with the bash shell that I have to change first or something?

---

### Post by charlesbrooking on 2007-09-15
> **silverace99 said:**
> Hi, I am learning tcl, and am running the one that comes with ubuntu.

From what I have read, once you have made a tcl script in a text file, all you have to do is type the text file in a terminal and it will run the script without you having to already be in the tcl environment, i.e. just type hello.tcl and the tcl script in hello.tcl will run.

however experimenting with it shows that doesn't happen. I have to type tclsh hello.tcl to get it running. But that doesn't make sense, because the first line in any tcl script is supposed to activate the environment automatically right?!

Is there maybe some setting with the bash shell that I have to change first or something?

Try having something like "#!/bin/tcl" as the first line of the file, as you're suggesting, and also setting the execute permission of the file, using a command such as "chmod u+x hello.tcl". You also need to type "./hello.tcl" instead of just "hello.tcl" when running from the command line in its directory.

Things to browse for to learn more are "hash-bang", "man chmod", and general guides on using the command line.

---

### Post by silverace99 on 2007-09-15
> **charlesbrooking said:**
> Try having something like "#!/bin/tcl" as the first line of the file, as you're suggesting, and also setting the execute permission of the file, using a command such as "chmod u+x hello.tcl". You also need to type "./hello.tcl" instead of just "hello.tcl" when running from the command line in its directory.

Things to browse for to learn more are "hash-bang", "man chmod", and general guides on using the command line.

Ok so I did as you advised, I ran it as an executable.

So the first line of my script was > #!/usr/bin/tclsh

and my execution command was > sudo ./hello.tcl which I ran in the same directory as the hello.tcl file.

However all I got back was > sudo: ./hello.tcl: command not found

:(

Any other ideas as to what I have to do?

---

### Post by silverace99 on 2007-09-15
ahh nevermind, I confused the ideas of sudo and chmod. I changed the text file to be an executable with the chmod u+x you suggested and now all  is good. Thanks for your help!

---

