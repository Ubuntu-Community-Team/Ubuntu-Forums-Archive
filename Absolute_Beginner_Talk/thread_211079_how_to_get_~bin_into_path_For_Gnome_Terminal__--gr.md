---
title: "how to get ~/bin into path For Gnome Terminal?  --grrr"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by tefflox on 2006-07-07
hi, i have an aggravating problem.  please tell me how i can get my ~/bin scripts to run in the gnome terminal.  i'm assuming this can be done.  the scripts work on tty1 -tty6.  thank you

---

### Post by Sonofmoog on 2006-07-07
Add the following to /$HOME/bashrc

# Add Scripts dir to path
export PATH=$PATH:$HOME/bin

Next time you reboot, do echo $PATH in a terminal and it should be there.  

HTH

---

### Post by tefflox on 2006-07-07
> **Sonofmoog said:**
> Add the following to /$HOME/bashrc

# Add Scripts dir to path
export PATH=$PATH:$HOME/bin

Next time you reboot, do echo $PATH in a terminal and it should be there.  

HTH

Yes!

---

