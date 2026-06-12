---
title: "Doom 3 Demo Install Help"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-03-18
No matter where I try to install it to it keeps saying:

"No write permission to"... then the path.

I have tried the default path and tried using my home directory.

Any ideas?

---

### Post by steve.horsley on 2006-03-18
I isntalled doom3 a few weeks ago. The installer likes to install to /usr/local, so you need root privilege while installing. Try running it under sudo.

---

### Post by _simon_ on 2006-03-18
i did try sudo but not had any luck :(

---

### Post by _simon_ on 2006-03-19
I tried CTRL ALT F1 (not sure what this is called?)

I logged in as root and ran sh path/filename

It still says I don't have permission to write!

To clarify:

The installer starts to run, I accept the licence and read the readme but it won't install to any path's including the default.

---

### Post by _simon_ on 2006-03-19
Ok going through it all again it appears it's NOT the installation path that's the issue.

It says I don't have write permission to the symbolic link path. But again it doesn't matter whether I use the default /use/local/bin or add my own in the home directory (is this still ok?) it still says i don't have write permision.

EDIT: I've managed to set the symbolic path in the home directory!

EDIT: The game runs fine :)

---

### Post by _simon_ on 2006-03-19
Very impressed.

That's the first graphics intensive game I have run under linux, Doom 3 will be on my shopping list :)

---

