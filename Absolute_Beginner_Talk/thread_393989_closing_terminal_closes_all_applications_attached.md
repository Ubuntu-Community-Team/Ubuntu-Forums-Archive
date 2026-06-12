---
title: "closing terminal closes all applications attached"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by ebin on 2007-03-26
I dont think this is just a Ubuntu problem, and i fear that the solution may be a little more than i barganed for but here is the situation:

I sit down, open a terminal and open a few files and start working. Now I compulsively open terminals to all different places and so sometimes I get annoyed and close them all, of corse when I close the terminal that i opened say gedit from, it kills off all my gedit instances. In fact it kills everything. 

TEST:
open a terminal
type: gedit&
close the terminal

why does gedit close??

actually i just tested this with firefox, and it doesn't close. However i did it on a debian machine and it did. Anyway if someone has found a way to fix this I would be interested to hear.

Thanks

---

### Post by jhenager on 2007-03-26
This is by design. Hit ALT+F2 to run a command like gedit or something else you don't want to terminate with closing terminal.

---

### Post by 23meg on 2007-03-26
If you put an ampersand ("&") at the end of the command line, it will run independent of the terminal. The shell will display its process ID and job number so that you can terminate it manually as well.

---

### Post by justaboutnormal on 2007-03-26
Ya, that's just what happens.  To solve this problem I just use the menus 
gedit: Application > Accessories > Text Editor
If you want to make a custom menu Item go to: System > Preferences > Menu Layout
then click the folder you want the item to appear in then click add item.  Type a name, and the command you would normally type in the terminal.

Some times you need to restart X to get it to appear, but I've never had a problem with accidentally closing a program because I closed a terminal after I made my most visited apps menu items.

---

### Post by ebin on 2007-03-27
I did use apersand, and it still closes certain programs.

---

### Post by ebin on 2007-03-27
Yes ALT-F2 does work, as does the menus, but i dont want to use them. I should be able to open a program from a terminal and then not have to keep the terminal open. Or at least i thought i should be able to. It's funny $firefox& well stay open on ubuntu, BUT will close on a debian system i tried it on. that's really strange. 

Anyway it appears nobody really knows how to fix this without opening the program through some other means.

---

### Post by mcduck on 2007-03-27
Run the programs with nohup. For example 'nohup xmms &' will start xmms separate from terminal, leaving it open even if you close the terminal.

---

