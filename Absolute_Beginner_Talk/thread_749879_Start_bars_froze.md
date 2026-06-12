---
title: "Start bars froze"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Boebuntu on 2008-04-08
I've had ubuntu for about 2 months. I've changed my desktop wallpaper many times, but I never messed with the starts bars. Today I was messing with them, and they froze up. I thought a simple restart would fix it. When It booted back up, the start bars were empty. Right clicking does nothing. They don't react to anything I do. It's annoying (but not impossible) to navigate without them. Is there a way to reset them?

---

### Post by buried on 2008-04-09
bug I must say?
Is it impossible to try to add a new panel?

---

### Post by Boebuntu on 2008-04-09
> **buried said:**
> 
Is it impossible to try to add a new panel?

Yes, it is. It doesn't respond to anything I do. It just sits there.

---

### Post by Boebuntu on 2008-04-09
Help. I don't know what to do.

---

### Post by Joe325 on 2008-04-09
Check your resolution first. If that seems in order try from the terminal:

Gnome-panel &

---

### Post by Boebuntu on 2008-04-09
> **Joe325 said:**
> Check your resolution first. If that seems in order try from the terminal:

Gnome-panel &
> 

boe@boe-desktop:~$ Gnome-panel &
[1] 7759
boe@boe-desktop:~$ bash: Gnome-panel: command not found

What does that mean?

---

### Post by Boebuntu on 2008-04-10
This is kinda a big thing. Could I get some help here?

---

### Post by 10Digits on 2008-04-10
What is that under that tremulous Icon???

Did you untick 'Expand' and Ticked Autohide maybe???

Try to click on that grey little box to see whether it is a panel or not!!!

I know this sounds crazy... but this the only thing I can think of right now...

If this does'nt work try searching for the problem at our forums....

I know I am lousy at this....

---

### Post by Boebuntu on 2008-04-10
> **10Digits said:**
> What is that under that tremulous Icon???

The second start bar.

> **10Digits said:**
> 
Did you untick 'Expand' and Ticked Autohide maybe???

Yes. ._.
how did you know?

> **10Digits said:**
> 
Try to click on that grey little box to see whether it is a panel or not!!!

It is the panel. When I click on it it comes forward... but if I right click on it nothing happens.

> **10Digits said:**
> 
I know this sounds crazy... but this the only thing I can think of right now...

Thanks for trying. 

> **10Digits said:**
> 
If this does'nt work try searching for the problem at our forums....

What would I search for? "I  untick 'Expand' and clicked Autohide what do I do now?"

> **10Digits said:**
> 
I know I am lousy at this....
It's all k. Thanks again for trying to help.

---

### Post by dje on 2008-04-10
Try running this:
```
killall gnome-panel
```
That should refresh the panel

hope that helps,
dje

---

### Post by Boebuntu on 2008-04-10
> **dje said:**
> Try running this:
```
killall gnome-panel
```
That should refresh the panel

hope that helps,
dje

Thanks, that got rid of it. ^_^

I ran it, and it refreshed, but it was still frozen. So I did it again, and it died and didn't come back. Now I how do I make a new one? I don't want my old one back.

---

### Post by dje on 2008-04-10
I would suggest creating a new user and see if that solves the problem, if it does just copy your files to the new user and delete your old user

hope that helps,
dje

---

### Post by Boebuntu on 2008-04-10
>_> how do i create a new user without using my gnome panels? =x sorry for being so oooby

---

### Post by Tyke91 on 2008-04-10
you shouldn't *need* to create a new user... but if you press alt+F2 and type "terminal" then enter this

```

sudo useradd -d /home/<USERNAME> -m <USERNAME>

``````

sudo passwd <USERNAME>

```you should get a new user/home directory

---

### Post by Boebuntu on 2008-04-11
OH GOD. 

I love you all. My panels are back, and working perfect. I didn't lose anything.

Thank you all. ^_^

---

