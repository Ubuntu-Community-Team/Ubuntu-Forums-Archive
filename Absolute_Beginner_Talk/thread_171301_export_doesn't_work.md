---
title: "export doesn't work"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by gl1756 on 2006-05-06
I'd like to set an environment variable in a script, e.g.
MY_ENV="192.168.1.1"
export MY_ENV

however, after running the script the variable is not set
any ideas?

thanks

---

### Post by unbuntu on 2006-05-06
make sure you are using bash

if you are, check the enviornment variable by ```
echo $MY_ENV
```

---

### Post by gl1756 on 2006-05-06
thanks for the answer

[QUOTE=unbuntu]make sure you are using bash[/QUOTE]

I'm pretty sure I'm using bash
(e.g. typing in a nonsense command in the terminal I get "bash: ... : command not foud")
Or is there something I have to do within the script to make sure it's executed as a bash script?

[QUOTE=unbuntu]if you are, check the enviornment variable by ```
echo $MY_ENV
```[/QUOTE]

doing this within the script the variable is displayed
doing it in the terminal after having run the script it's not

---

