---
title: "Automatically setting $PATH"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by FXFman1209 on 2007-05-02
Alright, well, I have just a simple problem...

I want to make it so my $PATH always includes ${HOME}/bin... if I do export $PATH=${PATH}:{$HOME}/bin in a shell, it only works until I close it. If I reopen another terminal, I have to reset it. Is there any way that i can change it so it always includes ${HOME}/bin??

---

### Post by taurus on 2007-05-02
You just add that to your ~/.bashrc and it will stick every time you log in or whenever you open a terminal.

```
gedit ~/.bashrc
```
Then add

```
PATH=$PATH:~/bin
export PATH
```

---

### Post by EndPerform on 2007-05-02
Try adding that line to your .bashrc file in your home directory, making sure you back up your original file.  Once you do that, you should be good to go :)

---

### Post by FXFman1209 on 2007-05-02
Thanks guys! It works great.

---

### Post by Cypher on 2007-05-02
Though I think you should be adding it to your "~/.bash_profile" file, but it all works..:)

---

