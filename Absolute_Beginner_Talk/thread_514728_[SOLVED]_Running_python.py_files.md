---
title: "[SOLVED] Running python.py files"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by jobbie007 on 2007-08-01
Hi,

I have just switched from openSUSE 10 to Xubuntu on my home server and want to get my hellanzb script up and running again. I am nearly there but for some reason under Xubuntu I have to run;

[COLOR="red"]python hellanzb.py[/COLOR]

Under SUSE I could run;

[COLOR="Red"]hellanzb.py[/COLOR]

The permissions appear to be the same. Is this a path variable problem? Also I have a crontab that pauses and continues the script, which seems to work but I get multiple python processes running whereas before I had the script name in the process list,

This is also try with other scripts not just hellanzb.py,:confused:

Any help greatly received,

Cheers,

Martin.:guitar:

---

### Post by mathewb on 2007-08-01
did you set the executable flag in the permissions? otherwise, it will not run it directly.

---

### Post by nitro_n2o on 2007-08-01
you need ./python_file.py the ./ is the missing part running files without the ./ is a big danger to your system!! and should never do this. It means that . (the current directory) is in your path, which might lead to execute a fake malicious command, maybe a malicious ls that will wipe out all your /home files 
to make the file executable ```
chmod u+x filename
```

---

### Post by jobbie007 on 2007-08-01
> **mathewb said:**
> did you set the executable flag in the permissions? otherwise, it will not run it directly.

i have checked the permissions of the script and all the execute permissions seem to be in order. -rwxr-xr-x for the script. tried running as ./hellanzb.py and get same "not executable" error.

cheers

---

### Post by sessine on 2007-08-01
check the #! line in your script, it may be that python is installed in a different place on ubuntu compared with SUSE.  If it is then you will need to change the #! line to point to the correct location of the python interpreter

---

### Post by jobbie007 on 2007-08-01
That did the trick. Many thanks.:)

---

