---
title: "Shell Script needed to start 'Listen'"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by mysticmatrix on 2007-08-17
I have found a great music jukebox 'Listen'(Found under Add/Remove...).([http://www.listen-project.org/](http://www.listen-project.org/))

I have really liked its interface and music library management. But the only problem with it is that it doesn't recognize the network proxy setting done in Gnome under System --> Preferences --> Network Proxy. I can get around this by starting program by command 'listen' from terminal after setting variable $http_proxy.

Now I guess this entire stuff can be done by a shell script which I can then double click to execute. Can anyone help me in this?

---

### Post by jdfreshwater on 2007-08-17
open a text file and start out with the first line of 

#!/bin/sh

(type your commands here)

After that you should make sure that it is executable.  This should work.

---

### Post by Bachstelze on 2007-08-17
Put this in your ~/.bashrc :

```
export http_proxy="http://host:port"
```

then logout and log back in, it should do the trick.

---

### Post by mysticmatrix on 2007-08-17
Oh perhaps I didn't put question in correct way. I don't know bash script and am a little lazy to learn. Can any one do it for me?
Also .bashrc trick would still require me to open a terminal everytime and type' listen'. 
What I was asking is that can I create a launcher that can be simply doube clicked to start 'listen' and allow me to use proxy?

---

### Post by Bachstelze on 2007-08-17
> **mysticmatrix said:**
> 
Also .bashrc trick would still require me to open a terminal everytime and type' listen'. 


You admit you know nothing about Bash. So how can you tell what this "would" do before you try it ? I think I know what I'm saying but if you don't want to listen to advice, why bother to ask ?

---

### Post by mysticmatrix on 2007-08-18
Sorry if I appear to be rude, but I have tried that .bashrc trick before also and it didn't worked. Moreover, when one sets Gnome network settings, Gnome automatically declares http_proxy variable in BASH.

I have now again tried the .bashrc stuff, and still listen doesn't works.

By what I meant that I don't know bash is that I am familiar enough with terminal to do basic navigation, understanding system variables and such stuff, but don't know how to do scripting in bash.

---

### Post by nichipet on 2007-08-18
Have you tried jdfreshwater's suggestion yet? That would work, as well.

---

### Post by walkerk on 2007-08-18
> **jdfreshwater said:**
> open a text file and start out with the first line of 

#!/bin/sh

(type your commands here)

After that you should make sure that it is executable.  This should work.

create a shell:
```
gedit ~/.listen.sh
```

enter the following and save:
```
#!/bin/bash
your_command_you_run_in_terminal
```

make it executable:
```
chmod +x ~/.listen.sh
```


now right click desktop > create a launcher .. now enter the name and command

Name: Listen
Command: ~/.listen.sh

That'll do it.

---

### Post by hyper_ch on 2007-08-18
> **mysticmatrix said:**
> and am a little lazy to learn.

So others should do all the work for you?

---

### Post by mysticmatrix on 2007-08-18
Thank you for helping but the various solution are not working(Damn my proxy!!!!)

I have tried that of walkerk, jdfreshwater and all other who helped.
Guess I would have to open a terminal everytime I want to listen music:(

---

