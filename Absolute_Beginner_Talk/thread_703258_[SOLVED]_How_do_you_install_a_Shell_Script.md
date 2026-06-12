---
title: "[SOLVED] How do you install a Shell Script?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-21
**[COLOR="DarkBlue"]I want to install a program, but it's not .deb (debian-based), it's a shell-script. I have already read these instructions (shown below), and they didn't seem to work at all, for me:[/COLOR]**

> You can run the shell script inside a terminal with the command sh. If the script is called test.sh and is on the desktop of user carl, you can install it with "sh /home/carl/Desktop/test.sh". Keep in mind that the script might not have permission to execute in your file-system.
[B]
The filename of my shell-script (seen below) is longer than test.sh (which is given as an example in the instructions),[/B]

```
install-hubble-pro.6.2.0.sh
```

[COLOR="DarkSlateBlue"]**What's the easiest way to install a shell-script, exactly like that one?**[/COLOR]

---

### Post by mdjohnson on 2008-02-21
edited:  misunderstood....

you mean you want to use a shell script to  install some software.

cd ~/Desktop
chmod a+x ./install-hubble-pro.6.2.0.sh
sudo ./install-hubble-pro.6.2.0.sh

try that.  basically you're changing directory to desktop, setting the script as execuable and executing it as root, which is usually needed to install software.




***OLD ANSWER***
Copy it to somewhere that's in your path

sudo cp /home/user/Desktop/test.sh /usr/bin/local

then make it executable

chmod a+x /usr/local/test.sh

then you can type test.sh at the prompt and it'll run

---

### Post by jan quark on 2008-02-21
> then you can type test.sh at the prompt and it'll run 

correct me if I am wrong but shouldn't it be

```
sh test.sh
```
?

---

### Post by mdjohnson on 2008-02-21
if you go through the procedure there it shouldn't need to have sh placed before it as it's executable and in the default path.  

have edited the answer anyway :)

---

### Post by marufaberlin on 2008-02-21
Also works:
put a ./ before the shell script. Then the shell doesn't look in the $PATH and executes in the current directory.

---

### Post by ahuman on 2008-02-24
[COLOR="DarkRed"]Both of you: thanks for your kindness. I appreciate y'all. Both of you helped me more than once.[/COLOR]

---

