---
title: "k3b fails to start"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by hlekat on 2008-02-20
i dont know why but k3b fails to starts.

the only think i remeber is that i made somes complete unistalls for video players software (totme, vlc).

i also made complete unistall to k3b and then i installed it again.

any ideas?

---

### Post by jan quark on 2008-02-20
start k3b trough the terminal

just type
```

k3b
```

into it 

do you get any error messages ? post them here please

---

### Post by hlekat on 2008-02-20
~$ k3b
trying to create local folder /home/jp/.kde/share: Permission denied
trying to create local folder /home/jp/.kde/share: Permission denied
trying to create local folder /home/jp/.kde/share: Permission denied
trying to create local folder /home/jp/.kde/socket-jp-desktop: Permission denied
trying to create local folder /home/jp/.kde/socket-jp-desktop: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/jp/.kde/socket-jp-desktop/kdeinit__0'
ERROR: KUniqueApplication: Can't setup DCOP communication.



i can run it by typing sudo k3b.

---

### Post by hlekat on 2008-02-21
no one?

---

### Post by FrozenFox on 2008-02-21
Wow, that's a pretty strange permission problem. Please open synaptic and remove k3b, press refresh, then reinstall k3b. If it still doesn't work, please give us the output of the command groups in the terminal.

---

### Post by hlekat on 2008-02-21
do i need any special command to see this output?

if i type k3b in the terminal it has the same results as i gave in the post #3 (after the reinstallation).

edit: is there any problem if i change the shortcut to : sudo k3b %U ??

because with admin privilleges it opens.

---

### Post by FrozenFox on 2008-02-21
If you are on normal ubuntu, you can use gksu k3b. If on kde, you can use kdesu k3b. But you shouldn't have to be using the password to use k3b.

And all you have to do is open the terminal under accessories and type groups. This shows what groups you are in, and I'm betting for some strange reason you're not in the one necessary for k3b.

---

### Post by stchman on 2008-02-21
> **hlekat said:**
> ~$ k3b
trying to create local folder /home/jp/.kde/share: Permission denied
trying to create local folder /home/jp/.kde/share: Permission denied
trying to create local folder /home/jp/.kde/share: Permission denied
trying to create local folder /home/jp/.kde/socket-jp-desktop: Permission denied
trying to create local folder /home/jp/.kde/socket-jp-desktop: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/jp/.kde/socket-jp-desktop/kdeinit__0'
ERROR: KUniqueApplication: Can't setup DCOP communication.



i can run it by typing sudo k3b.

Do this in a terminal.

```
sudo chown -R $USER:$USER ~/.kde
chmod -R 755 ~/.kde

```

This will return permission of the ~/.kde folder to the user logged in.  I have seen this happen before.

---

### Post by wpshooter on 2008-02-24
> **stchman said:**
> Do this in a terminal.

```
sudo chown -R $USER:$USER ~/.kde
chmod -R 755 ~/.kde

```

This will return permission of the ~/.kde folder to the user logged in.  I have seen this happen before.

I had the very same problem today when I tried to install K3b on my brother-in-laws Gutsy computer.  The installation seemed to go fine but yet the K3b program would not open.

Is the above a solutions for this problem and more importantly why is this apparent permissions problem occuring ???

Thanks.

---

