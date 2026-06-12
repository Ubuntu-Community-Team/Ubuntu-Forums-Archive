---
title: "Gnomebaker on 6.06?"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by anubis2814 on 2006-07-11
hello, I am a newby and installed Ubuntu 6.06 and cannot load any version of Gnomebaker on my system, can someone please help?

---

### Post by deadgobby on 2006-07-11
> **anubis2814 said:**
> hello, I am a newby and installed Ubuntu 6.06 and cannot load any version of Gnomebaker on my system, can someone please help?
Have you tried to install K3B? Have you tried to install Automatix?
[http://ubuntuforums.org/showthread.php?t=177646&highlight=Automatix](http://ubuntuforums.org/showthread.php?t=177646&highlight=Automatix)

---

### Post by anubis2814 on 2006-07-11
for all 3 programs I got the error message
configure: error: no acceptable C compiler found in $PATH
Any idea how to fix that?

---

### Post by deadgobby on 2006-07-12
> **anubis2814 said:**
> for all 3 programs I got the error message
configure: error: no acceptable C compiler found in $PATH
Any idea how to fix that?
Open up your terminal and type or copy and paste.

sudo apt-get install build-essential

---

### Post by Brunellus on 2006-07-12
> **anubis2814 said:**
> hello, I am a newby and installed Ubuntu 6.06 and cannot load any version of Gnomebaker on my system, can someone please help?
you should not have to be compiling gnomebaker!  it's in the 'universe' repository.

[http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic](http://monkeyblog.org/ubuntu/installing/#installing_with_synaptic)

---

### Post by Miguel on 2006-07-12
Hi anubis,

I suppose you have gone to a site and downloaded something like gnomebaker_0.5.1.tar.gz. Then you uncompressed it and typed in a terminal ./configure, make, sudo make install. If you did it... well you did exactly the same as I when I switched to linux.

Linux has a cool way to install programs, using what's called a "repository". You can see it by clicking in System -> Administration -> Synaptic package manager. This will ask for your password. Do you see those lots of apps? Just double-click on them, hit apply and the program will automatically download and configure the program for you. 

How would we install gnomebaker? Run synaptic. Once there, use the search function with gnomebaker (either "name" or "name and description"). Just double-click on gnomebaker (or right-click plus "install"). It may ask you to install another programs. These are usually smaller, but are needed by gnomebaker to function properly (technical name: dependencies). Click "apply" and you're done (well, after it downloads and install the program, of course).

*Note:* If a search for gnomebaker doesn't report anything, click on Configuration -> Repositories. Make sure to mark "universe" (you can also mark multiverse if you want, though it includes software that is legal in Europe but Illegal in the U.S.). After that "Refresh" or "Reload" the package list. Performing the search again should be satisfactory.

Hope it helps ;)

---

### Post by Jagot on 2006-07-12
And remember that GnomeBaker is in the universe repo so you'll need to enable that:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by tombeharrell on 2006-07-17
I've got a problem with gnomebaker on my 6.06 machine (upgraded from hoary through breezy). Gnomebaker was installed from the repository and I have just reinstalled it to see if it improves, but it still won't start. Running from a terminal shows:

GTK Accessibility Module initialized
GThread-ERROR **: GThread system may only be initialized once.
aborting...
Aborted

Any ideas?

---

### Post by koshari on 2006-07-17
see if theres not an instance sleeping on the system already, 

or reboot the machine and see if it helps.

---

### Post by tombeharrell on 2006-07-17
It doesn't seem to be running and I tried rebooting just in case, same thing though.

---

