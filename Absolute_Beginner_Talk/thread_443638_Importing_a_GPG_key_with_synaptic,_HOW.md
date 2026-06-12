---
title: "Importing a GPG key with synaptic, HOW?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by mpec82 on 2007-05-14
I would like to use the ubuntustudio theme, how can i import the gpg key ([http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg)) with synaptic?

How can i save the key? What file extension.


Thx

---

### Post by 67GTA on 2007-05-14
(in a terminal)sudo gedit /etc/apt/sources.list
add "deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main" (without the quotations and save)
(in a terminal)wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
(in a terminal)sudo apt-get install ubuntustudio-look

---

