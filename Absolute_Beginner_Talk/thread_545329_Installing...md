---
title: "Installing.."
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by H_91 on 2007-09-07
[SIZE=1]Hi there,
I recently installed Ubuntu on my laptop and loving every bit of it. :) I'm just having a problem where I don't know what I'm supposed to do.. 

I'm trying to install **Limewire** through the **Package Installer** but when I click on "**Install Package**", this message pops up.. 

**"Only one software management tool is allowed to run at the same time.**
*Please close the other application e.g. 'Update Manager', 'aptitude' or 'Synaptic' first."*

Obviously, I'm new to Ubuntu, how do I close the other applications? :? 
*Feeling like a noob*


**[SIZE=5]+[/SIZE]**
<edit>

+when I try to install from Synaptic, an error msg appears... 
[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

[/B] </edit>[/SIZE]

---

### Post by swisscow on 2007-09-07
Make sure you have no other package manager open, e.g synaptic, add/remove, update. Just the one you are using

---

### Post by H_91 on 2007-09-07
But I don't have any package manager open ...

---

### Post by Terl on 2007-09-07
> **H_91 said:**
> But I don't have any package manager open ...

Is the update manager closed as well?  The update manager and/or synaptic package manager will cause this if either is open.

---

### Post by H_91 on 2007-09-07
> **Terl said:**
> Is the update manager closed as well?  The update manager and/or synaptic package manager will cause this if either is open.

Could you please tell me where that is exactly done? =S

---

### Post by Tautoa on 2007-09-07
Try typing "sudo dpkg --configure -a" into a terminal (without the quotes)
Then try installing Limewire again.

However, I would recommend using FrostWire over LimeWire...
It's more or less the same program, but the FrostWire is free (there is no Pro version that you have to pay for), and it doesn't come bundled with adverts and spyware etc.

[http://www.frostwire.com/](http://www.frostwire.com/)

---

### Post by th3rmite on 2007-09-07
Well, can you visibly see a window open? I think that the software update app periodically updates itself through the net. A quick way to tell is to go to the command line, I know being new to Linux that is definitely something you probably don't want to hear, and type the following:

```
sudo apt-get update
```

If there aren't any errors, it should start scrolling the screen as it updates itself.

Oh and btw, I kept having problems trying to install limewire by just double clicking on the .deb file. I have a slower internet connection and the installer was hanging my computer while it was downloading all the dependencies. So, I got the commands to download all the dependencies from the command line. They downloaded much nicer in the back ground. The code is 

```
sudo apt-get install sun-java5-jre libltdl3 sun-java5-bin unixodbc java-common odbcinst1debian1
```

Once that is downloaded, just double click on the limewire .deb file and it should install fairly quickly.

---

### Post by H_91 on 2007-09-07
[SIZE="1"]Solved!
Thanks a bunch, that did it! =D
Also, thank you **Tautoa** for mentioning FrostWire, I'm going to try it. =]

Thanks again.[/SIZE]

---

### Post by H_91 on 2007-09-07
[SIZE="1"]Wow, thanks a lot **th3rmite**, but I had another error when typing in the first code... **E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. **

[/SIZE]

---

