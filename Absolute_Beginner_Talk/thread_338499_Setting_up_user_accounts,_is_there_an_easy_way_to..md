---
title: "Setting up user accounts, is there an easy way to..."
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-01-14
I have Ubuntu on my computer already, and I am now in the process of installing it on the family computer. There will have to be at least two different accounts, so I'm going to have to set up users.

The problem is that when I make a new user, and log in as that user, all of the configuration I had done (like menu delays, background, conky, top icons) is not done for the new user. Short of doing all this again, is there an easy way to bring my configuration files over to a new user account?

Also, will the programs that I installed work for a new user account? When I installed things like google earth, it put stuff in my home directory, will this work on a different account?

-Andrew

---

### Post by taurus on 2007-01-14
1.  Just copy all your stuff in your own $HOME directory to the new user with the sudo command.  Let's assuming your username is **atreus** and the new username is **john**.  Do

```
sudo cp -R /home/atreus  /home/john
sudo chown -R john:john /home/john
```

2.  If that program is in the path, john should be able to run it from your $HOME.

---

### Post by Atreus12 on 2007-01-15
Is there a way to move all the setting over to the new account? Such as background, startup programs etc?

---

### Post by Arisna on 2007-01-15
All of your config is stored in hidden files in your home directory.  They are files and directories that begin with the "." character.  They should get pulled in when you copy all the other files over.

You can view these files by opening Nautlilus and hitting Ctrl-H.  Hitting Ctrl-H again will re-hide them.

---

### Post by taurus on 2007-01-15
> **Atreus12 said:**
> Is there a way to move all the setting over to the new account? Such as background, startup programs etc?

```

sudo cp -R /home/atreus/*  /home/john
sudo chown -R john:john /home/john

```

---

