---
title: "[SOLVED] How to delete an executable system file?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by tepidarium on 2007-08-03
Hi,

I created a system file while trying to install beryl. It's address is: /usr/local/bin/start_beryl.sh

I made this file executable.  I would like to delete it as it is not functioning properly.  However, when I go to the directory and right click on the file, there is no option to move the file to trash.  

How can I delete this file and reverse its executable function without hurting my system? 

Also, this seems to be the only file located in /usr/local/bin - can I/should I delete this directory and how may I safely do so.

Thank you very much for any advice you can provide.  

I am an ubuntu newbie and really enjoy the OS.

---

### Post by LaRoza on 2007-08-03
How did you install?

---

### Post by Inxsible on 2007-08-03
> **tepidarium said:**
> Hi,

I created a system file while trying to install beryl. It's address is: /usr/local/bin/start_beryl.sh

I made this file executable.  I would like to delete it as it is not functioning properly.  However, when I go to the directory and right click on the file, there is no option to move the file to trash.  

How can I delete this file and reverse its executable function without hurting my system? 

Also, this seems to be the only file located in /usr/local/bin -[COLOR=Red] can I/should I delete this directory and how may I safely do so.[/COLOR]

Thank you very much for any advice you can provide.  

I am an ubuntu newbie and really enjoy the OS.

Yikes !! NO !!

Dont delete the entire folder ! Its a folder for the user created by the system. There maybe files in there, just hidden. if you navigate to the folder and do a Ctrl+H you will see the other files i think

you can delete the file thru a terminal by doing 

```
sudo rm /usr/local/bin/start_beryl.sh
```As long as you are sure its a file that you created you can safely delete it.

---

### Post by tepidarium on 2007-08-03
> **LaRoza said:**
> How did you install?

I installed it by ALT F2  then typing in: sudo gedit /usr/local/bin/start_beryl.sh

the script for that file is:

#!/bin/bash
#
# Start beryl-manager within gnome-session
#
if (( `ps -A -o comm | grep -c '^Xgl$'` == "1" )); then
       DISPLAY=:1 beryl-manager
       DISPLAY=:1 beryl-xgl
else echo "${0}: Error: beryl-manager not launched. Xgl not running?"
fi

I then made it executable by Alt F2  then typing: sudo chmod a+x /usr/local/bin/start_beryl.sh

---

### Post by LaRoza on 2007-08-03
Follow the above advice.

---

### Post by eentonig on 2007-08-03
PS If you are going to use GUI apps that need sudo power, I would advice you to use 'gksudo' and not 'sudo'. You could run in to problems with using sudo for GUI apps

---

### Post by tepidarium on 2007-08-03
Thanks for the tips. I used the above line of code to uninstall the file.

---

### Post by Inxsible on 2007-08-03
> **tepidarium said:**
> Thanks for the tips. I used the above line of code to uninstall the file.
:) Don't forget to mark the thread SOLVED for some other soul !! :)

---

### Post by tepidarium on 2007-08-03
Thanks...marked as solved. The support here is great.

---

