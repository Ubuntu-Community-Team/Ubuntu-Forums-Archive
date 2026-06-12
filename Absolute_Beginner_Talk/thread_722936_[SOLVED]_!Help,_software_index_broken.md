---
title: "[SOLVED] !Help, software index broken"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Mick8882003 on 2008-03-13
Was trying to get mp3 ripping up and running, ran *sudo apt-get install ubuntu-restricted-extras* and it didnt complete, Now the software index index is broken and I cannot work out what to do.

---

### Post by Hospadar on 2008-03-13
What error does it give you exactly?  I think you need to run "sudo apt-get -f" or maybe "sudo dpkg -f" or something like that.  maybe "sudo apt-get install -f"

Try some of those and see what happens.  I think you can also go into synaptic (System->Administration) and fix the index from in there.  try the "Broken Packages" filter

---

### Post by Mick8882003 on 2008-03-13
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

I have already tried to fix it as abouve and it failed as well.

as far as I know a package is half installed, it stopped and now im not sure what to do.

---

### Post by Mick8882003 on 2008-03-13
got it

---

