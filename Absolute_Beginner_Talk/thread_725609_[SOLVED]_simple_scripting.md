---
title: "[SOLVED] simple scripting"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by sammydadams on 2008-03-15
This is a simple scripting question

i'm a total noob at scripting, but the simple fact is that i dont really want to learn it (at least yet) but here's the rub

I have VirtualBox and i run windoze seamlessly through it, but i like beryl and so i'd only like to disable beryl when i run the virtual machine...

specifically i'd like it to essentially run:

```
metcity --replace
```
and then run virtualbox...it'd be awesome if it'd start the virtual machine too, but i'm not too picky about that...

i was messing around with stuff and wrote:
```
metacity --replace;
virtualbox
```

and oddly enough this works...sorta...
in short it seems to have to be run twice, the first time it switches to metacity and the second time i run it it starts up virtualbox...

any help would be much appreciated!

Thank you

---

### Post by unutbu on 2008-03-15
```

#!/bin/sh
metacity --replace & 
virtualbox

```

---

### Post by sammydadams on 2008-03-16
Thank you very much for a quick reply, it works perfectly
i know you guys probably hate to be hassled by these noob questions....there wouldn't happen to be any way for me to actually run the virtual machine through the script, would there?...i'd imagine not, but it's worth asking, right?
:D

---

### Post by banewman on 2008-03-16
See if this will do the trick
```
#!/bin/sh
metacity --replace & 
sleep 5
virtualbox
```
:)

---

### Post by sammydadams on 2008-03-16
it still starts up virtualbox, but it seems to just be slower...why doesnt virtualbox have a setting like vmware that starts up one of your machines once the program is started?...oh well thanks everyone...one other thing tho...i have a seagate drive that requires me to restart HAL when i plug it in...i'd like to hide a script in the nautilus menu to do just that...i tried something along the lines of:
```
#!/bin/bash

# Restarts Abstraction Layer

foo=`gksudo -u root -k -m "enter your root password to restart the Hardware Abstraction Layer" /etc/init.d "got r00t?"`
sudo hal restart 
```
but it doesnt seem to do anything other than ask me for the password
the idea is to essentially run
```
sudo /etc/init.d/hal restart
```
but to ask me for my root password in a popup....once again, any help would be much appreciated...it might be a good time to start learning a little bit of bash scripting myself 
:roll:

---

### Post by timbounceback on 2008-03-16
```
gksudo /etc/init.d/hal restart
```

---

### Post by sammydadams on 2008-03-16
Thanks Timbounceback...that was super i actually didnt really know the difference between "sudo" and "gksudo" before...ok one last thing, i promise! i found out how to start the VM by using:
```
vboxmanagege startvm WinXP

```
where WinXP is the name of the machine...the last thing is that it starts up in a window and i was hoping for a way to start it up minimized if possible...i know it isnt that big of a deal to simply minimize once it is up and running, but i'm loving the power of bash scripting, so i'd love for it to start minimized (the seamless start menu shows up with the VM minimized, but i dont have to watch the startup junk...i just see the start menu if it is minimized)...so so far i have (thanks to you guys)
```
#!/bin/sh
metacity --replace & 
vboxmanage startvm WinXP

```
so in short i'd like to have this minimize once it is started if possible...

thanks again for your patience and knowledge!

---

### Post by unutbu on 2008-03-16
It looks like this is a requested feature:
[http://www.virtualbox.org/ticket/851](http://www.virtualbox.org/ticket/851)

---

### Post by sammydadams on 2008-03-17
i was looking through some things and was thinking about trying something along the lines of wmctrl or devilspie...these seem to work for others, so i'm going to give it a shot so maybe i can just get the script i will ultimately use up here and maybe it'll work for others as well..i just need to learn to minimize using one of these two tools

---

### Post by Xiong Chiamiov on 2008-03-17
As far as bash scripting goes, I learned a bit from [these]("http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html") [two]("http://www.tldp.org/LDP/abs/html/index.html") pages.

---

### Post by sammydadams on 2008-03-17
ok...it looks like it would have to be done through devilspie, but i cant seem to get the .ds script right....i have tried everything i can think of!...the syntax seems to be:
```
(if
(contains (window_name) "virtualbox")
(minimize)
)
```

but this doesnt seem to work...

---

### Post by sammydadams on 2008-03-17
ok...i figured it out...so here's what i got, so i can call this one "solved"

i got a script that looks like this:

```
#!/bin/sh
metacity --replace &
vboxmanage startvm WinXP &
sleep 5
devilspie -a

```

and a virtualbox.ds in ~/.devilspie that looks like this:

```
(if 
     (contains (window_name) "WinXP") 
          (begin(minimize)
     )
)

```

the name of my VM is WinXP so this exists in the title...what i didnt realize is that all i had to really do is either add -a to the devilspie command or move it up because it only acts on newly opened windows otherwise...

it doesnt exactly do the same thing i want, but i think i'm going to try to maximize it after more time...add another devilspie .ds file whichi maximizes it after some time, but that is for another day...thanks to everyone who hepled me out with this and i hope this helps someone else!

---

### Post by unutbu on 2008-03-17
Great job! Congratulations!

---

