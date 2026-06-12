---
title: "Help please Updates have broken kubuntu"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by The303 on 2007-06-07
Hi I've been using kubuntu 6.06 for about 6 months now and so far all has been fine

My internet connection has been down for about 3 months and when it was finally reconnected this morning a small icon on my taskbar reported that 48 updates were available for me to download

I downloaded them and they installed fine all the way up to 100%

Everything was working fine until I rebooted the computer

Now I can no longer login

I enter my username and password at the login screen 

the screen then turns black for around 10 seconds with the mouse cursor still active and visible

it then returns me to the login screen again

this is so frustrating as this is the only pc I have at the moment

I found an old ubuntu 6.06 live cd which has enabled me to at least be able to post for some help or advice here

---

### Post by viciouslime on 2007-06-07
> **The303 said:**
> Hi I've been using kubuntu 6.06 for about 6 months now and so far all has been fine

My internet connection has been down for about 3 months and when it was finally reconnected this morning a small icon on my taskbar reported that 48 updates were available for me to download

I downloaded them and they installed fine all the way up to 100%

Everything was working fine until I rebooted the computer

Now I can no longer login

I enter my username and password at the login screen 

the screen then turns black for around 10 seconds with the mouse cursor still active and visible

it then returns me to the login screen again

this is so frustrating as this is the only pc I have at the moment

I found an old ubuntu 6.06 live cd which has enabled me to at least be able to post for some help or advice here

Are you using beryl/compiz?

---

### Post by PatrickMay16 on 2007-06-07
At the login screen, are there different options for different session types? when you login, try selecting some different kind of session. You might be able to get some use of the computer like that. 

BTW, what happens if you press ctrl + alt + f1 and try logging in there? Does it work?

---

### Post by The303 on 2007-06-07
> **viciouslime said:**
> Are you using beryl/compiz?

no just a regular kde desktop

---

### Post by The303 on 2007-06-07
> **PatrickMay16 said:**
> At the login screen, are there different options for different session types? when you login, try selecting some different kind of session. You might be able to get some use of the computer like that. 

I tried all the different options and the only one that made any difference was logging in vias console, but I was more than a little lost from that point

> **PatrickMay16 said:**
> BTW, what happens if you press ctrl + alt + f1 and try logging in there? Does it work?

I will reboot and try that

---

### Post by PatrickMay16 on 2007-06-07
I see. Try using the 'failsafe terminal' (or whatever it's called) option from the login screen, and then once logged in, try this command:

```

startkde

```

Let me know if anything happens.

---

### Post by The303 on 2007-06-07
> **PatrickMay16 said:**
> I see. Try using the 'failsafe terminal' (or whatever it's called) option from the login screen, and then once logged in, try this command:

```

startkde

```

Let me know if anything happens.

Ok thanks I tried that and it told me that it could not start kde because there is no free space in my home directory

---

### Post by PatrickMay16 on 2007-06-07
Ah HA! I see! You have no free space in your home directory, so KDE cannot start. Do the failsafe terminal thing again, but instead of 'startkde', type 'konqueror', and you'll get the file manager open (I hope) just enough for you to go and delete some stuff, so kde can work again. If konqueror won't work because of the lack of free space, you'll need to use the command line to delete stuff... I can help you with that if you need it.

---

### Post by The303 on 2007-06-07
you are an absolute star :KS

thankyou very much I'll let you know how I get on

---

### Post by The303 on 2007-06-07
no luck with konquerer, 

I just get the message "cannot connect to x"

I am not using failsafe mode btw, I can only login via console

---

### Post by PatrickMay16 on 2007-06-07
I get you. When you log in to the console, type 
```

ls

```
to get a list of the files in your home directory.

You can also do this
```

ls -lhSr

```
Exactly like that, the lower/upper casing of the letters is important too. This will list all the files in your home directory, showing the largest last. you can also do

```

ls -lhSr | less

```

And this will let you scroll up and down the list, if the list is too big for the screen to contain. If you want to change into another folder, type

```

cd directory

```

Where 'directory' is the name of the folder you want to change into.

When you find a file that you don't mind deleting, use this command

```

rm file
```

Where 'file' is the file to delete. If you've got any questions about the commands, be sure to ask.

Try deleting a couple of files you don't need, and you KDE should work again. Once KDE is working again, you should go through your files and delee stuff you don't need, and perhaps move other files off onto external hard disks or CD-Rs, to make space on your home directory so that you can be sure this problem won't happen again soon.

Good luck!

---

