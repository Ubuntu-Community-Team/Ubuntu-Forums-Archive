---
title: "Frostwire and XGL"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Copperteeth on 2007-01-21
Hi i have a problem with Frostwire and XGL. I am using Ubuntu 6.10 with Java 1.5
Everything is ok when i start Frostwire without XGL but if it is active i have only a blank white screen. I know xgl has problems working with java but is there maby a workarround because i dont want to have to logout, switch sessions and then log back in just to use frostwire!

---

### Post by rabid9797 on 2007-01-28
im having the smae problems(but with beryl)

---

### Post by MasterOfDisaster on 2007-01-28
#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire

Save as whatever you want such as runfrostwire, chmod +x (or right click, choose properties, Permissions, and Allow Executing File as a Program), and run.
If you want to get fancy, point your launcher to the script.
This works for me.

---

### Post by mahiyar on 2007-01-28
The answer is in this thread, [http://ubuntuforums.org/showthread.php?t=316398&highlight=frostwire+beryl+script](http://ubuntuforums.org/showthread.php?t=316398&highlight=frostwire+beryl+script) I'am also using the same script to run frostwire.

---

### Post by pparks1 on 2007-02-25
Just a quick FYI in case you run into the same thing that I did.

in the script below, make sure that you put your actual machine hostname in the export HOSTNAME line.   So, if you have changed your hostname from the default of HOSTNAME, you will need to put in the actual name or frostwire may continue to launch as a blank window.


> #!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=put_actual_hostname_here
/usr/bin/frostwire

---

### Post by 9.daemon on 2007-03-05
> **MasterOfDisaster said:**
> #!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire

Save as whatever you want such as runfrostwire, chmod +x (or right click, choose properties, Permissions, and Allow Executing File as a Program), and run.
If you want to get fancy, point your launcher to the script.
This works for me.


Thanks a ton this worked perfectly for me :)

---

