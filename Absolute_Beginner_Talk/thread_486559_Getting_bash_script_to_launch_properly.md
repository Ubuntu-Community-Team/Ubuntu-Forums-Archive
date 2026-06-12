---
title: "Getting bash script to launch properly"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by renzokuken on 2007-06-28
hi, i downloaded emesene (python based msn equivalent) and i'm trying to get it to launch automatically with a desktop icon.

i copied the extracted folder to /home/rob/.emesene and then wrote a simple bash script which i placed on the desktop to use as an icon.

everytime i click on the icon though i get a dialog asking would i like to "run in terminal", "display", "cancel" or "run".

id like to "run" without having to click on anything.........how can i do this?

the bash script is

```

#!/bin/bash

cd /home/rob/.emesene/
./emesene

```

---

### Post by cdiem on 2007-06-28
Actually, you may run the program as an Icon like this:
1. right click on your desktop, "Create new launcher"
2. In the name field write "emesene"
3. In the "run" field write "/usr/bin/emesene" or "/home/rob/.emesene/emesene"
4. Choose an icon

This should work if you double click on the icon afterwards. Is this what you want to do?

Sudo chmod +x would make it executable.

---

### Post by renzokuken on 2007-06-28
yeah thats what i want to do 

i tried it but when i click on the icon nothing happens.

i think i may need to make the /home/rob/.emesene/emesene file executable. i cant remember the command though.

i thinks it something like ```
chmod +x /home/rob/.emesene/emesene
```

is that right?

---

### Post by RomeReactor on 2007-06-28
Hi. **renzokuken**, if it still won't start using the launcher, try filling out the command section like this:
```
sh -c "cd /home/rob/.emesene && ./emesene"
```
 EDIT: Yes, **chmod +x** to make it executable.

---

### Post by renzokuken on 2007-06-28
yup that nailed it, thanks both of you

---

### Post by cdiem on 2007-06-28
Or, if you have it in your menu, you can just drag'n drop it to the desktop. 
Yes, I think this would be the command for making it executable (maybe with sudo in front of it); or "sudo nautilus" and changing the privilegies manually, without writing commands.

---

