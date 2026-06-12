---
title: "How to uninstall ?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Accurax on 2007-04-24
I have installed HPLIP in an attempt to get my printer working, but, i think i made an error when moving through the installation process... in fact i got lots of errors telling me dependant files do no exist etc.

So, i want to start again, from scratch.... but i can seem to get my system back to the way it was.

Simply deleting the folder doesnt work, and there is no un-install file.

Any tipe on properly removing hplip from my ubuntu box please?

---

### Post by jfinkels on 2007-04-24
You should be installing and uninstalling software by using Synaptic or the command-line utility "aptitude". To remove a program, type the following in the terminal:
```

sudo aptitude remove hplip

```
To install a program, type the following in the terminal:
```

sudo aptitude install hplip

```

take a look at these sites for information on installing and uninstalling programs
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.monkeyblog.org/ubuntu/installing/#uninstalling](http://www.monkeyblog.org/ubuntu/installing/#uninstalling)

---

### Post by Accurax on 2007-04-24
I downloaded the hplip file and ran it with:

sh hplip-1.7.4.run

Is there a better way of doing this? ... im totally lost and confused im sorry :(

---

### Post by jfinkels on 2007-04-24
> **Accurax said:**
> I downloaded the hplip file and ran it with:

sh hplip-1.7.4.run

Is there a better way of doing this? ... im totally lost and confused im sorry :(

No need to apologize! There's many ways to skin a cat. The best way for a beginner to install software in Ubuntu is using the package manager, Synaptic!

---

