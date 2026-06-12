---
title: "Home ownership"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-05-26
On bootup, Edgy reports that my .dmrc is being ignored, and suggests my Home directory should be owned by myself.

It seems like root owns my Home directory & I do not

How do I take ownership of my Home directory?

TBH I'm only pursuing this because it complains every boot. Everything seems to work just fine.

---

### Post by earobinson on 2007-05-26
```
chown <yourusername>:<yourusername> <file you want to change>
``` eg > earobinson@NaN:~$ sudo chown earobinson:earobinson test
 note you can try ```
man chown
``` for more info.

---

### Post by taurus on 2007-05-26
At GUI login screen, press <Ctrl><Alt>F2 to get into a console.  Log in with your name and password.  Then, at the prompt, run

```
sudo chown **username**:**username** .dmrc
```
Replace **username** with your actual log in name.

Log out and press <Alt>F7 to get back to GUI login screen again.  Now, log in and see if you still see that error message about your .dmrc.

---

### Post by earobinson on 2007-05-26
Im pretty sure in tarus's example you would need to add a -r to the chown since its a folder and you want to recursively apply the new permissions.

Edit: Im a moron and completely wrong.

---

### Post by taurus on 2007-05-26
~/.dmrc is not a directory, it's a file.

Look in your $HOME account.

```
ls -la ~
```

---

### Post by earobinson on 2007-05-26
> **taurus said:**
> ~/.dmrc is not a directory, it's a file.

Look in your $HOME account.

```
ls -la ~
```
oops my bad /blush. At least I got it right the first time.

---

### Post by ecs_pf5 on 2007-05-26
Cheers peeps.

The exact text of the error was:

> 
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writeable by other users.


You guys' suggestions have now stopped the error from popping up. Thanks :D

The $HOME wasn't owned by <username> and the .dmrc file wasn't CHMOD 644 for some reason.

---

### Post by taurus on 2007-05-26
Any change you used sudo with gedit or nautilus before?

---

### Post by ecs_pf5 on 2007-05-26
I was recently trying to install nspluginwrapper & 32-bit flash, to get my 64-bit system to play flash games. I was also hacking around in the bootloader config files, in both cases I recall sudoing quite a bit and using gedit.. haven't done much with nautilus though.  To be honest I'm taking the 'try and break it' approach to getting to grips with Ubuntu so anything could have happened ;)

---

### Post by taurus on 2007-05-26
When you run gedit, you should use gksudo since gedit is a GUI text editor and sudo is for a command.  So, "sudo gedit filename" will screw up your ~/.dmrc eventually.  Next time, use

```
**gksudo** gedit filename
```

---

### Post by ecs_pf5 on 2007-05-26
okay cheers Taurus. I'm gonna start noting these things down on a wallchart :lol:

---

