---
title: "termial problem"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-15
Hello folks ,
                 The termianl prompt was working properly before i shut ubuntu down . Now after restarting the terminal prompt is only displaying a "%" sign , previously it was displaying the directory name . Also when i press the up key i get "^[[A"

How can i get my terminal to behave like it used to do before

Thanks

---

### Post by Bachstelze on 2006-12-15
You wanted CSH, I think you got it :D This is its default behavior.

---

### Post by lance_klusener on 2006-12-15
thanks man , i think i will switch back to "bash" and switch to "csh" only when i want using the "chsh" command  , i certainly hope that is possible

---

### Post by Bachstelze on 2006-12-15
Certainly but it is not even needed. As I told you in some previous thread, you can run csh like any other program, do what you need to do with it and then *exit* to go back to your previous shell.

To set bash back as your default shell :

```
chsh -s /bin/bash
```

Then log out and log back in, no need to reboot.

---

### Post by Ben Sprinkle on 2006-12-15
```

sudo apt-get remove chsh

```
Bash is good enough for me.

---

### Post by taurus on 2006-12-15
Why don't you add these two lines to ~/.cshrc if you want to have a nice looking prompt!!!

```

set host=`hostname | awk -F. '{print $1}'`:
set prompt="${host}${PWD}:% "

```

---

### Post by Bachstelze on 2006-12-15
Goat Spirit, for your information, he needs csh to run a shell script that won't run in Bash. Also, the package name is *csh*, *chsh* is the command used to change user infos.

---

### Post by lance_klusener on 2006-12-15
Yes i have changed my shell back to bash , rebooted ( since i dindt knew what else to do :) ) . I will try the remaining things and let u know how did i fare.

Thank you all

---

### Post by Ben Sprinkle on 2006-12-15
> **HymnToLife said:**
> Goat Spirit, for your information, he needs csh to run a shell script that won't run in Bash. Also, the package name is *csh*, *chsh* is the command used to change user infos.

Bash is good enough for me.

---

### Post by Bachstelze on 2006-12-15
But I think telling him to remove csh while he needs it to run his script wasn't the most accurate answer...

---

### Post by mcduck on 2006-12-15
Wouldn't it be possible to just add "#!/bin/csh" to the beginning of the script?

---

