---
title: "Please answer this somebody?!!"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by dscott60 on 2007-01-24
I've been trying to get this question answered for two days and nobody replies.  How do you enter multiple lines of code in the terminal?  Do you hit return after each line?  It doesn't look like it in the examples, but I don't understand how to enter multiple lines.

[Desktop Entry] 
Name=NVIDIA Settings
Comment=NVIDIA X Server Settings 
Exec=nvidia-settings Icon= StartupNotify=true Terminal=false Type=Application Categories=Application;System;

---

### Post by Tomosaur on 2007-01-24
If you want to execute a bunch of commands one after the other, you use &&, like this:
```

./configure && make && sudo make install

```

---

### Post by taurus on 2007-01-24
```
first line \
second line \
third line
```
Is that what you're looking for?  

However, I believe the name of that file should be **NVIDIA-Settings.desktop** and it should be saved to** /usr/share/applications**.

```

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA X Server Settings
Exec=nvidia-settings 
Icon= StartupNotify=true 
Terminal=false 
Type=Application 
Categories=Application;System;

```

---

### Post by kvonb on 2007-01-24
If you are trying to save that text to a file, you need to use an editor, for example "vi" if you are using only the terminal, or "gedit" if you have X running (the GNOME desktop).

In the terminal you would type this first:

```
vi nvidia-settings.desktop
```

or

```
gedit nvidia-settings.desktop
```

....then enter all the text that you gave in your original post, save and exit the editor.

---

### Post by ardchoille42 on 2007-01-24
> **Tomosaur said:**
> If you want to execute a bunch of commands one after the other, you use &&, like this:
```

./configure && make && sudo make install

```

That's good but you need to keep one thing in mind. Take, for example, the following command:

```

command1 && command2 && command3

```

command1 will run, but if command2 doesn't run, or errors out, then command3 will not run. Likewise, if command1 doesn't run, or errors out, the other two will not run.

```

mkdir test && cd test && mkdir test2 && cd tesst2 && mkdir test3

```

The directory "test" will be made and the directory "test2" will me made, but the directory "test3" will not be made because of the typo in "cd tesst2", there isn't a tesst2 directory to change to, so the execution of that line of commands stops at the first error.

My point is chaining commands with a double ampersand is good but one needs to make sure all the commands will run and there are no typo's.

---

### Post by Pobega on 2007-01-24
To learn to use vi, run vimtutor on the terminal.

If you want a terminal editor that you are probably more familiar with, try nano. It works like mousepad/gedit/notepad, sans mouse use.

---

