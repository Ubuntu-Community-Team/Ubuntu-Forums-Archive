---
title: "Hello world script"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by tomryan on 2008-04-06
I just installed Ubuntu because we use Unix based enviroments at work and I want to learn more at home. I am unable to get even the simple "Hello, world." script to run.
When I enter "whereis sh" I get "sh:/ bin/sh.distub /bin/sh /user/share/man/manl/sh.1.gz"
My home directory is "tom@tom-desktop:~$"

The script is 
#!/bin/bash/
echo "Hello, world."

I have tried using .bash,. bh, and .sh extension on the file.
I have chmod to u+x
I always get ther error- bash: hello.bash command not found

What am I doing wrong? Thanks:confused:

---

### Post by WearZeeP on 2008-04-06
Try adding a space after the dot, and removing the trailing slash after /bin/bash.
Like so:

#!/bin/bash
echo "Hello, world. "

Not sure if you need to put a space after the dot though, but I have noticed the if you would have had an exclamation sign there, you would need a space after, for some strange reason.

Edit: and yeah, you don't really need to use file extensions in unix/linux

---

### Post by InfinityCircuit on 2008-04-06
It's amusing that there are two posts about the same issue within one minute.  You need to invoke a script not in your path with a trailing backslash: "./yourscript" once it has been made executable.

Or you can just run: sh yourscript

---

### Post by tomryan on 2008-04-06
Using ./myscript worked great.  Thanks

---

