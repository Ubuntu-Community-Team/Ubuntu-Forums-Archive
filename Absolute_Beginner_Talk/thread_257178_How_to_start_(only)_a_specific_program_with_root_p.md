---
title: "How to start (only) a specific program with root privileges?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Claudiu on 2006-09-14
Hi folks!

I'm repeting the question from the title (which is pretty obvious - nothing more to say):

How to start (only) a specific program with root privileges (and no password)?

Thank you!

---

### Post by Jussi Kukkonen on 2006-09-14
Well, actually I'm not 100% sure what you mean, but... 
```
sudo app
```
runs *app* with root privileges in command line if your user is allowed to run sudo...

---

### Post by Claudiu on 2006-09-14
Ah! Sorry! I've forgot one thing: I know sudo, gksudo kdesu.... but I dont't want to type anytime my password.

I want to run a program (Wireless Assistant) by clicking its icon on my panel (Yeah, I've managed to get wifi working) ... AND I don't want to be asked for my password anytime I run it.

---

### Post by Najand on 2006-09-14
Hmm, it is possible. Do you know the command you want to execute and the place where it is located?

---

### Post by Claudiu on 2006-09-14
It's a button on my KDE Panel.

The command is "wlassistant" (as I see in properties)

---

### Post by Jussi Kukkonen on 2006-09-14
I kind of guessed that there was an additional catch :)

I'm not sure if this works, but it's worth a try: Find out what executable the panel button launches (maybe with *ps aux* while it's running), then try adding a line like this to /etc/sudoers:
```
username ALL = NOPASSWD: /path/to/executable
```
where the username is the user the process was running as...
*EDIT: that would be your username as it's a normal panel launcher*

---

### Post by Claudiu on 2006-09-14
I've tried with
```
myusername ALL = NOPASSWD: /usr/bin/wlassistant
```

and still it ask my password :(

---

### Post by Najand on 2006-09-14
Use locate command to locate "wlassistant".
Run```
 sudo su 
```
Change permission for /etc/sudoers to able writing to it:
```

chmod u+w /etc/sudoers

```
 edit your /etc/sudoers:
```

%admin ALL=(root) NOPASSWD: /usr/bin/wlassistant

```
Change /usr/bin/wlassistant with the location and name of your application.
Save it. 
Change permission back to readonly.
```

chmod u-w /usr/sudoers
exit

```
and you are done.

---

### Post by Jussi Kukkonen on 2006-09-14
Hmm.. I wonder if I remembered the sudoers format right. Can you run 
```
sudo -k
sudo /usr/bin/wlassistant
```
in the command line to see if it works there?

---

### Post by Claudiu on 2006-09-14
I tryed your code:
```
sudo -k
sudo wlassistant
```

which results to:
```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

wlassistant: cannot connect to X server :0.0
```

and then I've tryed simply
```
wlassistant
```

and the program starts, announce that I didn't start it with superuser rights.. and let me see the networks, etc. But that behaviour is program specific. I want to learn how to start only one program as superuser and without password, so next time I want that for another program to make the same steps. I feel like the /etc/sudoers aproach is correct, but maybe the sintax is wrong?

I'll try also Najand's advices.



> **Jussi Kukkonen said:**
> Hmm.. I wonder if I remembered the sudoers format right. Can you run 
```
sudo -k
sudo /usr/bin/wlassistant
```
in the command line to see if it works there?

---

### Post by Claudiu on 2006-09-14
> **Najand said:**
> Use locate command to locate "wlassistant".
Run```
 sudo su 
```
Change permission for /etc/sudoers to able writing to it:
```

chmod u+w /etc/sudoers

```
 edit your /etc/sudoers:
```

%admin ALL=(root) NOPASSWD: /usr/bin/wlassistant

```
Change /usr/bin/wlassistant with the location and name of your application.
Save it. 
Change permission back to readonly.
```

chmod u-w /usr/sudoers
exit

```
and you are done.

I've tried your advice:

First I've modified /etc/sudoers by entering the following command (found in [www.ubuntuguide.org):](www.ubuntuguide.org):)
```
EDITOR=gedit sudo visudo
```

which realy works.

Ok, then...

Press on the button. Same behaviour - asks for password.

Do I need a reboot? I don't think so, but better I ask.

---

### Post by Najand on 2006-09-14
It just worth a try if you care? Doesn't it?

---

### Post by Claudiu on 2006-09-14
> **Najand said:**
> It just worth a try if you care? Doesn't it?

It didn't work.

Anyway, I will try another time. RIght now I feel what I wanted is not so usefull. Although....

Thank you guys for trying to help.

---

