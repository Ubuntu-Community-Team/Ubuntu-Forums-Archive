---
title: "usage of at command"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2008-01-12
Hi,
here is my small script.

> #!/bin/sh

echo 'Hello World!' | tee /dev/tty

The above file has been saved as hello.sh in home directory.

At the terminal I give the following command at 15:30:06

> $at 15:35
warning:command will be executed using /bin/sh
>hello.sh
ctrl d
$-
Nothing happens at 15:35:00, while I was expecting to see Hello World! hello World!
What am I doing wrong? Any help would be appreciated.

---

### Post by dcstar on 2008-01-12
> **gupta_sumesh63 said:**
> Hi,
here is my small script.



The above file has been saved as hello.sh in home directory.

At the terminal I give the following command at 15:30:06


Nothing happens at 15:35:00, while I was expecting to see Hello World! hello World!
What am I doing wrong? Any help would be appreciated.

You are assuming that "at" runs in your home directory and can somehow find (and run) your script (apart from the assumption that it will output to every terminal that is logged in under your user account).

I think that you will find that you have to be a lot more specific with at (and cron) jobs.

Just because things run in a user terminal environment does not mean that they will run in these other environments.

---

### Post by The Cog on 2008-01-12
What's more, /dev/tty is a directory. You can't output to a directory. Your text terminals on Ctrl-Alt-F1 to F6 are /dev/tty0 to /dev/tty5. Gui terminal sessions are /dev/pts/0, /dev/pts/1 etc (use the command **who** to see who is where).

---

### Post by gupta_sumesh63 on 2008-01-12
Thank you very much. I changed my script to 
echo 'Hello World!' | tee /dev/pts/3

and used the at command. It worked like a charm.
thanks again.

---

