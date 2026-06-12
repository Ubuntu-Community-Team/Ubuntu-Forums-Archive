---
title: "Wine Emulator"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Snitz on 2008-03-27
I want to install the wine windows emulator to be able to run windows software but when I search for it in the "add/remove applications" I cannot install it even though it shows in the results.

Any suggestions?

---

### Post by kesman on 2008-03-27
What do you mean "cannot install"? Does it give you error messages?

---

### Post by kpkeerthi on 2008-03-27
See the instructions here... [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Snitz on 2008-03-27
No, it doesn't give me any errors as when I select it, I cannot "check" it nor press "apply" to start the download process.

---

### Post by Snitz on 2008-03-27
> **kpkeerthi said:**
> See the instructions here... [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Did what they asked and still wouldn't allow me to install it from the "add/remove applications"

---

### Post by Tomatz on 2008-03-27
Type this in a terminal:

**sudo apt-get install wine**

Hopefully it will work if not tell us the output.

:)

---

### Post by Snitz on 2008-03-27
> **Tomatz said:**
> Type this in a terminal it will install wine:

**sudo apt-get install wine**

:)

I guess it's working now but why wouldn't want to install from the synaptic?

---

### Post by kesman on 2008-03-27
> **kpkeerthi said:**
> See the instructions here... [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

This is a great post, since with this you will add a special repository that always contains the newest version of wine. To simplify things, I'll tell you how to do this.

First run the given command that add's the repositorys key:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add 

```
in terminal. It should say OK.
Then add the wine repository with the command given in the instructions:
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```

Note that this sould be one single line, as it may show up in two lines here.
After this, run
```

sudo apt-get update
sudo apt-get dist-upgrade

```

in terminal to update your apt and all the packages you already have on your system.

---

### Post by Tomatz on 2008-03-27
> **Snitz said:**
> I guess it's working now but why wouldn't want to install from the synaptic?

Try a:

sudo apt-get update

Maby your package lists just need reloading :)

---

### Post by Snitz on 2008-03-27
It's downloading now in Terminal, I'll do the update thing as soon as it finishes.
Thank you all for helping me, I really appreciate it.

---

### Post by Snitz on 2008-03-27
I just ran the command

```
sudo apt-get update
```

It went well and at the end it gave me these 2 lines

> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


What does that mean?

---

### Post by hhhhhx on 2008-03-27
> **Snitz said:**
> I just ran the command

```
sudo apt-get update
```It went well and at the end it gave me these 2 lines



What does that mean?
you may have synaptic running when you are installing from the terminal aswell ( you cant install from 2 sources at once)

---

### Post by Snitz on 2008-03-27
Ah ok, thanks for the tip.

---

