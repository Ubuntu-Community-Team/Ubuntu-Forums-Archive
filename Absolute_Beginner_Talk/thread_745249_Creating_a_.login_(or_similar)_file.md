---
title: "Creating a .login (or similar) file"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by susan_1890 on 2008-04-04
I'm fairly new to Ubuntu and linux as well. However, I do have accounts on several other linux machines that run Debian. On these machines, I've created a .login file in my home directory that sets a few things (environment variables, mostly). I want to do the same thing for my home computer that's running Ubuntu (gutsy). 

I've created the file as /home/myusername/.login. However, it doesn't get read when I login to Ubuntu. I'm sure there's something simple I'm doing wrong, but I can't seem to find a thread on this when I search (I get all the posts which have the word login -- not just ones specific to .login).

If I open a terminal window and type source .login it then reads my login file and sets the environment variables I want, but I'd like this to happen automatically. Any suggestions would be greatly appreciated.

(If it matters, I'm using tsch as my shell).

---

### Post by ByteJuggler on 2008-04-04
Find out what tcsh's default profile script is (I don't know offhand, but given your problems  I doubt it's ".login")  The original "sh" profile is/was called ".profile" and bash uses ".bash_profile".  You might therefore blindly try .profile and see what happens, or switch to bash (I guess you wouldn't want to though, given that you know enough about scripting and shells to know there's alternatives and to have gotten to the point of having chosen an alternative shell. :) )

---

### Post by susan_1890 on 2008-04-04
Thanks -- that helped me figure out the right thing to search on. Turns out the answer was really simple. tcsh reads .login every time you open a login shell. But the terminals I launch in ubuntu aren't login shells, so it wasn't reading .login. I just had to rename .login as .tcshrc and it worked fine.

---

### Post by ByteJuggler on 2008-04-05
> **susan_1890 said:**
> Thanks -- that helped me figure out the right thing to search on. Turns out the answer was really simple. tcsh reads .login every time you open a login shell. But the terminals I launch in ubuntu aren't login shells, so it wasn't reading .login. I just had to rename .login as .tcshrc and it worked fine.

Ah yes, I should've thought of that actually... (bash uses .bashrc for non login shells etc...) :)

---

