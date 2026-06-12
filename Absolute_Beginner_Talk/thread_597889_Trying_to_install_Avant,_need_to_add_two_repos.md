---
title: "Trying to install Avant, need to add two repos"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-10-30
Hey folks. I'm making the final touches on my Gutsy install. I'm working on getting Avant installed and running, but I need to add two repos to /etc/apt/sources.list. I'm just not sure how to do this the way it's been given:
```

deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

---

### Post by llamakc on 2007-10-30
Way #1.

Open the Terminal in Applications | Accessories | Terminal

Make a backup copy of your /etc/apt/sources.list file:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-backup

```

Add those two lines to the BOTTOM of the file.

```

nano /etc/apt/sources.list

```

That opens the editor. Arrow down and cut/paste the lines in. Save it with the keys "ctrl-x (then) y". 

Now run 

```

sudo apt-get update

```

Continue following the instructions.

Way #2.

In the menu go to System | Administration | Software Sources. (enter your password).

When that opens go to the second tab called (third party software) and ADD those two lines. Save & finish with the instructions.

---

### Post by gate on 2007-10-30
open a terminal.
   sudo gedit /etc/apt/sources.list

  add those two lines to the bottom, save. Then open synaptic and reload the packages list :)

 OR
  

  GUI way, System->Administration->Software Sources

   "Third Part Software" tab, add, then put in the first line, add source. and do the same for the second.

---

### Post by CheshireMac on 2007-10-31
Alright, so I tried that, and I've tried it with other things in the past as well. I get the same error message I used to get with certain Third-Party repos in Feisty:
> W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
I'm yet to figure out what this means, as nobody's been able to give me a clear answer over the past few months (due mostly to my feeble attempt at fixing issues). I'm really putting a drive on getting my system up and running without any trouble, but I keep running into walls. 
I also get this message when I try to install the packages:
file:///home/mac/Desktop/Screenshot.png
Hopefully this sheds some light on what's going on here. Thanks for any help.

---

### Post by Partyboi2 on 2007-10-31
```
[I]wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg
sudo apt-key add 8434D43A.gpg
rm 8434D43A.gpg
sudo apt-get update[/I]
```

---

