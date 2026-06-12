---
title: "wrapper script question"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by ephman on 2006-04-02
hi,

i have to run growisofs in root, long story.  but i found these instructions and not sure what to do.  i put the code into a text file and tried to execute it but it didn't work?  here's the instruction i found.

consider running following wrapper script under sudo( 8 ) in place for real growisofs binary.

            #!/bin/ksh
            unset SUDO_COMMAND
            export MKISOFS=/path/to/trusted/mkisofs
            exec growisofs "$@"

any help with these instructions would be really appreciated.

thanks,
ephman

---

### Post by trent dillman on 2006-04-02
try this instead:

Open gedit as root (sudo gedit)

```

#!/bin/bash
unset SUDO_COMMAND
export MKISOFS=`which mkisofs`
exec growisofs "$@"

```

Save your file as /usr/bin/growisofs.wrapper

Close gedit, then make it executable:

```
sudo chmod 755 /usr/bin/growisofs.wrapper
```

You should then be able to run it in a terminal

```
sudo growisofs.wrapper (options)
```

---

### Post by ephman on 2006-04-02
hi,

when i try to execute it i get this error:

/bin/ksh: bad interpreter: No such file or directory


any ideas?

thanks,
ephman

---

