---
title: "Bash script"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by towersoft on 2006-09-02
Hi,
    I am trying to run a couple of commands via a bash script, what I have so far is:

#!/bin/bash
gnome-terminal --geometry 80x30

    This works to spawn the Terminal window with more available lines than normal. However I would like it to run a command in the terminal after it has opened, does anyone know how to do this? :confused: 

    Just to explain what I am trying to do I have installed testdisk to scan and recover partitions. When you open testdisk it complains that it needs to open with atleast 25 lines and the default that terminal opens with is 24. I was hoping that the terminal profile editor would give me the option to open it with more lines but it does not. I want to have a link in alecarte to open testdisk so that all my tools are in one place.

    Any help would be greatly apreciated, thanks!

---

### Post by gborzi on 2006-09-02
From the gnome-terminal manpage:
> -e, --command=STRING
                 Execute the argument to this option inside the terminal.

       -x, --execute
                 Execute the remainder of the command line inside  the  termi&#8208;
                 nal.


---

### Post by towersoft on 2006-09-02
Thanks for your reply! I read that page and tried those commands but I dont seem to be able to get it to do anymore than just open the terminal window. I have tried all sorts but I just cannot get it to work in the Terminal. What I need to do is make it run "sudo testdisk". Any more help you could give would be great!! ](*,)

---

### Post by gborzi on 2006-09-02
I have tried on my system
> gnome-terminal -x sudo pppstatus and > gnome-terminal -e "sudo pppstatus"
both of them works, i.e. a gnome-terminal is opened with the
> Passwd: prompt. After giving the password, it starts pppstatus. Try
> gnome-terminal -x sudo testdisk

---

