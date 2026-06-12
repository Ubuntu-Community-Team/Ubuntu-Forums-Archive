---
title: "Making terminal commands run automatically"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by kool_kat_os on 2008-01-05
How Do I make this terminal command run automatically every six hours with no user input:

[HTML]sudo rsync -rtlzv --delete rsync.apache.org::apache-dist /var/www/[/HTML]

Can someone give me step by step instructions?

Thanks

---

### Post by kool_kat_os on 2008-01-05
anyone??

---

### Post by aktiwers on 2008-01-05
You might want to have a look here:
[http://www.aota.net/Script_Installation_Tips/cronhelp.php3](http://www.aota.net/Script_Installation_Tips/cronhelp.php3)

---

### Post by stroyan on 2008-01-05
Run "sudo crontab -e" to edit the crontab entry for root.
Use the editor to change the file contents to this-```
# m h  dom mon dow   command
0 0 * * * rsync -rtlzv --delete rsync.apache.org::apache-dist /var/www/
0 6 * * * rsync -rtlzv --delete rsync.apache.org::apache-dist /var/www/
0 12 * * * rsync -rtlzv --delete rsync.apache.org::apache-dist /var/www/
0 18 * * * rsync -rtlzv --delete rsync.apache.org::apache-dist /var/www/
```
This tells the cron process to run your command at four specific times each day.

---

### Post by nhandler on 2008-01-05
Like aktiwers said, you would use cron to acheive this. Be sure to use "sudo crontab -e" when you go to edit the file. That will ensure that the command is run with root privileges.

The cron line would look like this:
> * */6 * * YOUR COMMAND HERE

For the command, you have two options. The first is to put the actual rsync command there. The second is to store the rsync command in a bash file. Then, for the command you would just have it execute the bash file. Either way will work. I personally prefer the bash file method because it makes it easier to modify the command at a later point in time.

One thing you should keep in mind is that the path environment variable is different for cron. This means that you need to use the absolute path for files, commands, and bash scripts. To find out the absolute path for a command, you use "which". So for rsync, you would enter "which rsync" in a terminal. It would then tell you the absolute path of rsync. You would then use that path in your command instead of plain old "rsync".

---

### Post by kool_kat_os on 2008-01-05
I just saved a file to my desktop called "cron.txt" and I when to terminal and typed 
"crontab -u myusername /home/mysuername/Desktop/cron.txt"
[HTML]
* 6 * * * sudo sync -rtlzv --delete rsync.apache.org::apache-dist /var/www/[/HTML]

Now what?

---

### Post by kool_kat_os on 2008-01-05
anyone(again)??

---

### Post by kool_kat_os on 2008-01-05
help me please!!!!

---

### Post by kool_kat_os on 2008-01-05
huh...

---

