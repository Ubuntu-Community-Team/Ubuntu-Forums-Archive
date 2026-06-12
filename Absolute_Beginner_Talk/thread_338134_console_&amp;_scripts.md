---
title: "console &amp; scripts"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by izua2 on 2007-01-14
Is there a way I can write all the comands I need to run at the console, in a file, and then just run the file, which will run the commands?

Somehow like "bat" files in windows.

Also, is there a way to add these files to the "path", so i just have to type their name, irrespective of the current working directory? thanks.

---

### Post by aysiu on 2007-01-14
Yes! It's called a shell script.

```
sudo nano /usr/local/bin/myscript
``` The text editor *nano* will open. The first line will tell Ubuntu it's a shell script: ```
#!/bin/bash
``` Then you can put in whatever commands you want afterwards. Finally, make it executable: ```
sudo chmod +x /usr/local/bin/myscript
``` Then you can run it with the command ```
myscript
```

---

### Post by izua2 on 2007-01-14
erm..

```

root@izubox:~# vim /usr/local/bin/s_ws_up
root@izubox:~# chmod +x /usr/local/bin/s_ws_up
root@izubox:~# s_ws_up
bash: s_ws_up: command not found
root@izubox:~# ./s_ws_up
bash: ./s_ws_up: No such file or directory
root@izubox:~# cd /usr/local/bin
root@izubox:/usr/local/bin# ls
s_ws_up


```

the file contains:

```

#!/bin/bash
/opt/lampp/lampp start
echo "\nWeb server & utils up!"

```

what's wrong?

---

### Post by wildkarde on 2007-01-14
Most likely this is because /usr/local/bin is not in your path.

Type this
```
echo $PATH
```

If it's not there, you can set a path of your own by
```
cd ~/.bashrc
```

Then look for the PATH= line and add it at the end.

What I personally like to do is adding a bin directory in the home directory and then adding that to the PATH.

```
PATH=$PATH:$HOME/bin
```

---

### Post by aysiu on 2007-01-14
That's weird. Usually when I place stuff in /usr/local/bin, I can run it as a command.

Can you try this in the meantime? ```
cd /usr/local/bin
./s_ws_up
```

---

### Post by rai4shu2 on 2007-01-14
Shouldn't that kind of script (meant for root) be elsewhere? Like maybe "/usr/sbin"?

---

### Post by izua2 on 2007-01-14
Thanks!

I've done it the way with a /bin in the user's folder and added that to the path :) 

But now I've got another issue. What are the ways to handle commands that require sudo/root access?

@aysiu, that way works. but it's easier to run it from any dir :)

---

