---
title: "Installing apps / sudo / su ???"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Stickymaddness on 2007-03-18
Quick questions, how do I go about installing applications? I've seen that I can use something like

```
# apt-get install appname
```

I've also tried

```
# sudo apt-get install appname
```

Which asks me for a password, which I enter, after which it returns me to the command line without any messages.

What is my root password? I tried to "su" but I don't know what password it wants since the installer didn't ask me to set a root password. 

I've tried using the update manager but I receive more errors, which seem to be access related....

---

### Post by jvc26 on 2007-03-18
It asks you for a passowrd which is your user password: For more info on sudo see:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Il

---

### Post by eljalill on 2007-03-18
Well, if appname doesn't work, you might want to try:
sudo apt-get install packagename .

But why don't you use synaptics? I think it is easier to use... and has everything apt-get also has.

Your root password, is your password.
"sudo" means "superuser do" and makes an application run as root.
With "sudo su" you can change into root in a terminal. with "exit" you get to be your own user again.

---

### Post by Arby on 2007-03-18
The 'root' password will be whatever you set the password of your primary user to be. Ubuntu doesn't really have a root user in the traditional linux sense by default. You can enable one if you want to but it's not particularly necessary. Ubuntu uses sudo instead to fulfil the functions normally supplied by root on other distro. This is the reason su isn't working the way you expect. ```
sudo apt-get install appname
 should work.
``` If it isn't then something is wrong. Does that command really produce no output at all?

You say that the update manager gives you errors. Could you post those here and we'll see if we can spot anthing out of order.

---

### Post by jvc26 on 2007-03-18
> **Arby said:**
> The 'root' password will be whatever you set the password of your primary user to be. 
Not strictly true, that is your user password. Ubuntu as you said doesnt have a root user by default, because its very security-unsafe to use a superuser or root account for everything. Instead, as explained in the link above, Ubuntu uses a 'sudo' prefix on your command which elevates your user to superuser status while it executes that command.
Il

---

### Post by Stickymaddness on 2007-03-18
Found my problem!!!

I was running feisty faun! I was given a copy of it on cd to try out by a friend. 

As I've found out, this is **NOT** a good idea! I was confused about how to install apps because Synaptics was missing from my installation!! System->Administration only had 4 items in it!!

So suffice to say, I downloaded 6.10 and am installing it as I'm posting this!

---

