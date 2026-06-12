---
title: "Need help with apt-get"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by duganator on 2007-09-05
Well first off I'm running kubuntu fiesty fawn...It all started when I was installing some new software via the konsole, and my computer shut down somehow...Yeah it sucked, well I typed in sudo apt-get -f install, to finish installing the software because I was getting some errors.  Well once I finished installing automatix 2 and tried to open it, a screeen popped up and said apt-get is being used by another program.  My package manager was closed, as was the konsole, any suggestions?

---

### Post by overdrank on 2007-09-05
> **duganator said:**
> Well first off I'm running kubuntu fiesty fawn...It all started when I was installing some new software via the konsole, and my computer shut down somehow...Yeah it sucked, well I typed in sudo apt-get -f install, to finish installing the software because I was getting some errors.  Well once I finished installing automatix 2 and tried to open it, a screeen popped up and said apt-get is being used by another program.  My package manager was closed, as was the konsole, any suggestions?

HI with automatix I would recommend uninstalling and then reinstall. Before you reinstall update your system.

---

### Post by duganator on 2007-09-05
I hate to sound stupid, but whats the code for un installing?

---

### Post by overdrank on 2007-09-05
> **duganator said:**
> I hate to sound stupid, but whats the code for un installing?

HI you can remove it via synaptic or adept manager. I hope! :)

---

### Post by duganator on 2007-09-05
I cant run adept manager either, I get the same error message...

---

### Post by nevle on 2007-09-05
try apt-get remove package-name also see man apt-get for more info

---

### Post by overdrank on 2007-09-05
> **duganator said:**
> I cant run adept manager either, I get the same error message...

Ok you can try 
```
sudo apt-get remove automatix2
```
or replace apt-get with aptitude

---

### Post by duganator on 2007-09-05
Wow, sometimes linux is so frustrating.  I opened up adept again to make sure that I would get the same error message again.  I tried to close it, and it wont close now, which basically means I cant uninstall automatix via the konsole.  Should I just restart?

---

### Post by duganator on 2007-09-05
Another quick question, if I'm getting the apt-get error from my package manager, doesn't that also mean that I will get a restricted message if I try to uninstall automatix via the konsole?

---

### Post by overdrank on 2007-09-05
> **duganator said:**
> Another quick question, if I'm getting the apt-get error from my package manager, doesn't that also mean that I will get a restricted message if I try to uninstall automatix via the konsole?

HI it may but like last nite for me installing on a friends system I could then track down what was causing the error and go from there. Automatix is not recommend by ubuntu but I have used it in the past. Since your download was interrupted that is why I recommended removing and reinstalling.

---

### Post by philven on 2007-09-08
I'm having a problem with Adept.  I added a repository and now it tells me there is an error and says to run apt-get setup or apt-get install in terminal.  When I do I get this error meesage  E: Malformed line 44 in source list /etc/apt/sources.list (dist parse).   I have tried to edit the sources.list file in terminal but I get a message that says it is an invalid operation.  I tried opening the sources.list file in an editor, but it says I need SuperUser to edit and save.  What can I do?

---

### Post by overdrank on 2007-09-08
> **philven said:**
> I'm having a problem with Adept.  I added a repository and now it tells me there is an error and says to run apt-get setup or apt-get install in terminal.  When I do I get this error meesage  E: Malformed line 44 in source list /etc/apt/sources.list (dist parse).   I have tried to edit the sources.list file in terminal but I get a message that says it is an invalid operation.  I tried opening the sources.list file in an editor, but it says I need SuperUser to edit and save.  What can I do?

Hi you may try this command to edit you list
```
gksudo gedit /etc/apt/sources.list

```
Good luck!

---

### Post by philven on 2007-09-08
Didn't work.  It told me I needed to install gksu.  Since Apt isn't working, I can't install anything.  The plain edit command doesn't work since it is an unknown command.  I may switch to GNOME.  KDE is not as user friendly as GNOME.

---

### Post by overdrank on 2007-09-08
> **philven said:**
> Didn't work.  It told me I needed to install gksu.  Since Apt isn't working, I can't install anything.  The plain edit command doesn't work since it is an unknown command.  I may switch to GNOME.  KDE is not as user friendly as GNOME.

I apologizes I did not see you are using kde 
```
kdesu kate /etc/apt/sources.list
``` 
I believe is the command

---

### Post by philven on 2007-09-08
It worked.  Thanks.  I'm copying and pasting that command in case I screw the pooch again.

---

