---
title: "Help me please with connecting to the internet"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by tim.buktu on 2006-02-18
Hi there,

i've just installed the latest version of Ubuntu but connecting to the internet with ADSL seems to be the biggest problem now.
i used Windows and know how to set up a new internet connection with the 'connection wizzard' but here with Ubuntu i don't know what to do. 
Could you please help me what to do?

Thank you in advance

regards

---

### Post by chimera on 2006-02-18
open terminal (applications->accesories->terminal)

type

```

sudo pppoeconf

```

You will be prompted for a password, enter the one you logged in with.

After that, keep selecting Yes all the time, and when prompted, enter your ADSL username and password.

---

### Post by jjf on 2006-02-18
(what he said)

---

### Post by tim.buktu on 2006-02-18
:D :D :D :D :D 
It works! Thank you very much!!!!!!!

---

### Post by tim.buktu on 2006-02-18
Hm, yes, it worked but after deactivating the connection i was not able to connect again unless i went through the process you wrote me.
I don't want to bother anyone but could you please help me how to restore the connection in an easier way?

Thank you in advance

regards

---

### Post by chimera on 2006-02-18
to connect, open the terminal and enter

```

pon dsl-provider

```

to disconnect,

```

poff

```

However, you don't need to manually connect when you boot your computer, because if you selected yes all the time, it should auto-connect at boot.

---

### Post by tim.buktu on 2006-02-19
thank you, it works!

best regards
tim.buktu

[QUOTE=chimera]to connect, open the terminal and enter

```

pon dsl-provider

```

to disconnect,

```

poff

```

However, you don't need to manually connect when you boot your computer, because if you selected yes all the time, it should auto-connect at boot.[/QUOTE]

---

### Post by chimera on 2006-02-19
Just curious, how did you deactivate the connection without knowing the poff command?

---

### Post by ChocoPanda on 2006-02-20
help! im a complete newbie & idiot to linux systems!:p 

i used to connect to the net via a router... and i'd just enter the gateway ip and that's all... but now i can't seem to connect to the internet, even after i'd entered all the networking settings under systems>admin>network.

and when i try to use the steps from above, the terminal thingy told me to be 'root' first... what does that mean?

ah im using ubuntu5.10

anyone with any ideas please mail me [email]king_of_panda@hotmail.com[/email] thanks

---

### Post by stalefries on 2006-02-20
The "root" user has all the power. He is king! Therefore, if you or a program you are running need to access a certain file that is owned by root, you must become root first. In Ubuntu, you would need to type "sudo <command>" instead of just "<command>".

---

### Post by ChocoPanda on 2006-02-20
ahhhh i see i see.. thanks for your guidance...:p

---

