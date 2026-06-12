---
title: "Synaptic Package Manager not responding"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by schmidtbag on 2007-05-06
Before I tell what the problem is, let me mention what caused the problem.  I was trying to install VirtualBox - it seemed like a good free Windows emulator.  I ran the .deb and after it finished downloading and installing a couple more packages, it just sat there for nearly 5 minutes doing absolutly nothing.  Both CPU and HDD was't being used at all so I figured I'd end/kill the process.  I'm not sure what the difference is or which one I did.  

Ever since then, I got an error message telling me to do "sudo apt-get install -f" in the terminal and I did.  That fixed half the problem.  The next half I can't fix because if I run the package or SPM again, it gives me the error, "The package virtualbox needs to be reinstalled, but I can't find an archive for it."

What do I do now?  I still have the package but on my dekstop :???:

---

### Post by taurus on 2007-05-06
What happens when you run these commands from a terminal?

```
sudo dpkg --config -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Lucifiel on 2007-05-06
Try this command in Terminal. It worked for me when Virtualbox messed up Synaptic. Not too sure if you need to put "sudo" in front of it , though. :

> dpkg --remove --force-remove-reinstreq virtualbox

---

### Post by schmidtbag on 2007-05-06
Cool thanks Lucifiel it worked!  I had to be root in order to do that but not like I really care, just to let other people know in case if they encounter the same problem,

---

### Post by Lucifiel on 2007-05-06
Sure, no problem. ;)

---

