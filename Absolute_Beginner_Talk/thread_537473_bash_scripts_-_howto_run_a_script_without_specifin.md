---
title: "bash scripts - howto run a script without specifing the path"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by adhg on 2007-08-28
Hi all,

I have 2 questions regarding bash commands:

I have some scripts that I run in the following manner:

$/home/adriana/scripts/name-of-script.

1. I wonder how can I have this script run without specifying the path. meaning simply to type in the command line: $name-of-script?

2. I am ssh(ing) to another server to retrieve a file. for that, I wrote a script that does everything. How can I enforce a policy that only super user can run this script.

thanks for any pointers
Adriana

---

### Post by dwhitney67 on 2007-08-28
For question 1:

Add the path of where the script resides to your PATH environment variable within your .bashrc (or similar file that is sourced):

For instance:

export PATH=$PATH:/directory/where/script/is/stored

For question 2:

```
  #!/bin/bash

  uid=`id | sed 's/^uid=\([0-9][0-9]*\).*$/\1/'`

  if [ $uid != 0 ]; then
      echo "$0: Permission Denied... you must be logged in as root."
      exit 1
  fi
```

---

### Post by pmg on 2007-08-29
Another approach to question #2 would be to make the script owned by root and executable only by it's owner:
```
sudo chown root *script_name*
sudo chmod 500 *script_name*
```
The solution dwhitney67 gave keeps non-root users from unintentionally running the script, but someone could always make a copy and remove the check to see if it's running under root.  This approach keeps a non-root user from even being able to look at the script.

---

### Post by adhg on 2007-08-29
thank you guys for the insight. 
I got the idea!

adhg

---

