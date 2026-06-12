---
title: "how to list the information about users?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by foxy123 on 2006-07-14
I need to list the info about users created on my system, mainly user ID in command line. My X server is dead so I cannot use Administration/Users and Groups. Is there a command to do it?

---

### Post by aysiu on 2006-07-14
This may not be the best way to approach it, but could you do something like this? ```
cd /home
ls
``` That will give you the usernames but not the IDs. It's a start...

---

### Post by halfvolle melk on 2006-07-14
```
id
```
will show that.

---

### Post by MrHorus on 2006-07-14
```
w
```
```
who
```

Will show information on currently logged in users.

---

### Post by digby on 2006-07-14
> **foxy123 said:**
> I need to list the info about users created on my system, mainly user ID in command line. My X server is dead so I cannot use Administration/Users and Groups. Is there a command to do it?
All the info you need is probably in /etc/passwd.  That file has a lot of extra info, though, so I hacked up a quick python script to print just the user name and user id for anyone who's id is higher than 500 (this excludes all users created for system use only).  If you need more info from it, you can either check /etc/passwd or let me know, and I'll add it to the script.  At this point, modification for something like this is trivial; I just don't know what else you want.

To use:
```
gedit ~/userlist.py
``` paste this into that file
```
#!/usr/bin/python

def split_field(num):
    return line.split(':')[num]

print '%s\t%s' % ('user name', 'user id')
try:
    try:                        # Open the data file and import it
        inFile = open("/etc/passwd", "r")
        for line in inFile:
            if line == "": break    # End if no more lines
            if int(split_field(2)) > 500:
                print '%s\t\t%s' % (split_field(0), split_field(2))

    except IOError:             # Error w/ file i/o
        print "Couldn't open file"

finally:
    try:
        inFile.close()

    except:
        print 'could not close file'

``` then, in a terminal run
```
chmod 755 userlist.py
./userlist.py
```

edit: realized that you wanted this because x is borked, so here's a [link]("http://umdrive.memphis.edu/mhollis/public/userlist.py") to download the file.

---

### Post by foxy123 on 2006-07-14
thanks a lot guys, 'id' command worked nicely for me!

---

