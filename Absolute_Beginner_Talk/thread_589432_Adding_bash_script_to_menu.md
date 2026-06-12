---
title: "Adding bash script to menu"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-10-24
Hi,
I have a bash script 'db2ccRun' like this:
```

#!/bin/bash
. /home/tonyr/.bashrc
. /opt/ibm/db2/V9.1/bin/db2cc

```

I would like to add this bash script to menu. So I select system>preferences>maim menu
and select Browse from window and select file db2ccRun, so command field shows the following command: /home/tony/db2ccRun.

But when clicking on application>mymenu>myapp nothing happens. No error and nothing happens.

How to run bash script from menu?
Thanks,
Abcuser

---

### Post by realvz on 2007-10-24
have you made it executable by doing
chmod 775 your_script_name.sh

---

### Post by abcuser on 2007-10-24
Hi,
I have done: chmod 777 myscript
Interesting it runs ok from Terminal

Any idea?
Thanks
Abcuser

---

### Post by realvz on 2007-10-24
try doing 
sh /home/tony/db2ccRun
instead of just
/home/tony/db2ccRun

---

### Post by hyper_ch on 2007-10-24
How about:

```

sh /home/tony/db2ccRun

```

Realvz: Didn't see you also suggested the "sh" way ;

Or you could put the script into /usr/bin/

---

### Post by abcuser on 2007-10-24
Hi,
I have tried: sh /home/tony/db2ccRun
I have also tried copy to /usr/bin

Doesn't work.

Is there any way I could monitor what is wrong? Where to look if some errors are displayed, because I don't get any error and I don't get any program startup.

Thanks,
Abcuser

---

### Post by hyper_ch on 2007-10-24
as you have it copied now to /usr/bin... just enter "db2ccRun" anywhere in the terminal. Does that work?

---

### Post by kevdog on 2007-10-24
Do you need the . (periods) in the script at the beginning of each line.  You only need periods when running the script from the same directory.

What does this statement do?:
. /home/tonyr/.bashrc

---

### Post by hyper_ch on 2007-10-24
no, the '.' is used to define a directory where it shall be looked for -->  ./SCRIPT means look in the current directory for an executable named SCRIPT. Otherwise, without the . , it will look in the normal environment paths but not in the current directory.

---

### Post by abcuser on 2007-10-25
> **hyper_ch said:**
> as you have it copied now to /usr/bin... just enter "db2ccRun" anywhere in the terminal. Does that work?
I have copied file to /usr/bin. Exit terminal window and start a new window. Then I have executed:
db2ccRun from terminal and got error:
bash: db2ccRun: command not found

BTW: my PATH system variable looks like:
/usr/local/sbin:/usr/local/bin:/usr/sbin:**/usr/bin**:/sbin:/bin:/usr/games:/home/db2inst1/sqllib/bin:/home/db2inst1/sqllib/adm:/home/db2inst1/sqllib/misc

---

### Post by abcuser on 2007-10-25
> **kevdog said:**
> What does this statement do?:
. /home/tonyr/.bashrc
It runs my bashrc profile file. I need to run this because some extra environment must be executed before second command.

Executing ./db2ccRun from terminal works fine, but from Main Menu it doesn't and doesn't report any error, just program is not executed.

---

### Post by PointyWombat on 2007-10-25
type:

#which db2ccRun

if it's path'd correctly, it will come back:

# /usr/bin/db2ccRun

---

### Post by PointyWombat on 2007-10-25
Remove the leading period from line 3.

---

### Post by abcuser on 2007-10-27
Hi,
strange thing. After executing 'which' command nothing is returned.
```

abc@abc-ubuntu710:/usr/bin$ pwd
/usr/bin
abc@abc-ubuntu710:/usr/bin$ ls -l db2*
-rwxr-xr-x 1 root root 64 2007-10-25 08:32 db2ccRun.sh
abc@abc-ubuntu710:/usr/bin$ #which db2ccRun
abc@abc-ubuntu710:/usr/bin$ which db2ccRun
abc@abc-ubuntu710:/usr/bin$ 

```
Note: I have executed 'which' command by # and without #. In both cases nothing is returned.
Any idea?
Abcuser

---

### Post by PointyWombat on 2007-10-29
try:

which db2ccRun.sh

that is what I meant to say. The idea is to see if it's in your path, but it must be because it's in /usr/bin. Also, the '#' symbol is simply a way to identify a shell prompt in the example, that's all.

Ultimately though, I believe that the problem is your script in that there's the leading period on line 3.  Line 2 needs a period because you're sourcing an environment, but line 3 is an execution.

---

### Post by abcuser on 2007-10-31
Hi,
using Gutsy. I am wondering what is the difference between the following commands:
```

./directory/execution_file.sh
. /directory/execution_file.sh

```
Note: Second command between (.) and (/) is space.

Thanks,
Abcuser

---

### Post by rhodry on 2007-10-31
I am not running Gutsy at the moment (dual boot PCLinuxOS) but I am pretty sure I remember seeing the same option there. When you create a 'launcher', whether on the desktop or the main menu, I think there should be an option to toggle that says something like "Run In Terminal". I am pretty sure you have to set this option to ON, becuase the command is executing a single or multiple shell command(s). Look carefully at the options offerred.

Hope this helps,
Rhodry.

---

### Post by abcuser on 2007-11-03
> **PointyWombat said:**
> Ultimately though, I believe that the problem is your script in that there's the leading period on line 3.  Line 2 needs a period because you're sourcing an environment, but line 3 is an execution.
Hi,
I have changed the script to:
```

#!/bin/bash
. /home/igor/.bashrc
/opt/ibm/db2/V9.1/bin/db2cc

```
I run the script from terminal and runs OK - just like with (. ) at beginning at line. But running this script from menu it just doesn't run.

Any idea?
Thanks,
Abucser

---

### Post by abcuser on 2007-11-03
[QUOTE=rhodry;3676382 When you create a 'launcher', whether on the desktop or the main menu, I think there should be an option to toggle that says something like "Run In Terminal"[/QUOTE]
Hi,
I have tried this too. From System | Preferences | Main menu and then in Launcher Properties I selected "Application in Terminal". I tried to execute script from menu and the blink of terminal is shown and hided but application that script should execute still doesn0't pop up.

By the way there are two options in Launcher Properties Type: "Application" and "Application in Terminal". I have tried them both by neither is working.

Any idea?
Thanks,
Abcuser

---

### Post by PointyWombat on 2007-11-08
as far as the difference between ./some/command and .<space>/some/command,  the leading period represends the current directory you're in, and is akin to how ".." is the parent directory. This is just running the command with a relative path from your current working directory.

as far as the period by itself, a space, then a command, well that's incorrect syntax. In bourne based shells, such as bash, it's a mechanism to source envornment variables. such as in your first line, which is setting up the environment.  For example, if you make changes to your .profile file, you can read and set those changes by running ". ./.profile" for example.

as far as the real problem,  lets see if it's actualy doing anything when being run from the menu. Add the following to the end of your command line like so:

/opt/ibm/db2/V9.1/bin/db2cc **2>/tmp/db2cc.log**

..which will dump all errors (1=stdout, 2 = stderr) to the specified log file. Check the file /tmp/db2cc.log and post what it contains.

PointyWombat

---

