---
title: "Lost command prompt"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Stefanius on 2007-11-04
Hi there,

I hope someone could help me. I'am running Kubuntu 7.04 and LinuxMC on top of it. The installer of my ATI card broke several times, and a solution was:

```

Sudo mv /bin/sh /bin/SH
sudo ln -s /bin/bash /bin/sh

```

The installer seems to work, and after the installation I had to do a command to bring the bash/dash/sh (Just a newby, dont know the real meaning/the way it works yet) in the original state:

```

sudo mv /bin/SH /bin/sh

```

And now the problem: After tje installation of the driver the system gets weird, so i did a reboot, the last line of code i could never use. When i start Kubuntu, the system stops, dont show a prompt and every command I use does nothing, in the start-up scrips there are some error that he can't fine Apt-get, nut that's logical I think. How can i fix this??

Tnx!
Stef.

---

### Post by amingv on 2007-11-04
Hi,

I'll give you a brief explanation of what happened:

```

sudo mv /bin/sh /bin/SH [COLOR="Blue"]#moved (could almost say "renamed") your /bin/sh to /bin/SH[/COLOR]

sudo ln -s /bin/bash /bin/sh [COLOR="Blue"]#created a link (symbolic pointer) from /bin/bash to /bin/sh[/COLOR]
[COLOR="Blue"]#the file /bin/sh now points to /bin/bash, could almost say they're the same[/COLOR]

sudo mv /bin/SH /bin/sh [COLOR="Blue"]#if I don't misunderstand you, you couldn't run this;[/COLOR]
[COLOR="Blue"]#it's purpose "was" to return SH to it's original state (sh), which you couldn't
#do because you didn't "have" sh in the first place; unlike Win, Linux is case-sensitive
```[/COLOR]

This means you lack the sh file (ouch), thus, no command prompt. But fear not! nothing that can't be solved.

The easiest way to solve it: grab your Kubuntu disc, run the LiveCD and copy these files again (and delete the pointer).

How NOT to make this mistake again:

1. Tempting as it may be, do not rename/move system files, not even capitalizing them, because Linux is case-sensitive.
2. If the command prompt asks you for your root password while doing a command you don't fully understand; STOP, google the command, learn what it does and follow your newly instructed mind, because these "root commands" have global consequences.
3. Most of the things in your /bin directory can be automatically accessed through the console, since they are binaries or scripts. So In this case there was no need to create a pointer to bash in the first place, you could have used instead
```
bash name_of_installer
```
and achieve the same effect, without damage.

---

### Post by nick_h on 2007-11-04
/bin/sh is just a symbolic link to /bin/dash by default.

To restore it, you just need to restore the link with:
```
sudo rm /bin/sh
sudo ln -s /bin/dash /bin/sh
```

---

### Post by Stefanius on 2007-11-04
ok, thanks for your reaction and explaining the code. 

I'am not at home rioght now, so i can't fix it right now, but LinuxMCE has some scrips/extenders especialy for running a MCE. It's not very likely, but not imposible, could one of those files contains these 'custom' commands?

and for the next time your tip was very useful! 

Stef.

---

### Post by Stefanius on 2007-11-06
I tried to copy the files sh (lowercase)  and bash to my /bin/ om the hardrive. But the system  told me i have no permission.When i do:

sudo mv /mnt/sda3/bin/SH /mnt/sda3/bin/sh

(note: this was my temporaly linux partition mount-point during the Live-session)

it seems te work, when i do it again i get an error that SH doesn't exist. So far is everything OK, reboot on the harddrive: there is nothinh changed, the same error.

The configuration connot be lost, there several hours in ot to create the MCE and fill the database etc. An reïnstall isn't really an option:(

---

### Post by nick_h on 2007-11-06
If you have a permission problem make sure you are using sudo.  The **mv** command is for moving (renaming) files.  After the move if you repeat the command you will expect to get a file not found error.

Run the command:
```
ls -al /mnt/sda3/bin/*sh
```
and check that the files **dash** and **bash** exist.

**sh** is normally just a symbolic link to one of these 2 files- **dash** by default.
You could just try and copy one of them to **sh** with:

```
sudo cp /mnt/sda3/bin/dash /mnt/sda3/bin/sh
```

When you get it working you really should just re-create the link as described in my previous post.

---

### Post by amingv on 2007-11-06
Did you delete the old sh file first? I'm not sure, but I think the mv command does not overwrite by default, try this:

```

sudo rm /mnt/sda3/bin/SH [COLOR="Blue"]#assuming /mnt/sda3/ is still the path to your HD[/COLOR]
sudo rm /mnt/sda3/bin/sh

sudo cp /bin/sh /mnt/sda3/bin/sh [COLOR="Blue"]#or, as nick_h pointed out:
#sudo ln -s /mnt/sda3/bin/dash /mnt/sda3/bin/sh[/COLOR]
```

---

