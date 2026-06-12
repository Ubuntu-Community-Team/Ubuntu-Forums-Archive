---
title: "Help please"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by Ali Karam on 2006-06-08
Hi,

I'm very new to linux and I was told that rc.local is a startup script

This is what I have in rc.local
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```

I don't think I'm understanding this, because it says
"This script is executed at the _END_ of each multiuser runlevel."

Can anyone tell me when should I put commands that I want to be excuted on boot ?

Thanks

---

### Post by darkali on 2006-06-09
The commands to be started on boot should be at
System > Preferences >  Sessions.

Click 'Add' and then type the command your want.

---

### Post by Ali Karam on 2006-06-09
Thanks darkali

---

