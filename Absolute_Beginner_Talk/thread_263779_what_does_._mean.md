---
title: "what does ./ mean?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by wgato on 2006-09-23
to run some scripts i have to put ./ before the script name.  why?

i know . usually means the current directory and / is root
or is this completely unrelated to that?

the reason i'm asking is because i'm having a hard time getting a script to run in cron but i realized i dont know why i type './' and it doesnt google.

thanks

---

### Post by mvaniersel on 2006-09-23
./ tells the shell to look for the script in the current directory

When running scripts or other executables, the shell looks for all directories in the path (/usr/bin, /usr/local/bin, ~/bin, etc.), but that doesn't include the current directory. If the script is located in the current directory you have to make that explicit.

---

### Post by Shay Stephens on 2006-09-23
[http://www.pcmech.com/show/os/359/2/](http://www.pcmech.com/show/os/359/2/)
> The dot slash signifies in Linux that you are operating within that particular folder. It is something that Windows users often forget to use.

---

### Post by wgato on 2006-09-23
thanks for explaining that.
I should add my home directory to my path.

---

