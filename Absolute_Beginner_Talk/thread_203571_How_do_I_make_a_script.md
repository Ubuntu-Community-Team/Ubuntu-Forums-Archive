---
title: "How do I make a script?"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by mister_p_1998 on 2006-06-25
Ive put some commands into a text file,
to convert an avi to VCD compatible Mpg

it wont execute as a script, even though I go into properties & click on executable.
heres the commands
they work manually in a terminal

cd mnt/drive2
cd Drive2
sudo ffmpeg -i alien.avi -target ntsxc-vcd alien.mpg
vcdimager alien.mpg

Am I doing something stupid? it opens & closes to fast to read any errors
Thanks
Steve](*,)

---

### Post by taurus on 2006-06-25
Put this line at the beginning of your script!!!
```

#!/bin/bash

```

---

### Post by glinsvad on 2006-06-25
When creating a sequential script (basically a list of commands) it is often wise to use the -e option in the bash environment:
```

#!/bin/bash -e

```

This way, if any of the commands fail (exit with non-zero error code) the script will stop execution. Basically if "sudo ffmpeg -i alien.avi -target ntsxc-vcd alien.mpg" fails, there's is really no point in running "vcdimager alien.mpg" is there?

---

### Post by mister_p_1998 on 2006-06-26
[QUOTE=taurus]Put this line at the beginning of your script!!!
```

#!/bin/bash

```[/QUOTE]

Nope, still didnt work!
Do I have to run the script as Sudo?

---

### Post by Brunellus on 2006-06-26
you have to make the file executable:  

chmod +x scriptname

---

### Post by mister_p_1998 on 2006-06-26
[QUOTE=Brunellus]you have to make the file executable:  

chmod +x scriptname[/QUOTE]

Yep, Did that, as well as setting it as executeable in properties, heres the exact script, it still wont run?

#!/bin/bash -e
cd /mnt/drive2
cd Drive2/vcd
sudo ffmpeg -i alien.avi -target ntsc-vcd alien.mpg
vcdimager alien.mpg

---

### Post by Brunellus on 2006-06-26
best I can tell you is to have it run in a terminal even when you click on it. My guess is that it hangs up on the "sudo" line, waiting for input.

---

### Post by richbarna on 2006-06-26
[QUOTE=Brunellus]best I can tell you is to have it run in a terminal even when you click on it. My guess is that it hangs up on the "sudo" line, waiting for input.[/QUOTE]

Password prompt?

Sorry, it's just that i,ve been playing with scripts too.

What would be the command for the script to automatically enter a defined password at that point?

---

### Post by IYY on 2006-06-26
Why don't you just run the whole script with sudo?

---

### Post by glinsvad on 2006-06-27
Seems to me you have two options:

The GUI-way - save the script, make it executable and run it (e.g. by double-clicking it):
```

#!/bin/bash -e
cd /mnt/drive2
cd Drive2/vcd
gksudo "ffmpeg -i alien.avi -target ntsc-vcd alien.mpg"
vcdimager alien.mpg

```

The terminal-way  - save the script, make it executable and run it as root (i.e. run "sudo ./scriptfile.sh"):
```

#!/bin/bash -e
cd /mnt/drive2
cd Drive2/vcd
ffmpeg -i alien.avi -target ntsc-vcd alien.mpg
vcdimager alien.mpg

```

---

### Post by harishg on 2006-06-27
Create  a local bin directory in /home/xXXX and put the script file in there.You should be able to run it without any problem.

---

### Post by jwd45244 on 2006-06-27
the current directory is not in your path so if you have a script called my-cool-script you must run it as: ./my-cool-script

---

### Post by mister_p_1998 on 2006-06-28
[QUOTE=glinsvad]Seems to me you have two options:

The GUI-way - save the script, make it executable and run it (e.g. by double-clicking it):
```

#!/bin/bash -e
cd /mnt/drive2
cd Drive2/vcd
gksudo "ffmpeg -i alien.avi -target ntsc-vcd alien.mpg"
vcdimager alien.mpg

```

The terminal-way  - save the script, make it executable and run it as root (i.e. run "sudo ./scriptfile.sh"):
```

#!/bin/bash -e
cd /mnt/drive2
cd Drive2/vcd
ffmpeg -i alien.avi -target ntsc-vcd alien.mpg
vcdimager alien.mpg

```[/QUOTE]

Its funny,
if I open the non-working script, copy the content, make a new document, paste it, and save it, make it executeable, it works!
whats up?
Im using the default text editor, is it saving in a strange format?
Steve

---

### Post by glinsvad on 2006-06-28
[QUOTE=mister_p_1998]Its funny,
if I open the non-working script, copy the content, make a new document, paste it, and save it, make it executeable, it works!
whats up?
Im using the default text editor, is it saving in a strange format?
Steve[/QUOTE]

A lot of things can go wrong. The most obvious sources of erros could be:
- The original script was not executable
- The line #!/bin/bash -e was not placed at the very top (no whitespace before)
- If you saved the script as UTF-8 in gedit, special control characters are sometimes saved yet are invisble to the eye. Copy-/pasting might have eliminated them...

To compare the two scripts, which should be identical, try:
```

diff -y script1.sh script2.sh

```
This will output both scripts side by side, and will emphasize lines that differ with | > or <.

Also try:
```

md5sum script1.sh
md5sum script2.sh

```
The two scripts should have identical checksums...

---

