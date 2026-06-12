---
title: "Radeon 9200 PRO problems when booting from CD"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by blakkinferno on 2006-12-10
Well, a while ago, when I was about to install ubuntu on this computer... it broke. Not because of ubuntu, I'm proud to report.

Anyway, it broke, and i was on my sisters. I dual-booted it with a small partition, and loved it.

However, im back on this computer... its a Dell with
1 gig of ram
Radeon 9200 PRO

and, when i hit "start or install ubuntu" on the CD, it goes to the "fsck" thing, and it says there was a problem with Xorg and its probably not set up properly, and asks if i want to view the errors returned, and then another screen asks if i want to view and in-depth log of the errors returned.
I can either get to a ubuntu console (not sure how i did that), or it goes back to fsck and i believe it freezes.

How do i install ubuntu with these problems? I can't even get to the ubuntu desktop(workspace?).

---

### Post by riven0 on 2006-12-11
> **blakkinferno said:**
> 
How do i install ubuntu with these problems? I can't even get to the ubuntu desktop(workspace?).

Okay, when you get to the terminal, can you try running this command:

> sudo dpkg-reconfigure xserver-xorg

If you don't know what options to choose, just keep hitting enter. But make sure to enter ATI as your graphics card.

After that's finished and you get returned to the prompt, try this:
> 
sudo dpkg-reconfigure -phigh xserver-xorg

Then:
> 
starx

---

### Post by blakkinferno on 2006-12-11
Well, i want to try it, but i dont remember how i got to the Ubuntu terminal from the Xorg error screen. 

Its a blue screen asking about if i want to look at the error messages. Do you know how to get to the console/terminal from there? Thanks.

---

### Post by blakkinferno on 2006-12-11
Okay, nevermind. I entered all the stuff into the terminal... but the command starx didnt do anything. Help, please? 

(WHen i type in starx is just says "bash:command not found."

---

### Post by blakkinferno on 2006-12-13
Sorry, just a bump to bring it to the top. Me wants my ubuntu ^^.

---

### Post by xabbott on 2006-12-13
> **blakkinferno said:**
> Sorry, just a bump to bring it to the top. Me wants my ubuntu ^^.

He meant to say ```
star**t**x
```

---

### Post by blakkinferno on 2006-12-14
> **xabbott said:**
> He meant to say ```
star**t**x
```

ooooooooooooh! i should try that then ^^

---

