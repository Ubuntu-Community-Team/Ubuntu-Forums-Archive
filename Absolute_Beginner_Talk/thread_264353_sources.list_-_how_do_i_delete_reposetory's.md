---
title: "sources.list - how do i delete reposetory's"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by pkslot on 2006-09-24
I've got a bad link to a reposetory in my sources.list in /etc/apt/sources.list but i cant edit it in a normal editor. I don't have the rights to do it, even if i'm the only profile, how come?

Is there any way of doing it via my terminal?

Or can i do it from synaptic, the same place i add reposetorys?

It's really bugging me, cause i cant update anything.

---

### Post by bulldog on 2006-09-24
Type in you terminal

gksudo gedit /etc/apt/sources.list

You need root rights to this so use gksudo for apps with a GUI or sudo in other circomstances.

You can delete or comment out ## rules you dont want to use.

If you alter a lot it's always wise to make a copy of it before you begin
 
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

---

### Post by Rashid584 on 2006-09-24
Yep, you can do it with synaptic. I wouldn't though.

Open terminal, and copy and paste the following command

```
sudo nano /etc/apt/sources.list
```

Type in your password when asked. That should open nano (text editor) with your sources.list open

Go down to the line you added thats broken, hit the HOME button and type '#' (without the marks) to comment the line out.

Then press CTRL+O ENTER CTRL+X and exit.

Hope that helps.

-Rashid

---

### Post by pkslot on 2006-09-24
> **bulldog said:**
> Type 
gksudo gedit /etc/apt/sources.list
and edit.

You can delete or comment out ##

Thanks man, it worked, great!!

:D

---

### Post by pkslot on 2006-09-24
> **Rashid584 said:**
> Yep, you can do it with synaptic. I wouldn't though.

Open terminal, and copy and paste the following command

```
sudo nano /etc/apt/sources.list
```

Type in your password when asked. That should open nano (text editor) with your sources.list open

Go down to the line you added thats broken, hit the HOME button and type '#' (without the marks) to comment the line out.

Then press CTRL+O ENTER CTRL+X and exit.

Hope that helps.

-Rashid


Nice, so when i write "sudo nano" it opens in nano..... i&#314;l remember that :D

But just out of curiosity, how do i do it in synaptic?

---

### Post by Rashid584 on 2006-09-24
yep, I prefer nano because its faster and works directly from terminal. Plus, it means if you REALLY mess up, you know how to fix stuff from terminal (CTRL+ALT+F1)

I use Kubuntu so in all honesty, I wouldn't know :) Kubuntu has Adept which is like Synaptic, and in that you just go Adept > Manage Repositories.

Try [here](http://ubuntuguide.org/wiki/Dapper#How_to_apt-get_the_easy_way_.28Synaptic.29)

-Rashid

---

