---
title: "loggin in as root"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Lameboy on 2006-10-12
Ok, i'm trying to log on as root in terminal.
Typing "su" , it asks me for the pass wich i dont have.
How do i change the root password?

One more thing? What does "sudu" do? Everytime i type sude ex. "sudu passwd" it tells me "sudu command not foud. What the hell?

I'm new to this so please show me the light.:-k

---

### Post by Portable_Jim on 2006-10-12
Are you the first user (the user that you created when Ubuntu was installed)?

---

### Post by bapoumba on 2006-10-12
**sudo -s** will give you a root terminal, "exit" to quit.
The password will be your user password, if it is in the adm and admin groups ;)

---

### Post by hotbrainz on 2006-10-12
Hello,

Su will give you root access. Use the same paaword as that you use to login as user.

the command which  is much safer is "sudo" and not "sudu". This gives you root access only to execute that one operation.

Welcome to Ubuntu.

Cheers

---

### Post by hyper_ch on 2006-10-12
actually, it's **sudo** and not **sudu** :)
sudo lets you execute commands as root while not being root and temporary acquiring root privileges... ok, that's a pretty plain explanation but I think it does the job :)

---

### Post by Rhubarb on 2006-10-12
The command isn't "sudu", it's "sudo".
The password is generally the same as the password you used to login.
If you want to have a super user terminal session (like most other non-"sudo" distros out there), then try "sudo su" - I think this should work for you.

---

### Post by endorfin on 2006-10-12
Are you trying to be root for longer than just a few commands? If not you could use sudo in front of each command to operate the command as root. You will only be asked to provide a password the first time. The password is the password for your user's account.

---

### Post by hyper_ch on 2006-10-12
If you want to have longer sudo available then you can just enter

```

sudo -i

```

That will grant you sudo rights for the whole terminal session.

---

### Post by Lameboy on 2006-10-12
U guys rock!!!


It works, thx!!!!:p

---

### Post by hyper_ch on 2006-10-12
you're welcome :)

---

### Post by PriceChild on 2006-10-12
For a quick introduction: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You should use sudo for most root commands, for example,```
sudo nano /etc/fstab
```and gksudo for graphical apps e.g.```
gksudo nautilus
```

A good introduction to graphical sudo (gksudo) is: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

