---
title: "Getting ROOT privilage"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by quarkhirad on 2007-10-06
Hello 

I was helping a friend set up his ubuntu to install pakages . Hence i decided to apt-get . To do so i need to be root. Hence i typed sudo su in the terminal and i got 

Sudo: must be setuid root

and thus i cannot get into root. 

HELP :confused: HELP :confused: HELP HELP :confused:

khirad

---

### Post by overdrank on 2007-10-06
> **quarkhirad said:**
> Hello 

I was helping a friend set up his ubuntu to install pakages . Hence i decided to apt-get . To do so i need to be root. Hence i typed sudo su in the terminal and i got 

Sudo: must be setuid root

and thus i cannot get into root. 

HELP :confused: HELP :confused: HELP HELP :confused:

khirad

Hi I believe all you need is ```
sudo
``` as in ```
sudo apt-get install " the package" 
```

---

### Post by Pumalite on 2007-10-06
What about:

sudo -i

---

### Post by quarkhirad on 2007-10-06
Dear overdrank
Thanks but when i typed sudo apt-get update (this to first update the database before selecting the package) i still get the same reply 

Sudo : must be setuid root 

Oh and pumalite 
sudo -i 

also gives the same error . 

Help :confused:

---

### Post by taurus on 2007-10-06
Here is more info about sudo, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

---

### Post by taurus on 2007-10-06
> **quarkhirad said:**
> Dear overdrank
Thanks but when i typed sudo apt-get update (this to first update the database before selecting the package) i still get the same reply 

Sudo : must be setuid root 

Oh and pumalite 
sudo -i 

also gives the same error . 

Help :confused:

Did you log in as the first user that you created during the installing process?  What's the output of this command from a terminal?

```
id
```

---

### Post by quarkhirad on 2007-10-06
Taurus

Thanks for the link but i dont have time to go through it. 

Did you log in as the first user that you created during the installing process?

Yes i did

My user id is rahul.
Network name is rahul-laptop 


output to code id 

rahul@rahul-laptop:~$ id

uid=1000(rahul) gid=1000(rahul) groups=4(adm) ,20(dialout) ,24(cdrom) ,25(floppy) ,29(audio) ,30(dip) ,44(video) ,46(plugdev) ,106(lpadmin) ,110(scanner) ,112(admin) ,1000(rahul)

rahul@rahul-laptop:~$

---

### Post by steve.horsley on 2007-10-06
It looks as though the sudo binary has the wrong permissions flags. This is what I get when I look at mine:
```
steve@StevesPC:~$ ls -l /usr/bin/sudo
-rwsr-xr-x 2 root root 91508 2006-10-09 12:37 /usr/bin/sudo

```

Notice the permissions at the start. The 's' is the setuid property. If your firend's isn't like that then there is something badly wrong. It can be fixed by booting into rescue mode (which gives you a root prompt) and using the command:
```
chmod 4755 /usr/bin/sudo
```
But I worry about how this happened and what else is messed up. I wonder if a re-installation might be better.

---

### Post by taurus on 2007-10-06
When you run this command from a terminal,

```
sudo apt-get update
```
make sure you use the same password that you're logging in with.  And when you type it in from a terminal, you won't see it echo on the screen so make sure you type it right.

---

### Post by quarkhirad on 2007-10-06
Dear taurus 

Nope thats not it . I am aware of the password being the same. Anyways thanks for the information.

Dear  steve.horsley

Your on target bingo man :guitar::guitar::guitar::guitar:

heres what i got 

-rwxr-xr-x 1 rahul root 93844 2006-05-17 14:11 /usr/bin/sudo

Man thanks..  :):):):)

Hey anybody can you answer this part 


But I worry about how this happened and what else is messed up. I wonder if a re-installation might be better.

???????

---

### Post by taurus on 2007-10-06
> **quarkhirad said:**
> 
heres what i got 

-rwxr-xr-x 1 **[COLOR="Blue"]rahul[/COLOR]** root 93844 2006-05-17 14:11 /usr/bin/sudo


You should not be monkeying around with file permission or ownership if you don't know what you are doing.

---

