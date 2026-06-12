---
title: "[SOLVED] Simple bash script to logout?"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-01-12
I want to run:
gnome-session-save --kill --silent

from a bash script - is this possible? If so, I imagine the script would be very short and sweet. But I haven't created any scripts yet and I'm not sure where to put it, how to make it executable, etc.


The reason I want to do this is in Windows I grew addicted to [SlickRun]("http://www.bayden.com/SlickRun/"). It is sort of like Alt-F2...but all the commands/launchers are customizable. Kind of a cross between Alt-F2 and a scripting interface really. I hope someone makes this for Ubuntu soon!

---

### Post by ByteJuggler on 2008-01-12
Open GEdit, put into it:

```
#!/bin/bash
gnome-session-save --kill --silent
```

Save it as (for example) "LogoutScript".  (By default this goes into your Home folder, unless you specify another.)  Click on "Places"->"Home folder", right click on "LogoutScript", click on the "Permissions" tab, tick "Execute", Click "Close" button.

Thats it, now you have an executable shell script.

If you want to change the permissions from a command prompt instead, you'd do:

```
chmod u+x ~/LogoutScript
```

"u" in u+x means change "user" permissions, +x means "add eXecute permission" 
~/LogoutScript is the path the file to change the permission on.

Hope that helps.

---

### Post by jjsonp on 2008-01-12
That is exactly what I was looking for; thanks!

However, I just discovered Katapult, which is fabulous and similar in concept/implementation to SlickRun. Now I just how to figure out how to add my own shortcuts...maybe I'll combine it with the bash scripting somehow and call those...

---

