---
title: "How to navigate through directories via terminal?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Vega on 2007-04-06
I know there's a CD\ command that works this, to get from one directory to another

lets say I want to get to my apps folder that's in my home directory how do I cd to that?

---

### Post by taurus on 2007-04-06
```
cd **directory_name**
```

---

### Post by hec1979 on 2007-04-06
lets 's just say that your in the root directory /root

issue the following command cd /home/your-hostname/apps/

and it will take you there

---

### Post by bashologist on 2007-04-06
> **Vega said:**
> I know there's a CD\ command that works this, to get from one directory to another

lets say I want to get to my apps folder that's in my home directory how do I cd to that?

In the last example here the tilde expands to the home folder; Search man bash or google "tilde expansion" for more information.

cd "/home/$USER/apps"
cd "$HOME/apps"
cd ~/apps

---

### Post by aysiu on 2007-04-06
If you start off in /home/vega and want to get to /home/vega/apps, you would type ```
cd apps
```

---

### Post by Maestro23 on 2007-04-06
Just some more logs on the fire:

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

