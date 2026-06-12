---
title: "Neither Azureus nor Menu Editor works..."
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-03-07
Neither of these applications initialize when clicked.  

I tried reinstalling Azureus but still didn't work.

Any ideas?

Thanks in advance...

---

### Post by Moebius on 2006-03-07
Can you open a terminal and start those programs from there?

If not, what kind of errors do they output

Note, to start azureus just type at the terminal
```
azureus
```

To start the menu editor just type at the terminal
```
smeg
```

---

### Post by Sweet on 2006-03-07
You should also ensure you have the the latest **Sun** Java runtimes (1.5) installed and set up.

You may need to add an extra repository to your "/etc/apt/sources.list" if you havent already.

Simply add the line:
```
deb http://ubuntu.tower-net.de/ubuntu/ breezy java
```

Then install the runtimes/SDK from synaptic.

Once you have installed the Sun java runtimes you will need to configure your system to use it instead of the ubuntu default one. This is very important. You can do this using:
```
sudo update-alternatives --config java
```

---

### Post by Cousindaddy on 2006-03-07
Thanks for your response.

I reinstalled Azureus and it now works.  However, I can only get SMEG to work from terminal.  I tried reinstalling it to no avail.  

I'm having trouble at bootup with:

[B]> Starting Enterprise Volume Management  Failed
Mounting Local File Systems  Failed[/B]

I'm thinking that this might be related somehow.

---

