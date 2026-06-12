---
title: "Looking for help"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by trucker124 on 2007-01-23
How can i get into folders like opt? keeps telling me i dont have the priviledges but i am the only one on this new box?:(

---

### Post by taurus on 2007-01-23
Applications -> Accessories -> Terminal
```
cd /opt
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bachstelze on 2007-01-23
You neet to have [root privileges](https://help.ubuntu.com/community/RootSudo) to write in /opt. What exactly do you want to do ?

---

### Post by trucker124 on 2007-01-23
yeah i can do that but it says i do not have perms to do anything. was trying to load xammp

---

### Post by LittleCleo on 2007-01-23
taurus is right, you should be able to cd into it. But your question indicates that you may be trying to do something else in that directory (mv, cp) which would relult in permission problems. If that's the case, you'll want to use sudo. just type 'sudo' followed by whatever command it is that you need root privileges to run. You'll then be prompted for a password.

```
sudo whatever-command-you-need-to-run
```

---

### Post by trucker124 on 2007-01-23
trying to install xammp into /opt

---

### Post by taurus on 2007-01-23
Perhaps

```
sudo ./xammp
```

---

### Post by trucker124 on 2007-01-23
nope,lol how can i login as root when starting lets try that

---

### Post by taurus on 2007-01-23
```
sudo su
```

---

### Post by docetes on 2007-01-23
have you installed xampp yet?

---

### Post by trucker124 on 2007-01-23
nope still stuck.

---

### Post by taurus on 2007-01-23
Are you trying to install it from source or from a binary?  What's the listing of that directory?

```
ls -la
```

---

### Post by trucker124 on 2007-01-23
> **taurus said:**
> Are you trying to install it from source or from a binary?  What's the listing of that directory?

```
ls -la
```

huh?:lolflag:   but it is a tar.gz from xammp.com

---

### Post by taurus on 2007-01-23
What is the exact name of that file and where did you have it to, ~/Desktop?

You need to unpack it first and then probably either install the binary or build it from source.

Look at Section 4 of this guide.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by trucker124 on 2007-01-23
> **taurus said:**
> What is the exact name of that file and where did you have it to, ~/Desktop?

You need to unpack it first and then probably either install the binary or build it from source.

Look at Section 4 of this guide.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

ok thanks will do

---

### Post by trucker124 on 2007-01-23
i got it figured out with the help of everyone here. logged in as root and installed the pkg. thank you all

---

