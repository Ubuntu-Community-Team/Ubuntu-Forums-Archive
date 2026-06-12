---
title: "filetype conversions..."
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by Patrick-Ruff on 2006-03-10
hey all, is it possible to convert files using linux? such as, converting a .deb file to a .rpm (which is my current situation right now.

---

### Post by Perfect Storm on 2006-03-10
It's possible with alien. Though it's not recommendable. Which application are we talking about you want to convert?

---

### Post by Brunellus on 2006-03-10
why would you need to convert a .deb to an .rpm?  if you mean .rpm to .deb, you can use 

alien

but that's not usually recommended.

What are you trying to achieve by the conversion?  If you said what you wanted to do, maybe we could point out easier ways of doing it.

---

### Post by dvarsam on 2006-03-10
Yes, use the program called "alien"

Launch a terminal window & type:

sudo apt-get install alien

Note:
The program runs from the Terminal.

Command:

alien -d file.rmp		( < - The "-d" option stands for convert to Debian)

You should probably be able to do the opposite (have NOT tried it),
but how about:

alien -r file.deb

Tell us if it worked for you...

---

### Post by Patrick-Ruff on 2006-03-10
on another note, I'm using SUSE 10. also, I was referring more to ALL deb files.

---

### Post by Patrick-Ruff on 2006-03-10
also, where would one find the program? and whats the best place to download all sorts of Linux programs?

---

### Post by Perfect Storm on 2006-03-11
Well, it's diffently a bad idea to convert them all by alien, nuff' said.


You'll find programs/applications, libs etc. via apt-get for ubuntu. But you might want to makes some changes in your sourcelist. Suse have something similar with yum.

You might want to check Synaptic (if you use ubuntu/gnome). System ---> Adminstration ---> Synaptic package manager

---

### Post by Patrick-Ruff on 2006-03-11
please read above, I do not use Ubuntu on my laptop. SUSE 10...

---

### Post by Perfect Storm on 2006-03-11
Still, it's a bad idea to convert .deb to .rpm or vice versa. If you're using Suse you'll have to use .rpm as they are two diffrent package system and a convertion can break stuff or not working.
If you want help getting .rpm packages I'm pretty sure there's some nice people on the Suse forum who'll guide you through how to setup yum and/or find the .rpm packages you need.

Now you're warned that you can break both system if you that either on Suse or ubuntu, but if you want to proceed anyway:

Open the terminal and write:
```
sudo apt-get install alien
sudo alien -r XXXXXXX.deb
```

for more information about alien_
```
man alien
```

and 
```
alien --help
```


> and whats the best place to download all sorts of Linux programs?

From your repositories. The gui for has I explain above. Suse have something similar. Everything is gathered under same roof so to speak. If you want expand more software/applications etc. you need to modify or add your soucelist:

```
sudo gedit /etc/apt/sources.list
```
Here you can enable/disable where to get stuff from. (with few exceptions)

---

### Post by stalefries on 2006-03-11
Why are you asking in the Ubuntu Forums, if it's Suse-related? You'd be better off asking Suse users.

---

