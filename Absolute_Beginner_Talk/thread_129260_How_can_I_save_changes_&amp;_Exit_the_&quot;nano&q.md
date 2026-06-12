---
title: "How can I save changes &amp; Exit the &quot;nano&quot; Editor?"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-13
Hello everybody!

I tried to edit my file "**/etc/apt/sources.list**" with gedit, but Ubuntu would not let me.

I then tried to edit the same file with the "**nano**" Editor.

However, if I choose from the Menu "**File\Close Window**", the changes are not saved...

And there is NO "**File\Save**" or "**File\Save As**" in the Menu.

When I go back & re-open the file with "nano" Editor, the changes I have made have not been applied to the file... 

Can somebody help with this?

---

### Post by FrankTM on 2006-02-13
[QUOTE=dvarsam]Hello everybody!

I tried to edit my file "/etc/apt/sources.list" with gedit, but Ubuntu would not let me.

I then tried to edit the same file with the "nano" Editor.

However, if I choose from the Menu "File\Close Window", the changes are not saved...

And there is NO "File\Save" or "File\Save As" in the Menu.

When I go back & re-open the file with "nano" Editor, the changes I have made have not been applied to the file... 

Can somebody help with this?[/QUOTE]
quit: ctrl + x
it then will ask you if you want to store the changes

---

### Post by Adrian on 2006-02-13
Also, don't forget to use **sudo** when you launch the editor.

```
sudo gedit /etc/apt/sources.list

```
or
```
sudo nano /etc/apt/sources.list

```

Otherwise the changes will not be saved.

---

### Post by lha on 2006-02-13
You did use sudo, didn't you?
sudo gedit /etc/apt/sources.list
or
sudo nano /etc/apt/sources.list

In nano, <control>-o saves. <control>-x ask's if you want to save modifications and then exits.

---

### Post by FrankTM on 2006-02-13
[QUOTE=FrankTM]quit: ctrl + x
it then will ask you if you want to store the changes[/QUOTE]
sorry, didn't read the opening post too well...

my bad

---

### Post by dvarsam on 2006-02-13
Yes, I did add the "sudo" upfront.

It all worked well with the "ctrl+x" command.


Thank you all!

Dimitris.

---

