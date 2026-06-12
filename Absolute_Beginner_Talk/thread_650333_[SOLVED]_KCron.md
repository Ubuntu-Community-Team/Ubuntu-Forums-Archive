---
title: "[SOLVED] KCron"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-12-26
Just something missing here.
I use Kcron to backup to folders to the “Backup Directory” and it works very well. However if I place a new file into one of the sub-folders of the 'Backup' folder on the hard disk it does not transfer into the appropriate folder on the Kingston !!
This is the current command I am using:

rsync -r ~/Documents/Backup /media/Kingston

Can you assist me in this.


Thank you


Bernard

---

### Post by blueridgedog on 2007-12-28
Some simple questions.  Is the media full?

Have you tried it as a sudo command, just to rule our permission issues?

---

### Post by bern1939 on 2008-01-01
Thanks I will try those options


Bern

---

### Post by bern1939 on 2008-01-01
No just cannot get this to work. The copy command is:
rsync -r ~/Documents/LinuxBkup/  /media/KINGSTON

The 12 or so folders in the main folder 'LinuxBkup' copy over fine.
However when I put a subfolder inside one of the 12 folders that new subfolder does not copy
over to the Kingston??

Is there something wrong with the command???

Thanks


Bernard

---

### Post by blueridgedog on 2008-01-01
The command seems find, and if you are running at as 

```
sudo rsync -r ~/Documents/LinuxBkup/ /media/KINGSTON
```

Then there should be no permissions issues.

Show the output of:

```
df
```

While the media is mounted.

Also, show the ouptup of 

```
ls -al /media/KINGSTON/XXX
```

Where XXX is one of the directories that will not copy.  Perhaps there is a name issue.

---

### Post by bern1939 on 2008-01-01
Thanks.... this is a real conundrum!!!
Result of the command 'df' is as per attached screen dump.

I am not clear about how the second command could work because the[COLOR="Red"] new folder[/COLOR] coming from
the main folder on the hard disk i.e. LinuxBkup is obviously not on the KINGSTON stick?

Just to elaborate:

There is a main folder on the hard disk called 'LinuxBkup'
Within that there is a sub-folder called 'Tax'
Within that folder there are several sub-folders which copied correctly when I ran the crontab first.
Now I put a new folder called 'Test' in the Tax folder and run the crontab again.
Result is that the new folder 'Test' is not copied over to the Tax folder on the KINGSTON.

Hope I am making myself clear.

Thanks again


Bernard

---

### Post by blueridgedog on 2008-01-01
Sorry, I meant to type out a ls -al of one of the new directories.

However, I see the DF tells me that the stick is about full.

So it would be good to see:

ls -al /Documents/LinuxBkup/XXX
cat /var/log/messages | grep rsync

where XXX is one of your new directories.

I bet it is getting full.

You can see if there are message about it with:

cat /var/log/messages | grep rsync

---

### Post by bern1939 on 2008-01-02
Thanks for your assistance. I figure the problem is solved.

1.Yes the stick was getting pretty full so I took out several folders and it worked fine.
2.An irregular file which I had downloaded was also causing a problem so I discarded that as well.

All seems to work fine now.

Thanks for your patience and assistance. The problem is cured and I learned a few new things as well. So Happy New year.

I will mark this thread as 'solved'

Thanks again.

Bernard

---

### Post by blueridgedog on 2008-01-02
Glad to help.  The forum process is a bit iterative, but it helps in learning.

---

