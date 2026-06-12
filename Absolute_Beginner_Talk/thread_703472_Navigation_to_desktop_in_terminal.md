---
title: "Navigation to desktop in terminal"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by universalis13 on 2008-02-21
I

---

### Post by universalis13 on 2008-02-21
Sorry, hit wrong key

here's the question. installing flash, need to input commands to navigate to desktop?

---

### Post by northern lights on 2008-02-21
```
cd /home/<user>/Desktop
```
where <user> needs to be replaced by your username

> **universalis13 said:**
> Sorry, hit wrong key
..you can edit your posts, btw...
(button on the bottom right of your own posts)

---

### Post by universalis13 on 2008-02-21
Thanks

---

### Post by northern lights on 2008-02-21
No problem - just got one quick question:

How is navigation to the desktop neccessary to install flash?
I assume you downloaded some package or tarball?
Simply run
```
sudo apt-get install flashplugin-nonfree
```
and delete what's on your desktop - this is definitely easier than whatever it is you wanna do

---

### Post by universalis13 on 2008-02-21
Well I guess this is not solved, jumped the gun a bit.

typed in: cd  /home/<user>/desktop
and got: no such file dirctory

any ideas?

Oh, new to forums.

I just installed ubuntu and went to youtube and was directed there on 3 ways to install flash.

---

### Post by jan quark on 2008-02-21
you have to replace

```
cd /home/<user>/desktop
```

<user> with your username

so for instance
```

cd /home/bob/desktop
```

---

### Post by lswest on 2008-02-21
also it's **D**esktop  (linux is case-sensitive)

---

### Post by jan quark on 2008-02-21
good catch 

thank you

---

### Post by northern lights on 2008-02-21
> **northern lights said:**
> 
where <user> needs to be replaced by your username

Your username is what you type in the login screen before the password...

Suppose my username was "northern" - then the comman would read```
cd /home/northern/Desktop
```
--> Got it?

[EDIT]Take your time typing and someone's always quicker...[/EDIT]

---

### Post by universalis13 on 2008-02-21
Got the user name right, it was the case sensitive on Desktop that got me.

Thanks, ill work on this - have some trouble with Adobe instrutions.

Tried to run sudo and got error. I forgot to remove flash installer app, so this might be the problem. Before I delete I want to try to solve Adobe intall.

---

### Post by universalis13 on 2008-02-21
This is funny. I didn't have any luck with all this command line stuff, but went back to youtube see wether I had flash installed and it wasn't. Then I noticed the yellow bar and just installed from there. No muss no fuss.

Thanks though for the introduction to terminal commands.

LSWest I'm working on emailing you. I'm using gmail and am not quite sure how to do it.

---

### Post by jan quark on 2008-02-21
:lolflag:

the easy path worked

---

### Post by universalis13 on 2008-02-21
Yes, this is true. But none the less I have to ween myself from my GUI limitations.

---

### Post by lswest on 2008-02-22
you're trying to email me?  there's a link in my sig, or you can email me from my profile on here, both work^^
the link should open a thunderbird or evolution send mail window, with my email address in the "to" section, in any case the email is: [email]quantum_haxx@yahoo.ca[/email]

---

