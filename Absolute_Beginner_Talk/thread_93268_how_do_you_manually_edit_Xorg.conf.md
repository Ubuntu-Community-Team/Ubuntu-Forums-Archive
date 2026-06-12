---
title: "how do you manually edit Xorg.conf?"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by slade on 2005-11-21
sorry, quick newb question.  if i open it with a text editor it says its read only and i dont know how to edit it through the CLI, which, im guessing, is what i have to do.

thanks everyone.

---

### Post by Teroedni on 2005-11-21
to manuallly edit it you will ne to run as sudo user
Start the terminal and put in the code below

```
sudo gedit /etc/X11/xorg.conf
```

hope this helps:)

---

### Post by slade on 2005-11-21
[QUOTE=Teroedni]to manuallly edit it you will ne to run as sudo user
Start the terminal and put in the code below

```
sudo gedit /etc/X11/xorg.conf
```

hope this helps:)[/QUOTE]
damn, fast replies here.  thanks, ill try that.

---

### Post by Brunellus on 2005-11-21
and if you're asking this question you probably dont' have X anyway so the CLI way is:

```
sudo nano /etc/X11/xorg.conf
```

Note that this is all case-sensitive.  Also note that you can use any text editor you want(vim, emacs, nano...), so long as you do it as root (i.e. using sudo).

---

### Post by slade on 2005-11-21
[QUOTE=Brunellus]and if you're asking this question you probably dont' have X anyway so the CLI way is:

```
sudo nano /etc/X11/xorg.conf
```

Note that this is all case-sensitive.  Also note that you can use any text editor you want(vim, emacs, nano...), so long as you do it as root (i.e. using sudo).[/QUOTE]
wait...  what?  X?  are you saying what he said wont work for me?

---

### Post by Brunellus on 2005-11-21
gedit will work for you if you are already running an X windows session (in this case, GNOME).  

If and when you break xorg.conf by hacking it manually, you will be without the GUI, and only with the text terminal. 

To repeat, gedit *requires* you to be in a GUI, while nano does not.  If your GUI is broken, you can't use gedit;  you must use a real text-mode text editor like nano, vim, or emacs.

---

### Post by dubz on 2005-11-21
no his will work perfectly...nano is just another text editor.

use gedit though. its more notepad-ish

---

### Post by slade on 2005-11-21
[QUOTE=Brunellus]gedit will work for you if you are already running an X windows session (in this case, GNOME).  

If and when you break xorg.conf by hacking it manually, you will be without the GUI, and only with the text terminal. 

To repeat, gedit *requires* you to be in a GUI, while nano does not.  If your GUI is broken, you can't use gedit;  you must use a real text-mode text editor like nano, vim, or emacs.[/QUOTE]
ahh, okay, thanks.  i wasnt sure what you meant by X.  yeah, i expected GNOME wouldnt work if i altered the file, which is why its read only.  i was planning to use the CLI for all of this, not just open the terminal.

---

### Post by slade on 2005-11-21
thanks everyone, i got my video card working!  i hate the steep learning curve with linux...  but so far, there are a lot of things i like better than windows.

---

