---
title: "[SOLVED] Deleting a &amp;quot;locked&amp;quot; folder on my desktop"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by TaoBoogie on 2007-09-12
Hello
I'm hoping this is just a quickie question.
During a couple of failed attempts to install RealPlayer on my new Feisty Fawn I ended up with a "locked" folder on my desktop called "Real Player".
Now that I have successfully installed RealPlayer using another method I would like to delete this folder, but can't as it is locked. I get the message "Error while moving. Cannot move /home/tao/...RealPlayer to the deleted items folder because you do not have permissions to change it or its parent folder."

How should I go about deleting it?
Thanks in advance

---

### Post by the.phantom on 2007-09-12
open the terminal
gksudo nautilus

navigate to that folder and you should be able to delete it 

that way you have root powers

just a Ubuntu lightweight here ;-D
mitch

---

### Post by Tautoa on 2007-09-12
Or...
Open the terminal
Type "sudo rm -R /path/to/folder"
and type your password

But with either method, be careful, sudo/gksudo gives you the power to do some real damage.

In fact, as much as I like to use the terminal, I would suggest that you use the.phantom's method. Less likely to do something wrong with the GUI :)

---

### Post by TaoBoogie on 2007-09-12
Thanks for the replies
I tried your suggestion first the.phantom and I got this message

> tao@tao-laptop:~$ gksudo nautilus

(nautilus:12730): GnomeUI-WARNING **: While connecting to session manager:

Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Initializing gnome-mount extension

ALSA lib pcm_dmix.c:914:(snd_pcm_dmix_open) unable to open slave

Then I tried your method Tautoa and got this response;

> tao@tao-laptop:~$ sudo rm -R /desktop/RealPlayer

Password:

rm: cannot remove `/desktop/RealPlayer': No such file or directory

tao@tao-laptop:~$ 


I am a complete newby in using the terminal so forgive me if I have missed an obvious step
Do I have to navigate to the folder from within the terminal window?

---

### Post by rsambuca on 2007-09-12
```
sudo rm -R ~/Desktop/RealPlayer

```

---

### Post by bsharp on 2007-09-12
the commands in the terminal is case-sensitive, you typed 

```
sudo rm -R /**desktop**/RealPlayer
```

when it should be 

```
sudo rm -R ~/Desktop/RealPlayer
```

Also, the slash in front of desktop is pointing it to /Desktop when actually it needs to be pointing to /home/your_user_name/Desktop....the tilde (~) is a shorthand meaning your home folder (/home/your_user_name)

*edit-dangit rsambuca, you are faster on the draw than me :(

---

### Post by rsambuca on 2007-09-12
> **bsharp said:**
> *edit-dangit rsambuca, you are faster on the draw than me :(
It wasn't really fair!  You took the time to explain everything, which I should have.

---

### Post by TaoBoogie on 2007-09-12
Excellent stuff. The offending folder has now evaporated into the ether.
Thank you both bsharp and rsambuca.
I'd love to learn more terminal commands and language as it appears to be essential for good Ubuntu computer management I'll go and look for some learning resources on the subject. Do you have any links to learning this you may care to share?
I am just starting to get used to the file structure it seems a little like DOS which I used a little bit back in the Cretaceous period I think it was.
Thanks once again.

---

### Post by rsambuca on 2007-09-12
Actually, it is surprising how little you are required to use the terminal nowadays, unless you want to.  With these latest versions of ubuntu, a lot of users *never* use the terminal.  However, if you are determined to exercise your fingers, here are a couple of links to help you get started!

[http://www.linuxhq.com/guides/LUG/guide.html](http://www.linuxhq.com/guides/LUG/guide.html)

[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

---

### Post by TaoBoogie on 2007-09-12
Thanks once again rsambuca I've bookmarked the links to check out tomorrow as it is getting rather late here in Blighty. I've been so very impressed by the way people like yourself have given their time and expertise to help newcomers like myself.
I can only hope one day to repay the genorosity. 
Slainte

---

