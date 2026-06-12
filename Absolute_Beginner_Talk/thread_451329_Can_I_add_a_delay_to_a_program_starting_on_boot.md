---
title: "Can I add a delay to a program starting on boot?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-22
Everytime I boot, I have Evolution start as well.  But since my wireless is still authenticating, I always get an error from Evolution that it can't grab the mail.  Is there a command or something I can add to make Evolution boot 15 seconds after startup?

---

### Post by dannyboy79 on 2007-05-22
hwo are you starting Evolution, with init.d script or did you add it to your session dialog box? Maybe you want to move your wireless activation up in the init script order? I am not sure at the moment what number networking is within the init.d folder. If you added Evolution to your session dialog box, the has to be a way to add a timer effect in front of the command, like

after amountoftimeinmilliseconds evolution
(Example specifically: after 20000 evolution)

and that will start Evolution .33 seconds after the command within session are called upon to start. Now unfortunately I have no idea exatly when all those command are called upon as the boot process as always been a bit of a mistery to me. good luck

---

### Post by gohanssjn on 2007-05-22
Ok, thanks.

I added it to the session, so I will try the later.

---

### Post by gohanssjn on 2007-05-22
Oh, and on the same note, is there a command to start certain programs on certain workspaces?

---

### Post by dannyboy79 on 2007-05-22
not sure about the certain programs on certain workspaces but I would imagine so, you just have to gogle it. ALso, I had asked you how Evolutiin was currently starting before you did anything and you didn't answer. If it was starting from init and now you added a session startup program, you may get 2 evo's after you boot up. Hence why I asked you how Evo was being started to begin with.

---

### Post by gohanssjn on 2007-05-22
Ah, I misunderstood.

Evo. wasn't starting before, I opened it each time I booted Ubuntu, and I never had it save sessions.  This is the first time it's really been starting on boot.

---

### Post by argie on 2007-05-22
You will need to use devilspie to start programs on only certain workspaces if you're using Gnome. First install devilspie, type in the terminal:
```
sudo aptitude install devilspie
```
Then create a .devilspie folder in your home folder and enter it, in the terminal , one after the other:
```
cd
mkdir .devilspie
cd .devilspie
```

Now make a rule to move evolution to the fourth workspace. In the terminal, type:
```

gedit evolution.ds

```

And in the text editor, copy paste:

```
(if
        (matches (application_name) "evolution")
        (begin
                (set_workspace 4)
        )
)

```

Now save the file, and run devilspie, then evolution. It should move to the fourth desktop, irrespective of which desktop you start it on. If you want this to happen every time you start, put devilspie in your sessions *before* evolution.

---

### Post by gohanssjn on 2007-05-22
You all rock :D

I'll try this tonight wehn I get home :D

---

### Post by gohanssjn on 2007-05-22
Ok, for some reason, I can't find how to make a script for any of the OpenOffice applications with application_name.  Any ideas?

---

### Post by dannyboy79 on 2007-05-23
i would suggest starting a new thread.

---

