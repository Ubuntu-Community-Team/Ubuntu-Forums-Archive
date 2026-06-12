---
title: "Crontab Question"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-30
Using Ubuntu 7.10

I understand from reading the material that for cron jobs that I wish to run under my own user account, I should stick with using crontab -e to edit my local cron jobs rather than editing the system-wide /etc/crontab.

Firstly I type 'crontab -l' and get 'no crontab for bernard'

So then I type 'crontab -e', ...  nano opens and I insert a simple test script as follows and name it 'myfile.sh' and save it in my home folder 'bernard'

#!/bin/sh

SHELL=/bin/sh

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin; 
* * * * *  cp ~/Documents/Envelopes/XXX.doc  ~/Documents/TEST

I did: chmod 0755 myfile.sh

I type ./myfile.sh and get:
bernard@bernard-desktop:~$ ./myfile.sh
./myfile.sh: 3: /home/bernard: Permission denied
./myfile.sh: 4: Desktop: not found


My questions are:
1.Where is the error
2.Where exactly should the file be saved?
3.How do I get it to run automatically

Note: The copy function works perfectly from the terminal!


Thanks for your help


Bernard

---

### Post by hyper_ch on 2007-11-30
I'd use this as script:

```

#!/bin/bash
cp ~/Documents/Envelopes/XXX.doc ~/Documents/TEST

```

And then add a cron entry:

```

* * * * * /path/to/script.sh

```

Or directly use a cron entry:

```

* * * * cp ~/Documents/Envelopes/XXX.doc ~/Documents/TEST

```

---

### Post by bern1939 on 2007-11-30
Thank you so much... very simple really.

I notice that having made any changes to the crontab file one needs to do a crontab xx.sh at the terminal each time for things to work correctly.

Thanks again


Bernard

---

### Post by ptn107 on 2007-11-30
> #!/bin/sh

SHELL=/bin/sh

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/us r/sbin:/usr/bin;
* * * * * cp ~/Documents/Envelopes/XXX.doc ~/Documents/TEST

The problem is that you actually need to use single quotes on commands that have spaces.

The entry in crontab should be:
```
* * * * * 'cp ~/Documents/Envelopes/XXX.doc ~/Documents/TEST'
```

Cron was interpreting your original entry as three separate commands instead of a single *cp* command with two options.  (Cron interprets differently than the shell does, that's why your original command worked in the terminal and didn't work here.)

Using a script and executing the script via crontab (like described in the previous post) is by far the better method anyway.

---

### Post by bern1939 on 2007-11-30
Very good ..... thank you


Bernard

---

