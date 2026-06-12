---
title: "ACPI not running Scripts"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by davebed on 2006-11-26
I am trying to have the following script excecuted automatically when the AC power is removed and the battery is called:
```
#!/bin/bash 

DISPLAY=:0 /usr/bin/aticonfig --set-powerstate=1
```

I put in in a file called **script.sh** (with execute permissions) and placed it in /etc/acpi/battery.d 

The problem is that it doesn't appear to get called.

How can I track this and see why it's not getting executed?

NOTES:
If I execute the code in the TERM it works fine.
```
DISPLAY=:0 /usr/bin/aticonfig --set-powerstate=1
```

If it execute it with sudo:
```
sudo DISPLAY=:0 /usr/bin/aticonfig --set-powerstate=1
```
 I get:
```
sudo: DISPLAY=:0: command not found

```

Perhaps that is useful in solving this little problem?

thank you.

---

### Post by kspider on 2007-10-26
I have the exact same problem.  The scripts actually ARE running, but we're not getting the ATI powerplay result that we want.

I can execute
DISPLAY=:00 aticonfig --lsp
DISPLAY=:00 aticonfig --set-powerstate=1
DISPLAY=:00 aticonfig --set-powerstate=3

I can put those commands in a script and run the script, and it runs fine, changing the ATI powerplay state.

I created a script like
```

#!/bin/sh
DISPLAY=:00 aticonfig --set-powerstate=1
echo "Testing; results: $?" > /home/kspider/Desktop/testfile.txt

```

and placed the script in the /etc/acpi/battery.d/ directory.  When I unplug the ac adapter, the testfile is created on my desktop, but the powerstate does not change.  That is, if it does change, it is changed back.  The testfile reports that the aticonfig command returns code 0 - ie it worked.

Anyone out there have any more insight?

Thanks - kspider

---

