---
title: "Burning CDs/DVDs over the network"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by &#12465;&#12452;&#12488; on 2007-08-02
Is there any software which can make it possible to mount, or at least use, a CD/DVD writer on another computer over the network?

---

### Post by Hospadar on 2007-08-02
if the other machine is a linux/unix machine you could connect to it with ssh (allows you to get a terminal on a remote machine, so you could then open up your fav burning app or do it command line style) it it's windows, it might be possible, but it's gonna be harder.

to use ssh, you'd need to install the ssh host on the machine that has the burner you want to use with something like ```
sudo apt-get install ssh
``` and then on you're machine you'd use a command like ```
ssh <a valid username on the remote machine with the burner>@<the name or ip of the remote machine>
``` then enter the password for the username you used.
eg.
```
ssh luke@luke-desktop
```

This will get you a terminal for the remote machine at which point you could any burning app installed on the remote machine such as ```
serpentine
``` or some other app for burning cd's (there are many to choose from)

Hope this helps, if these directions for ssh don't work for you, you may want to poke around for some ssh tutorials, ssh in general will be able to do what you want I think.

cheers!

---

### Post by Ek0nomik on 2007-08-02
> **Hospadar said:**
> if the other machine is a linux/unix machine you could connect to it with ssh (allows you to get a terminal on a remote machine, so you could then open up your fav burning app or do it command line style) it it's windows, it might be possible, but it's gonna be harder.

to use ssh, you'd need to install the ssh host on the machine that has the burner you want to use with something like ```
sudo apt-get install ssh
``` and then on you're machine you'd use a command like ```
ssh <a valid username on the remote machine with the burner>@<the name or ip of the remote machine>
``` then enter the password for the username you used.
eg.
```
ssh luke@luke-desktop
```

This will get you a terminal for the remote machine at which point you could any burning app installed on the remote machine such as ```
serpentine
``` or some other app for burning cd's (there are many to choose from)

Hope this helps, if these directions for ssh don't work for you, you may want to poke around for some ssh tutorials, ssh in general will be able to do what you want I think.

cheers!

These directions should work just fine, but remember when you issue the command to connect to the remote box via SSH, if you want to run programs graphically you need the X argument.

```
ssh **-X** <a valid username on the remote machine with the burner>@<the name or ip of the remote machine>
```

If the program isn't going to run graphically (you are *only* going to use the console, you don't need the -X)

---

### Post by &#12465;&#12452;&#12488; on 2007-08-11
Thanks a lot, both of you! I had no idea X forwarding through SSH was that easy, now I can happily burn DVDs all day!!!

---

