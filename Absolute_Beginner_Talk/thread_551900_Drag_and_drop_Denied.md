---
title: "Drag and drop Denied"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Uren2 on 2007-09-15
I'm using Feisty Fawn and it won't let me drag and drop files into /usr/local/<the destination directory>. I'm using the first user account I created after installation.  How can I get the necessary access to drag and drop?

---

### Post by saj0577 on 2007-09-15
You have to make your account have sudo (full admin) permissions im not sure ho to do this in a GUI but if your just moving files every so often i would recommend doing this in terminal.

Saj

---

### Post by Uren2 on 2007-09-15
Thanks saj.  I've been trying to use the command line, but given my lack of experience it isn't working out.

---

### Post by saj0577 on 2007-09-15
Im currently developing a guide with basic things like this in it.
I think the code you need is:

```

sudo mv /home/saj/Desktop/folder/ /home/saj/



```


/home/saj/Desktop/folder/ being the folder that i am moving 
/home/saj/ being the place to move it to


Hope it helps
Saj

---

### Post by Metacarpal on 2007-09-15
Hit alt-f2 (this will give you a prompt to run a command) - enter:
```
gksudo nautilus
```

That'll give you a file manager window in which you will have write permissions to /usr/local or just about anywhere you'd care to drop a file.

You should be careful that you don't overwrite an existing file that way, however, unless you're sure you know what you're doing.

What are you looking to put there?

---

### Post by Uren2 on 2007-09-15
I'm trying to install mozilla seamonkey.  Thanks for those suggestions, I finally got it working.  Can you guys recommend a method to be able to launch seamonkey from the Applications menu instead of having to go into the terminal?

---

### Post by por100pre1 on 2007-09-15
```
alacarte
```

and then create a launcher for SeaMonkey. The command should be:

```
seamonkey
```

---

### Post by st33med on 2007-09-15
Two things to warn you about: you're a root user while in root nautilus. Also, I haven't confirmed this yet, but I think if you leave open for a while, it while wakeup the processor a whole bunch, meaning its taxing on power and electricity.

---

### Post by Dr Small on 2007-09-15
Why would it do that ?

---

### Post by st33med on 2007-09-15
Have no idea. Powertop told me it was waking up more than 800 per second.

---

