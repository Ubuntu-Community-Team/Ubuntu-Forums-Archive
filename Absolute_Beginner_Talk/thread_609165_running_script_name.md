---
title: "running script_name"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by t00n on 2007-11-10
Hello,
I have limited linux experience....i have a simple question as it pertains to running a script.
I'm trying to avoid enter the  "./" before running my own script and just enter the scriptname

for eg: 
when I run
./scriptname.sh    -> it works fine
but when I run
scriptname.sh     -> i get a "bash: scriptname.sh : command not found"

is there a way to solve this?
is there a special command I should add to any file that will allow me to run all my scripts just by entering "scriptname" instead of "./scriptname"?

can anyone help?

---

### Post by matthewcraig on 2007-11-10
You could put your script directory into your PATH variable.

---

### Post by geirha on 2007-11-10
It needs to be in a directory specified in the $PATH-variable. You can add . to the PATH-variable to get the "DOS-feeling", but it's highly reccomended to NOT do that for security reasons. A better way to do it would be to create a directory *bin/* in your home directory, put the script there, and add the line ```
export PATH=$PATH:$HOME/bin
``` to the end of ~/.bashrc

---

### Post by FuturePilot on 2007-11-10
```
cd /location/of/script
```
```
sudo mv script.sh /usr/local/bin/
```
Then you can simply run it by entering scrip.sh in a terminal or ever from Alt+F2

---

### Post by t00n on 2007-11-10
thanks fo helping folks.... i was searching around and tried 
export PATH=.:$PATH as a command and then entered the same command in the ~/.bashrc

is there are different in entering
export PATH=.:$PATH

and 
export PATH=$PATH:$HOME

they seem to say the same thing but i could be wrong since I'm a newbie

---

### Post by geirha on 2007-11-10
adding . to the path is very dangerous, especially setting it first in the path. It will allow you to run an executable file in the directory you're currently in, without prepending ./ to it. Now, say someone managed to log into your computer with an unpriviledged user which had a password that was easy to crack, he could make a malicious script, call it "ls" and put it in all directories that user has write access to. And when you unsuspectingly enter a directory he put it in, and type ls, you're running that malicious code instead of the listing command.

export PATH=$PATH:$HOME adds your home-directory to the path. Only you (and root of course) have write access to that directory, so it's much safer. Though don't make a script called ls in your home directory that runs "rm -rf /" or something ;)

---

