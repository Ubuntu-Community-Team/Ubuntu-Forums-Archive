---
title: "An ignorant user with a question"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Somenoob on 2006-07-03
I am trying to run a shell script file, how do i execute this type of file?

I know it's done via the terminal, but i do not know the command.

---

### Post by scxtt on 2006-07-03
if it's executable (rwxr-xr-x) just put ./ infront of it, for example - if the script is called "hello_world.bash":
[indent]./hello_world.bash[/indent]and make sure the interpreter is on the 1st line, #!/bin/bash ...

---

### Post by th3james on 2006-07-03
prefix the filename with ./
e.g.
./yourscriptname

---

### Post by Somenoob on 2006-07-03
thanks that helped.

---

