---
title: "setting environment variables"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-02-15
I am trying to set my environment variables using "export." When I do env it shows the path that I listed. However if I exit the terminal the variable is no longer there. How can I always have my environment variables set?

---

### Post by Bachstelze on 2007-02-15
Add the comand in bashrc. ~/.bashrc if you want to set the variable on a per-user basis or /etc/bashrc to set it system-wide.

---

### Post by syalam on 2007-02-15
I went to /etc/bashrc and there is nothing there. I also tried ~/.bashrc and its a bunch of scripting code..i didnt see any env variables there

---

### Post by Bachstelze on 2007-02-15
Just add your export line(s) in there. They will be executed with all the other code whenever you'll login.

---

