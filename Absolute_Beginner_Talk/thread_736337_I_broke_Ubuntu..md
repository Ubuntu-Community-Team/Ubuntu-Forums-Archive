---
title: "I broke Ubuntu."
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by dungheap on 2008-03-26
I break everything. I started following the instructions [here]("http://www.ubuntux.org/root-login-ubuntu") which I'm sure I shouldn't have done, I only completed up to number 3 though because I couldn't do the rest.

(1.First enter into ubuntu as your user login.2.Then open the terminal and type the command sudo -s,it will ask for root access and type the password.3.Then type passwd root it will ask for new password)

Then I rebooted. Now I've locked myself out of the OS. I try to log in and it says

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

I think that's it. Please help and call me a stupid boy.

---

### Post by ByteJuggler on 2008-03-26
<thinking out loud> I cannot understand some people's obsession with logging in as root, when "sudo -s" has for all practical intents and purposes the exact same effect, without the downsides of logging in as root.... :confused:
</thinking out loud> 

Anyway, the 3 steps you describe wouldn't have caused the problem you're seeing, so wittinginly or unwittingly you did something else that's the real reason for your problem.  What other commands have you run if you do know? Can you get to a console command prompt by pressing ctrl-alt-f1, or can you boot up in "safe mode" and get to a command prompt?

---

### Post by dungheap on 2008-03-26
I probably did do other stuff but I dno what. :( Sorry. I can still use Ubuntu and the terminal with the installation disk, I just can't login as the installed user.

---

### Post by saj0577 on 2008-03-26
Can you use terminal without using live cd?

---

### Post by dungheap on 2008-03-26
Yes.

---

### Post by Bachstelze on 2008-03-26
Login through the terminal, do

```
sudo chown $(whoami):$(whoami) ~
sudo chmod 755 ~
sudo chown -R $(whoami):$(whoami) ~/.dmrc
sudo chmod 644 ~/.dmrc
```

Hopefully, that will do the trick.

---

### Post by dungheap on 2008-03-26
Thank you, trying it now, brb.

---

### Post by iansane on 2008-03-26
> **ByteJuggler said:**
> <thinking out loud> I cannot understand some people's obsession with logging in as root, when "sudo -s" has for all practical intents and purposes the exact same effect, without the downsides of logging in as root.... :confused:
</thinking out loud> 

Anyway, the 3 steps you describe wouldn't have caused the problem you're seeing, so wittinginly or unwittingly you did something else that's the real reason for your problem.  What other commands have you run if you do know? Can you get to a console command prompt by pressing ctrl-alt-f1, or can you boot up in "safe mode" and get to a command prompt?

It's just like using the administrator account in windows. I did it when I first installed Ubuntu because I didn't understand sudo and sometimes even with sudo I get permission denied. Then I had to learn how to do sudo su to be in a actuall root shell. Computer savy people have a hard time admitting that to the average noob, terminal looks like another language and is hard to understand.

Anyway, I just used the GUI. System>admin>login window sessions and chose allow administrative log in. Of cource that only works if you have a GUI. You have to use users and groups to make a password cause it appears to have one auto generated and no way of knowing what it is.

Interesting. I just found out that no root or root home exists in my new installation of Hardy. Strange, don't know how that works.

---

### Post by prshah on 2008-03-26
> **dungheap said:**
> I break everything. I started following the instructions [here]("http://www.ubuntux.org/root-login-ubuntu") which I'm sure I shouldn't have done, I only completed up to number 3 though because I couldn't do the rest.

(1.First enter into ubuntu as your user login.2.Then open the terminal and type the command sudo -s,it will ask for root access and type the password.3.Then type passwd root it will ask for new password)

Then I rebooted. Now I've locked myself out of the OS. I try to log in and it says

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

I think that's it. Please help and call me a stupid boy.

Why not just clear up the errors it says, one by one?

```
 sudo chown -R dungheap:dungheap /home/dungheap
sudo chmod 644 /home/dungheap/.dmrc
sudo chmod 755 /home/dungheap

```

NOTE: At your own risk: you have a broken system anyway, this may heal or harm, but it won't delete any files etc.

EDIT: Got in a little late

---

### Post by dungheap on 2008-03-26
I did this, but it came back with "cannot access "/.dmrc, no such file" etc. :( Should I be doing it from me@computer or somewhere else? Should I just reinstall and try not to touch the terminal ever again?

---

### Post by Bachstelze on 2008-03-26
You need to type that right after you log in, and watch out for typos.

---

### Post by dungheap on 2008-03-26
Okay I've done it all again properly this time and it accepted all the commands but it's still doing exactly the same thing, it says that and then it starts logging in and then says my session lasted less than 10 seconds etc. :(

---

### Post by Bachstelze on 2008-03-26
All right, do that then :

```
sudo chown -R $(whoami):$(whoami) ~
sudo chmod -R 755 ~
sudo chmod 644 ~/.dmrc
```

---

### Post by dungheap on 2008-03-26
I've done that, I've done everything I've been told and there is no change. Please don't give up on me, I'll give you chocolate.

---

### Post by Bachstelze on 2008-03-26
That's really weird... Do

```
ls -l ~/.dmrc
```

and copy what you get.

---

### Post by dungheap on 2008-03-27
Sorry I disappeared, my internet broke. The terminal said:

-rw-r--r-- 1 loginname loginname 26 2008-03-23 14.16 /home/loginname/.dmrc

When I did a normal plain "ls" I couldn't see anything called .dmrc.

How do I perform a search? And move files? Just in case that's what I did originally.

*RTFMs*

---

### Post by stalkingwolf on 2008-03-27
When I got that " session lasted less than 10 seconds" it was because the / partition
was full.  Might be worth a check.

---

### Post by dungheap on 2008-03-27
I don't think it's that, thanks though.

---

### Post by dungheap on 2008-03-27
I sort of fixed it, I did sudo -s
sudo useradd -d /home/userid -m userid
sudo passwd userid
and was able to log in with that so it's okay.

Well it still seems a bit dodgy tbh, I'm gna back everything up and reinstall.

Thank you.
x

---

