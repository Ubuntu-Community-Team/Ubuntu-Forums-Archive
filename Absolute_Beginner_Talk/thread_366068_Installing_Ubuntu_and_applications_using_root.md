---
title: "Installing Ubuntu and applications using root"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by rbradshaw on 2007-02-20
I didn't join the Ubuntu web forums until after I installed Ubuntu (my bad). I don't remember if the installation asked me to provide a root password, and I don't remember if I can login the GUI using root. When I do login to the GUI, I use my user name: rbradshaw. Under this user name, I have installed Apache2 and other applications. After installing Apache2, I created an index.html file, but could not save it under /var/www because of root permissions.

Should I have installed Apache2 under root?

How do I log into root from the GUI?

If I login the GUI using rbradshaw, how can I switch to root (GUI and command line)?

How does one log into Ubuntu with the command line? Do I have to exit the GUI? How do I exit the GUI? If I do exit the GUI, how do I re-start it from the command line?

Should I start all over and re-install Ubuntu? Should I do something different? What lessons has anyone learned by installing Ubuntu again?

If I don't remember my root password, do I have any choice other than to re-install Ubuntu?

Is I don't have to re-install Ubuntu, do I need to remove Apache2 under rbradshaw, and re-install it under root? How do I remove an application from the command line? I assume the GUI has a way of removing software?

Sorry for the load of questions, but I need to determine if I should start over after learning so much through these forums.

Thanks in advance for your advice.

---

### Post by taurus on 2007-02-20
Here's something for you to read.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by rbradshaw on 2007-02-20
Now I understand about root. One should not log into root, but may require root permissions at time (true?)

What is the following command doing?

sudo chown bob:bob /home/bob/*

---

### Post by taurus on 2007-02-20
> **rbradshaw said:**
> Now I understand about root. One should not log into root, but may require root permissions at time (true?)

If you need to modify something besides your $HOME, then use the sudo command (with your own password).

> What is the following command doing?

sudo chown bob:bob /home/bob/*

It changes the ownership of everything under /home/bob/ to bob.  For more info about chown and chmod, run

```
man chown
man chmod
```

---

### Post by rbradshaw on 2007-02-20
Sorry - my mistake. What is the "sudo" command doing? I understand chown and chmod.

---

### Post by Bachstelze on 2007-02-20
It allows you to run commands as though you were root while you aren't.

---

### Post by rbradshaw on 2007-02-20
Thank you HymnToLife. I installed Apache2 using Synaptic under my rbradshaw login. Would you recommend I remove Apache2, and then re-install Apache2 using sudo?

---

### Post by Bachstelze on 2007-02-20
You did install apache with the sudo rights, believe me. Didn't Synaptic ask for a password when you started it ?

---

