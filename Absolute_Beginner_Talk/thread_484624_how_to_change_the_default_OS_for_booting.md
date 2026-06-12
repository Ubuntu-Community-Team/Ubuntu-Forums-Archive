---
title: "how to change the default OS for booting?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by pearlygate on 2007-06-26
Like the title, can anyone help me to change the default OS loader from ubuntu to windows?

Any help is greatly appreciated. Thank you.

---

### Post by rillip on 2007-06-26
If you look at your /boot/grub there is a file called menu.lst.

Near the very very top you'll see this:

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0


```

Change 0 to be the number cooresponding to your Windows instalation.  I.e. if it's the third item on your menu, change it to 2 (since it starts counting at zero). If you don't remember, scroll down a ways and you'll see entries for each OS that shows up in the boot list.

---

### Post by Inxsible on 2007-06-26
Make sure you also count the one for the Separator. Most likely named : 'Other Operating Systems'

---

### Post by pearlygate on 2007-06-26
wow thanks a lot. it works

---

