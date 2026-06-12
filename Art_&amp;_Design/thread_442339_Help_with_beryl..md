---
title: "Help with beryl."
date: 2007-05-13
forum: Art &amp; Design
---

### Post by Nightmare- on 2007-05-13
Hi there, I'm sure that I have done this correct.. I have done:
```

sudo gedit /etc/apt/sources.list

**added the following:**

deb http://ubuntu.beryl-project.org feisty main

[B]Then:
[/B]
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get install beryl beryl-manager emerald-themes heliodor beryl-manager
[B]
Then ran this in the terminal:[/B]
beryl-manager
```

When I run* beryl-manager* in the terminal it just shows me a blank screen and I can't do anything about this apart from reset X.

Is there anything I can do.. can anyone help me?

---

### Post by sardines454 on 2007-05-13
I am having a similar problem.  I entered all the stuff that you did and then the terminal said

E: The package h-k-suite needs to be reinstalled, but I can't find an archive for it.

I don't know what this means.  I was able to install Beryl Manager but not Emerald or Heliodor.  If you know why please help!

---

