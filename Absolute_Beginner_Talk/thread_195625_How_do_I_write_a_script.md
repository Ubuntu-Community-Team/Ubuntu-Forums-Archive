---
title: "How do I write a script?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by bof on 2006-06-13
I am trying to connect an iPAQ to ubuntu (see another thread somewhere) and think I need a script to enter all the command lines.
I can open a terminal and enter the commannds ok but can't figure how to automate the job.  Help please

---

### Post by jason.b.c on 2006-06-13
Does this help you at all..???

[http://vertigo.hsrl.rutgers.edu/ug/shell_help.html](http://vertigo.hsrl.rutgers.edu/ug/shell_help.html)

:confused:     ;)

---

### Post by bof on 2006-06-13
[http://vertigo.hsrl.rutgers.edu/ug/shell_help.html](http://vertigo.hsrl.rutgers.edu/ug/shell_help.html)

Sorry, but that looks completely baffling to me at present and maybe it's not really what I need.
I open a terminal and type and execute the following commands in turn:

sudo synce-serial-config ttyUSB0 192.168.131.102:192.168.131.201
dccm
sudo synce-serial-start

Do I need a "script" or smething else.

BTW thanks for the swift reply

---

### Post by Gustav on 2006-06-13
1. Make a new file and begin the file with the line #!/bin/bash

2. Write the commands you want to excecute in the file

3. Save the file

4. Make the file excecutable by issuing the command chmod +x <the_file> (or you can edit the files properties via nautilus)

And that's it!

Later you can run the script by typing ./<the_file> when you are in the right directory, or you can move the file to /usr/local/bin - then you can run the script by typing <the_file> anywhere.

---

