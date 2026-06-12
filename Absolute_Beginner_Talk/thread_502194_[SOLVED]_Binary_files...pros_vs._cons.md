---
title: "[SOLVED] Binary files...pros vs. cons"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-16
Hello, 

Im a noob to Ubuntu/Linux and i have a pretty simple question.  Everywhere i go to look for software to download, i always see an option to download a BIN file.  I know this stands for binary, but what are the advantages\disadvantages for downloading a binary file as opposed to a "regular" download file (usually [filename].tar.gz)? 

Secondly, how do i go about downloading and installing binary files.

---

### Post by aysiu on 2007-07-16
If you're really a "noob" to Ubuntu/Linux, you should read this first:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

.bin or .tar.gz files should be a last resort for new users.

---

### Post by FleetAdmiral74 on 2007-07-16
I agree with the above poster. I fully recommend using the repositories, found in administration - synaptic, that takes care of a lot of the troubles you might get with binary and tar.gz files. Or the equivilant found in the command line,as shown in the above link.

---

### Post by ITdrummer on 2007-07-16
Thanks, but im willing to take on the challenge if you are willing to explain it to me.

---

### Post by aysiu on 2007-07-16
In [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
chmod +x *nameoffile*.bin
sudo ./*nameoffile*.bin
```

The method for installing most .tar.gz files is described in the link I gave you earlier.

---

### Post by asmoore82 on 2007-07-16
^^ And there you see the CON

you must give root access to every annonymous "bin" file you want to install.

you need to understand now that it is only a matter of time before this breaks your system.
Always install from apt/Synaptic when available.

---

### Post by ITdrummer on 2007-07-16
the first line changes the file to an executable file, then the second line executes? Is this correct?

---

### Post by Soybean on 2007-07-16
Also, if you install using Synaptic or apt, you get automatic updates to newer versions of the software. It's one of my favorite Ubuntu features.

In Windows, you typically either have to go find the new version yourself and download/install it, or the program has to handle it on its own (with an annoying system-tray-based updater, or a check every time you run the program). In Ubuntu, every single piece of software I have is updated right along with my OS. It's like if Windows Update handled every program ever made for Windows.

I'll install from source or use a binary if I have to, but it always makes me very grumpy. ;)

EDIT:
> **ITdrummer said:**
> the first line changes the file to an executable file, then the second line executes? Is this correct?

That is correct. :)

---

### Post by ITdrummer on 2007-07-16
Ok, so basically, i only should use .bin or .tar.gz files when software is not available in synaptic?  If so, thats easy enough to understand.

---

### Post by aysiu on 2007-07-16
> **ITdrummer said:**
> Ok, so basically, i only should use .bin or .tar.gz files when software is not available in synaptic?  If so, thats easy enough to understand.
You've got it.

---

### Post by Canis familiaris on 2007-07-16
> **ITdrummer said:**
> Ok, so basically, i only should use .bin or .tar.gz files when software is not available in synaptic?  If so, thats easy enough to understand.
A good accurate summary, yes! 
There will hardly be a situation where you'll need to install through .bin or .tar.gz or .deb since APT/Synaptic handle the job so well. You'll basically need .deb, .tar.gz, or a binary executable mainly if you want to install proprietary software or the software is yet to be or no longer supported. In many cases proprietary software can be installed using Add/Remove.

---

### Post by ITdrummer on 2007-07-16
thanks for your help!

  *Thread closed*

---

