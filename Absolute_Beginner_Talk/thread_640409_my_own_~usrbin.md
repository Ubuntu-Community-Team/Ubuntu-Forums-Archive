---
title: "my own ~/usr/bin"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by miko3k on 2007-12-14
i would like have my own ~/usr/bin directory where I could install stuff compiled from source, etc... so far so good.

I would like to run programs from there using alt+f2. I tried to modify my ~/.bashrc to include ~/usr/bin im $PATH, but it gets executed only if I open a terminal, not after login. 

Any suggestions?

---

### Post by cmnorton on 2007-12-14
.profile is already set up for you to have a ~/bin. If you don't have a bin directory, create one, and put your stuff in there. This seems to be a common way to do things across distros, as well.

---

### Post by miko3k on 2007-12-14
I tried to symlink ~/bin to ~/usr/bin to and it does not work.

Again it *works* when I open a terminal and type command. I just want to run stuff without opening terminal (alt+f2 as i noted in my first post)

---

### Post by frodon on 2007-12-14
Just add the path of your personnal bin to the $PATH variable. To do this you, in general, add a line in your .bashrc file like that :
```
export PATH=$PATH:/home/user/mybin
```Replace /home/user/mybin by your personal bin path then each time you will open a terminal all the scripts in your personal bin will be known as terminal commands.

---

### Post by miko3k on 2007-12-14
Thanks for reply. But unfortunately according to my little research ~/.bashrc gets executed only when I open a terminal, not after login to system.

---

### Post by frodon on 2007-12-14
This is exact.

Once executed are you able to see your apps using Alt +F2 ? i'm scared you won't.

---

### Post by miko3k on 2007-12-14
alf+f2 that was just an example (alhough it's my primary reason for this). Same example as creating a launcher without path... or whatever. $PATH just has to be modified after login time not after I open the terminal as ~/.bashrc does. Is it even possible ? :-) Is there a script executed right after I login?

---

### Post by frodon on 2007-12-14
Sure it is possible however i'm not sure it will do what you expect.

Create a script in init.d  :
```
sudo gedit /etc/init.d/path_update
```and put your export $PATH command in :
```
#!/bin/bash
export PATH=$PATH:/home/user/mybin

```
Make it executable then make it run on boot (before GDM) thanks to the following command :
```
sudo update-rc.d path_update defaults
```

---

### Post by miko3k on 2007-12-14
I want to keep it user specific. It has to launched after login (probaby by gdm or something). I tried to create simple script like this 
```

#!/bin/sh
export FOOBAR=foo
```

and exectue it via system/adminstration(?)/sessions (sorry about names, I'm not using english locale). It does not seem to have effect (because it's run in subshell or something).

I just want to do something like this. But working :-)

---

### Post by psusi on 2007-12-14
> **frodon said:**
> Sure it is possible however i'm not sure it will do what you expect.

Create a script in init.d  :
```
sudo gedit /etc/init.d/path_update
```and put your export $PATH command in :
```
#!/bin/bash
export PATH=$PATH:/home/user/mybin

```
Make it executable then make it run on boot (before GDM) thanks to the following command :
```
sudo update-rc.d path_update defaults
```

That won't even work... the init scripts are run as root by init... when you login, you get your own environment.

OP: Just place the directives in .profile, not .bashrc, which is only used by bash.

---

