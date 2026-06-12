---
title: "crontab : nothing happens. assist me please"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Linux Lover on 2006-12-04
Using Ubuntu D/D. Trying to write a crontab file.
There is no file named /etc/cron.allow or /etc/cron.deny.

I am giving the following commands
```
sudo crontab -u username -e
```

Then I am editing the file as follows...
```
15 10 05 12 2 ls /
```

I am assuming that the above file will burst at 5th Dec. 2006 (Tuesday) at 10:15 am and will display the root directory structure.

But the fact is that, nothing happens at 10:15 am. What is wrong in me? And how to write such a meaningful crontab file?

Thanks in advance.

regards
linuxlover

---

### Post by David_T on 2006-12-05
OK, so whatever you put in the crontab, by default the output is usually emailed to you (the ``mail'' command), but Ubuntu doesn't have ``mail'' installed by default.  

There are a number of things you can do here as a test command in your crontab.  You could redirect the ouput to a file:
```

ls / > ~/testfile

```
You can call up an X program such as gimp by using the following syntax in your crontab:
```

export DISPLAY=:0 && gimp

```
Finally, if you really want the output on your terminal, you can use ``wall'' or ``write'', like this:
```

echo "this is a friendly message" | write <username>

```

---

### Post by lloyd_b on 2006-12-05
First problem - you're running the "ls" command, but you're not telling it to send the output anywhere.  It may or may not email the output to you (depends on how your machine is configured). 

Second point - you do NOT need both "dom" and "dow" in this instance.  "dow" should be used if you want something to run on a particular day each week (such as "every monday").  For values that aren't needed, put an asterisk ("*") in that column.

```
15 10 05 12 * ls / > ~/root.txt
```

Will run the command "ls /", and send it's output to a file called "root.txt" in your home directory.  It will run at 10:15 a.m. on December 05.

I would recommend putting the actual command to be executed in a shell script, and then executing the script.  Create a file that contains the command(s), then "chmod 700 {filename}" to make it executable.  In "crontab -e":
```
15 10 05 12 * {filename}
```

Where {filename} is the name of your script.

Having the crontab executing a script provides a couple of advantages:

1.  You can easily create scripts with dozens of separate commands (hard to put on the command line in crontab).
2.  You can easily "tweak" the script without having to edit the crontab.


Lloyd B.

---

### Post by SuperMike on 2006-12-05
> Ubuntu doesn't have mail installed by default.

* If you add MAILTO directive in crontab, it will send mail for any output from crontab events. It sends this to /var/spool/mail/<user id>

* If you install mailx and postfix local mode with apt, you can then take Thunderbird and point it at a maildir of /var/spool/mail/<user id> and see your mail that way. Or, you can just use cat or tac to view the mail file natively.

* I also prefer to edit /etc/crontab instead of the various crontabs. It makes it far easier to manage. The only difference is the extra column for what ID to run it under.

---

### Post by Linux Lover on 2006-12-05
Understand something but nees to be more clear the matter. Can you please refer me a site for a good crontab tutorial?

regards
linuxlover

---

### Post by Linux Lover on 2006-12-05
All respected thread repliers, the thing is now going well. I have tested with,
ls / > ~/abc.txt and it delivered the desired result in ~/abc.txt file.
also tested, export DISPLAY=: && gimp and it started the Gimp program.

Thank you all for helping me. But I want to know more to write my own cron job. Please help me by refering some good site, from where I can know more about cron job.


regards
linuxlover

---

### Post by dbd on 2006-12-05
The Documentation links at the bottom of this page may be useful:
[http://en.wikipedia.org/wiki/Crontab](http://en.wikipedia.org/wiki/Crontab)

---

### Post by Linux Lover on 2006-12-05
> **David_T said:**
> OK, so whatever you put in the crontab, by default the output is usually emailed to you (the ``mail'' command), but Ubuntu doesn't have ``mail'' installed by default.  

There are a number of things you can do here as a test command in your crontab.  You could redirect the ouput to a file:
```

ls / > ~/testfile

```
You can call up an X program such as gimp by using the following syntax in your crontab:
```

export DISPLAY=:0 && gimp

```
Finally, if you really want the output on your terminal, you can use ``wall'' or ``write'', like this:
```

echo "this is a friendly message" | write <username>

```


All are going well, but how do I execute non X commands(like wget) and shell scripts?

regards
linuxlover

---

