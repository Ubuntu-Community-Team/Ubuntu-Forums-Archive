---
title: "How do I change the sides of the close/minimize/maximize buttons?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-09-23
On Ubuntu (gnome, I havent tried KDE yet) they are on the upper right, like in windows and I hate that, but in this screenshot of a theme from kde-look the buttons are on the right side like in macs. Am I able to change sides or is it just a kde thing?

---

### Post by henriquemaia on 2006-09-23
You can do that doing the following steps:

1: install gconf-editor (I don't know if it's installed by default) by typing the next command on a terminal:

```
sudo aptitude install gconf-editor
```

2: run gconf-editor (press alt+f2 and on the Run Application, type **gconf-editor**

3: on gconf-editor, open the **apps** folder, then **metacity**, and then [B]general

[/B]4: go to button_layout and edit the entry beside it. 

It's easy to understand how it works. On the long description below, you can read:

[I]The value should be a string, such as "menu:minimize,maximize,close"; 
the colon separates the left corner of the window from the right corner, and the button names are comma-separated.[/I]
So, to achieve what you want, you would type there:

"close,maximize,minimize:menu"

Hope this helps.

---

### Post by Brendantb on 2007-02-12
Hi, 

Do you know if this works for Xubuntu? I don't think it runs on Metacity. 

Can someone point me in the direction of the right files to edit?

---

