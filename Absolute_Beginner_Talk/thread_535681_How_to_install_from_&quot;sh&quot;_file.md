---
title: "How to install from &quot;sh&quot; file"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Gary.M on 2007-08-26
I have an application (PersonalBrain) that comes as an install file ending in .sh

How do I install this?

---

### Post by Majorix on 2007-08-26
-Right click the file and select properties.
-Open the permissions tab.
-Under that, check "allow this file to be executed" if its not checked.

Now you have two choices after that to run the file. One is easy but you won't see errors. The second isn't easy for starters but you can see any errors that pop up during the install if you use this method.

First method is double clicking the file and selecting run in terminal.

Second method is moving the file to home directory, then opening a terminal, and typing this:
```
sudo ./NameOfTheProgram.sh
```

sudo might and might not be necessary. First try without that and if you get any permission errors use the sudo.

Good luck.

---

### Post by John.Michael.Kane on 2007-08-26
You can try this in the terminal type.

First
```
chmod +x filename.sh
```

Second
```
./filename.sh
```

---

### Post by Majorix on 2007-08-26
So that you aren't confused let me explain what the other poster was doing.

He used chmod instead of the graphical way. It is somewhat a matter of taste which one you use.

And he didn't use sudo when running the file. But with installers you might need it because they can place several files in places you don't have write permissions to. Like I said in my first post, you have to try.

---

### Post by Gary.M on 2007-08-27
Thanks! Done (used graphical option but ran it from the console). All worked OK and in this case didn't use sudo.

---

### Post by Dark Star on 2007-08-27
> **Majorix said:**
> -Right click the file and select properties.
-Open the permissions tab.
-Under that, check "allow this file to be executed" if its not checked.

Now you have two choices after that to run the file. One is easy but you won't see errors. The second isn't easy for starters but you can see any errors that pop up during the install if you use this method.

First method is double clicking the file and selecting run in terminal.

Second method is moving the file to home directory, then opening a terminal, and typing this:
```
sudo ./NameOfTheProgram.sh
```

sudo might and might not be necessary. First try without that and if you get any permission errors use the sudo.

Good luck.

Thanks a ton was loking for it :) Now I have updated my Cf :D can you tell me how can I check that I have newer ver. :lolflag:

---

