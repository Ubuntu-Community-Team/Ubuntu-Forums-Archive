---
title: "chmod problem"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by chacham23 on 2007-07-30
I did this command at my /home library:

su
chmod -R u=x assaf

now I cant log to the user assaf(is my user!!!).

so what can I do? is there is anyway to reverse it????? please I dont want to install ubuntu again :(

thanks....

---

### Post by diatribe on 2007-07-30
what exactly were you trying to do?  it seems you changed your /home directory to executable

---

### Post by chacham23 on 2007-07-30
I was trying to install some update for azures and it said that he didnt have permissions...

so I want to have the all folder permission...:confused::confused:

I know it little stupid!

---

### Post by deadgobby on 2007-07-30
For one do not use (su) for root priv it is sudu with Ubie
Thus the command line should look like this

sudo chmod -R u=x assaf

See if that works

Gobby

---

### Post by chacham23 on 2007-07-30
> **deadgobby said:**
> For one do not use (su) for root priv it is sudu with Ubie
Thus the command line should look like this

sudo chmod -R u=x assaf

See if that works

Gobby

but I did that and it made all the trouble.  to do it again?????

---

### Post by diatribe on 2007-07-30
> **deadgobby said:**
> For one do not use (su) for root priv it is sudu with Ubie
Thus the command line should look like this

sudo chmod -R u=x assaf

See if that works

Gobby

I doubt this will work.  sudo is just another method of gaining root access, if he executed the same command while logged in as root it won't matter.  Anyway,  what is displayed when you try to login?

---

### Post by chacham23 on 2007-07-30
```

your session only lasted less than 10 seconds......

```
```

.: 107: cant open /home/assaf/.profile

```

I think I need to chmod again... but how??????????????

---

### Post by diatribe on 2007-07-30
well seeing as you used chmod with the -R flag, it did the **** recursively; its worth trying but I think that you may have ****** up this time.  try chmod +rw /home/assaf/.profile and see if it helps

---

### Post by chacham23 on 2007-07-30
ok now it tell me something about the gnome it cant do...

I think I should do it with -R on all the folder... what do u think?

---

### Post by diatribe on 2007-07-30
I mean, you cant break it anymore than it already is

---

### Post by chacham23 on 2007-07-30
hope it will help :)

---

### Post by chacham23 on 2007-07-30
> **diatribe said:**
> I mean, you cant break it anymore than it already is

m8 U my HERO!!!!!!!!!!!!!!

thanks alot!!!:guitar:

---

### Post by asmoore82 on 2007-07-30
i've never seen the '=' form of the chmod command before today and don't recommend using it ;)

```
~ $ sudo chmod -R u+rw .
```

should give you read/write permission back to all of your files.

BUT you still have some major cleanup to do; i.e. that first command you did set the executable bit on all regular files.
directories need to be 'rwx' but files just 'rw'

---

