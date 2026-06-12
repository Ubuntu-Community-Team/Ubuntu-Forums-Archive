---
title: "Grrrr"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by murphyj on 2007-09-05
I am trying to install ndiswrapper. EVERY place you go says to type something in a command line. Would someone please tell me just how the hell you do that?

---

### Post by Vadi on 2007-09-05
Click on applications - terminal.

You'll get a box, that'll have a line that's something like this - *yourname*@[I]yourcomputer. That's called the command line.

---

### Post by murphyj on 2007-09-05
I extraced to the desktop. It does not seem to be structured even similarly to DOS. How do you get there with a command line if it doesn't even know what C: is? I can't run C:/dir.

---

### Post by rsd-17 on 2007-09-05
> **murphyj said:**
> I extraced to the desktop. It does not seem to be structured even similarly to DOS. How do you get there with a command line if it doesn't even know what C: is? I can't run C:/dir.

There's no C: on a *nix system.

Once you have opened a terminal window you can type **pwd**
at the prompt and hit enter. The shell will respond with your current working directory, e.g. **/home/yourusername**
You can then type **cd Desktop** and then **ls** and you should see your extracted package listed (if you did indeed extract it to the desktop.)  Note that directory and file names are case-sensitive.

In *nix systems ls is roughly equivalent to dir. There are lots of other differences between DOS/Windows and *nix systems, for instance in *nix we use forward slashes instead of backward slashes in directory paths. Surely you didn't expect Ubuntu to be identical to Windows?

..jr

---

### Post by murphyj on 2007-09-05
Thank you for your help. I suppose I did expect the same commands to do the same things. Is there a place I can find a list of commands that are equivilent to del, makedir, ipconfig and stuff like that? How would I change drives if I had more than one hard drive or I want to go to the CD ROM, floppy or pen drive? To install Ndiswrapper, I have to log in as root. I can't do it by switch user, so how do I do that? God I wish I didn't have to use a friggin wireless connection!

---

### Post by Vadi on 2007-09-06
I'm pretty sure you can find a good guide for that on Google.

On in the /media folder are all your drives. USB, floppy, CD, all of them are in there.

And you can just put "sudo" before the ndswrapper command, it'll ask for your pass, and install just fine then. As I understand it, you're temporarily giving root privs to the command you do after sudo. (ie, doing just "nautilus" will launch it normally, by doing "sudo nautilus" will give it root privs)

---

### Post by Steve1961 on 2007-09-06
You might find this link helpfull:

[http://www.computerhope.com/unix.htm](http://www.computerhope.com/unix.htm)

---

### Post by rolnics on 2007-09-06
> **murphyj said:**
> I extraced to the desktop. It does not seem to be structured even similarly to DOS. How do you get there with a command line if it doesn't even know what C: is? I can't run C:/dir.

I thought that when I first looked used terminal, there are similarities I've seen, but unfortunately there's more stuff that's different as mentioned previous. But I'm starting to see how powerful the command line can be, so be patient and bare with it!

> **Vadi said:**
> I'm pretty sure you can find a good guide for that on Google.

I found a good one for me, it actually has some tutorials as well, which might be of use. The site is call [Linuxcommand]("http://www.linuxcommand.org/"), take a look.

---

### Post by Vadi on 2007-09-06
Oh, I actually remember that site! I read it before I got Linux, but prompt forgot about it after I did. Heh, thanks for reminding.

---

