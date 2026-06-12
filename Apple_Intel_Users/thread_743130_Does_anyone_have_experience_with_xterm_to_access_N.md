---
title: "Does anyone have experience with xterm to access Nautilus?"
date: 2008-04-02
forum: Apple Intel Users
---

### Post by vsiege on 2008-04-02
Does anyone have experience with xterm to access Nautilus? I was told that installing xterm would allow me to get Nautilus to work, but I cannot. Xterm installs and works fine. I am am to SSH into my ubuntu 7.10 machine.

---

### Post by cyberdork33 on 2008-04-02
is there any reason you specifically need nautilus? Midnight Commander is a great file manager that runs in the terminal.```
sudo apt-get install mc
```

PS this is an Apple hardware forum :)

---

### Post by vsiege on 2008-04-04
Its ok for its size.... but i was really looking for the ease of a GUI. Thats why i wanted to try to run Nautilus. I have plenty of memory to run whatever. Do you know how to run it from a mac terminal or xterm?

---

### Post by shawnansasio on 2008-06-17
Just type nautilus. To do it remotely type:

# ssh -Y username@host
username's password:

#nautilus

:guitar:

---

