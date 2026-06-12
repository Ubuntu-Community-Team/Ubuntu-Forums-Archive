---
title: "How to run Gnome?"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by WindForce on 2007-04-15
Hi all
I installed 6.10 server, then i run:
sudo aptitude update
sudo aptitude install ubuntu-desktop

When it finished, i rebooted, and i see the graphic ubuntu logo while the machine boots, but then i get the command-line user and password, then i login to a terminal.
Why doesn't the machine load the graphical environment automatically? What command should i run to get to gnome, and how can i automate this?

Thanks

---

### Post by taurus on 2007-04-15
What happens if you run this command at the prompt, after you've logged in?

```
startx
```

You probably have to configure X first though.

---

### Post by TheRingmaster on 2007-04-15
why did you install the server to begin with? Why not just install regular ubuntu?

---

### Post by maxamillion on 2007-04-15
```
sudo /etc/init.d/gdm start
```

---

### Post by WindForce on 2007-04-15
> **taurus said:**
> What happens if you run this command at the prompt, after you've logged in?

```
startx
```

You probably have to configure X first though.

I get some empty graphic screen and i can only reboot

---

### Post by WindForce on 2007-04-15
> **maxamillion said:**
> ```
sudo /etc/init.d/gdm start
```

Hi
Thanks guys for your fast response.

Running the code above, i get "gdm : command not found"

---

### Post by WindForce on 2007-04-15
> **TheRingmaster said:**
> why did you install the server to begin with? Why not just install regular ubuntu?

Well this is going to be a server, so i went with the server version.
After install, i thought it would be easier to maintain ( since you may have noticed i'm a complete noob ) if i installed some lightweight graphical environment, so there..

---

