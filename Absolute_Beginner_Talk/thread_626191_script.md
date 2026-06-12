---
title: "script ?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Malice007 on 2007-11-28
ok I have a dell 1420n laptop and I read this on the dell site. But my question is how do you run a script? Does all scripts need to run on boot up? Here is the info I got off of dell:

 Suspend and Hibernate do not work very well with nVidia 8400M video controller and the 'nvidia-glx-new' driver
Systems Affected: Inspiron 1420n
Impact: Unable to suspend and hibernate properly
Workaround: Run the following script

#!/bin/bash
# Workaround for Suspend and Hibernate with nVidia video cards
perl -p -i -e "s|MODULES=\"\"|MODULES=\"uvcvideo\"|g;" /etc/default/acpi-support
perl -p -i -e "s|SAVE_VBE_STATE=true|SAVE_VBE_STATE=false|g;" /etc/default/acpi-support
perl -p -i -e "s|POST_VIDEO=true|POST_VIDEO=false|g;" /etc/default/acpi-support




How do I even run this? I see other places that tell me to run scripts....and I have no clue how to even run it.... I know I need to trust the person once I learn how....but thats the thing I do not even know where to start hehe :)

---

### Post by nhandler on 2007-11-28
Copy that stuff to a new text file. Save the file somewhere on your computer. I'll assume you saved it to your home folder (/home/YOURUSERNAME) with a name of 'script'. Now, launch a terminal (Applications->Accessories->Terminal). Type this command

```

chmod +x ~/script
sh ~/script
```

That should run the script. I haven't used that script before, so I am not sure if it is meant to run at start up. If it is, take a look at System->Preferences->Sessions. Under Start Up programs, click add. For the command, put
```
sh ~/script
```
You can put anything for a name and comment. This will have the script run everytime you log in.

---

