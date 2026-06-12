---
title: "Shell Script Permissions"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by noynac on 2008-03-10
I have a script named search.sh that in simplified form contains the following:

#!/bin/bash
find / -iname "$1" -type f

When I run this script, the output contains many permission-denied messages (as expected). To remedy this, I moved the script to the /usr/bin directory and added the following to the sudoers file:

# Allow search command
ALL ALL=NOPASSWD: /usr/bin/search.sh

I then reran the search script but still received many permission-denied messages. My questions are:

* Did I do something wrong in my sudoers entry? 

* Does the find command in the script also require an entry in the sudoers file (which I assume would be a bad idea)? 

* Is there a way to get the script to do what I want without compromising security.

BTW, the easy solution is to include sudo before find in the script and that's probably what I will do. For now, I am using this for learning purposes.

Thanks for the help.

---

### Post by scragar on 2008-03-10
just run:
```
chmod +x search.sh
```
on the file to give everyone execute perms for the file.

---

### Post by jordanmthomas on 2008-03-10
Well, you'd need to run 
```
sudo scriptname
``` 
the way you've set it up.  No password will be asked, though.

If you don't want to search places you're not allowed to search, you can also do this:
```
find / -iname "$1" -type f 2>/dev/null
```
to ignore the errors.

Finally, to make the script just run as root without sudo you can look up how to set SUID on a file.  I'll leave how to do that to you since you said you're interested in learning.

---

### Post by noynac on 2008-03-10
> **scragar said:**
> just run:
```
chmod +x search.sh
```
on the file to give everyone execute perms for the file.

Scragar,

Thanks for the response. I should have been clearer. The script does have execute permission. An example of the output I'm talking about is:

bob@dell:~$ find / -iname pdf -type f
find: /var/run/cups/certs: Permission denied
find: /var/cache/setup-tool-backends/debug: Permission denied
find: /var/cache/setup-tool-backends/backup: Permission denied
find: /var/cache/system-tools-backends/backup: Permission denied
<snip>

---

### Post by noynac on 2008-03-10
> **jordanmthomas said:**
> Well, you'd need to run 
```
sudo scriptname
``` 
the way you've set it up.  No password will be asked, though.

If you don't want to search places you're not allowed to search, you can also do this:
```
find / -iname "$1" -type f 2>/dev/null
```
to ignore the errors.

Finally, to make the script just run as root without sudo you can look up how to set SUID on a file.  I'll leave how to do that to you since you said you're interested in learning.
Jordan,

Thanks for the response. I tried sending the error messages to /dev/null, and this did clean up things a lot, but it also skipped files.

For example, the command:

```
sudo find / -iname hplip.conf -type f
```

...yielded...

/etc/hp/hplip.conf
/home/noynac/.hplip/hplip.conf
/root/.hplip/hplip.conf

The command:

```
find / -iname hplip.conf -type f 2>/dev/null
```

...yielded...

/etc/hp/hplip.conf
/home/noynac/.hplip/hplip.conf

I'm not familiar with SUID, so I'll do some research on this.

Thanks again.

noynac

---

