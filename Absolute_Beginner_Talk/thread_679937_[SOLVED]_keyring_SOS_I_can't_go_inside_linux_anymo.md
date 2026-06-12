---
title: "[SOLVED] keyring SOS I can't go inside linux anymore"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by antonio_ing on 2008-01-27
Hi everybody

I was looking about how to change the keyring and i found some suggestion about installing libpam-keyring enter package with the terminal. I followed the instructions. But when I have restarted the laptop i couldn't go inside linux anymore because there is the window "Authentication failed" continuously. Does someone have the cure?

---

### Post by llamakc on 2008-01-27
What do you mean by "go inside linux"? Be specific please.

---

### Post by antonio_ing on 2008-01-27
that now i cannot boot anymore :-)

---

### Post by antonio_ing on 2008-01-27
Should I reset all the settings of the network manager? I'm in panic :confused:

---

### Post by llamakc on 2008-01-27
> **antonio_ing said:**
> that now i cannot boot anymore :-)

Are you confusing "boot" with "login"? Sounds like it.

---

### Post by antonio_ing on 2008-01-27
you're right. it's login. Any idea?

---

### Post by llamakc on 2008-01-27
> **antonio_ing said:**
> you're right. it's login. Any idea?

Yes.

Press the key-combo CTRL-ALT-F2.

Now login as your username. You'll be logged into the system on a console. There will be NO graphics or buttons to click.

Type:

```

sudo apt-get remove libpam-gnome-keyring

```

and enter YOUR password.

Next type:

```

sudo /etc/init.d/gdm restart

```

And login.

You can not commit typos on the command line while in the console, so be precise.

---

### Post by antonio_ing on 2008-01-27
ok now it´s working again

by means of the command line i have removed the pamkeyring and also delete the last line from /etc/pam.d/gdm that was 

@include common-pamkeyring

thank you very much

---

### Post by llamakc on 2008-01-27
Cool. Don't forget to mark your post 'SOLVED'.

---

### Post by antonio_ing on 2008-01-27
Solved

---

