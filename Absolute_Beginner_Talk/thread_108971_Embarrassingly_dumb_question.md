---
title: "Embarrassingly dumb question"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by harveyvan on 2005-12-27
I've wanted to try some Linux distributions for a while, and about 6 months ago tried Suse.  Didn't take to it;  went back to Windows;  am trying again, but as a pretty raw newbie, and right away I've hit a wall.  (If this is a FAQ, please don't yell:  just point me to the page.)

I've installed Ubuntu 5.10, and the boot loader comes up.  I chose to boot to Ubuntu;  got a command-line like screen;  entered my user name and user password.  The next line comes up with username@uburntumyinstall, followed by a dollar sign;  it's obviously eagerly awaiting my input. 

I have *no* idea what to do next -- everything I try (my password again, etc.) gets the response that it's not a "bash" command.  (Whatever that is....told you I'm new.)

So:  at the command prompt after username@ubuntumyinstall, what comes next to get it to boot?

Thanks in advance for being patient.

---

### Post by Glottis on 2005-12-27
check the sessions in the log in prompt. You should have somehting like Gnome, KDE, Terminal. 

Sounds like your logging into terminal. Try Gnome instead :)

---

### Post by bob phillips on 2005-12-27
at this point, try typing
```
sudo gdm
```
followed by your password

you'll probably get a graphical login screen again, and at this point you can type in username/password again, and then you're up and running

---

### Post by akniss on 2005-12-27
[QUOTE=harveyvan]I've wanted to try some Linux distributions for a while, and about 6 months ago tried Suse.  Didn't take to it;  went back to Windows;  am trying again, but as a pretty raw newbie, and right away I've hit a wall.  (If this is a FAQ, please don't yell:  just point me to the page.)

I've installed Ubuntu 5.10, and the boot loader comes up.  I chose to boot to Ubuntu;  got a command-line like screen;  entered my user name and user password.  The next line comes up with username@uburntumyinstall, followed by a dollar sign;  it's obviously eagerly awaiting my input. 

I have *no* idea what to do next -- everything I try (my password again, etc.) gets the response that it's not a "bash" command.  (Whatever that is....told you I'm new.)

So:  at the command prompt after username@ubuntumyinstall, what comes next to get it to boot?

Thanks in advance for being patient.[/QUOTE]


You've already booted into the operating system.  Try using startx to get a GUI.
```
startx
```

---

### Post by ardchoille on 2005-12-27
Sounds like you've booted into runlevel 3. This is the runlevel I prefer to boot into. you should be able to get a desktop environment by typing the below text and pressing the enter key:

```

startx

```

---

### Post by harveyvan on 2005-12-27
Many thanks for the fast responses -- I'll try the various suggestions, and see what pops up!

Thanks again.

---

### Post by harveyvan on 2005-12-27
Alas.  Those didn't work.

For each of the commands I get "startx [or gdm] command not found", and the "~$" sign reappears (doubtless in the eager expectation that I know what to type next).

Glottis -- you mentioned about booting into Gnome (or KDE) instead of terminal;  I don't see that as a boot option, but do you mean at *boot up*, or when the "~$" prompt appears?

---

### Post by steve.horsley on 2005-12-27
[QUOTE=harveyvan]Many thanks for the fast responses -- I'll try the various suggestions, and see what pops up!

Thanks again.[/QUOTE]

Ubuntu should normally give you a graphical (brown) login screen. Come back here with the results either way and we'll see how to fix it up. If either **startx** or **sudo gdm** gives you a bunch of error messages, try to post them here so we can figure out what's wrong. If **startx** and **sudo gdm** work, we can look at getting gdm to run at startup as it should.

---

### Post by harveyvan on 2005-12-27
[QUOTE=steve.horsley]Ubuntu should normally give you a graphical (brown) login screen. Come back here with the results either way and we'll see how to fix it up. If either **startx** or **sudo gdm** gives you a bunch of error messages, try to post them here so we can figure out what's wrong. If **startx** and **sudo gdm** work, we can look at getting gdm to run at startup as it should.[/QUOTE]

I'm certainly not getting any graphical login screen:  just a white-on-black, DOS-like command line screen.

The error message for "startx" is "-bash startx command not found:~$";  with "sudo gdm", I get another password prompt, then "sudo gdm command not found?~$".

Maybe I'll try resintalling ubuntu from the CD again...

---

### Post by cbudden on 2005-12-27
I think you have done just a server install, which leaves out the GUI.  Once you are at the username@ubuntu $ screen, type
```

sudo apt-get install ubuntu-desktop

```

providing your connected to the internet.

HTH

Chris

---

### Post by ardchoille on 2005-12-27
[QUOTE=cbudden]I think you have done just a server install, which leaves out the GUI.  Once you are at the username@ubuntu $ screen, type
```

sudo apt-get install ubuntu-desktop

```

providing your connected to the internet.

HTH

Chris[/QUOTE]
That could very well be, I hadn't thought of that.

---

### Post by Rinzwind on 2005-12-27
```
sudo apt-get install ubuntu-desktop
```installs Gnome and ```
sudo apt-get install kubuntu-desktop
```

if you want KDE.

Do both and you get kde and gnome installed.

2 questions:
are you sure the install finished without errors?
and -did- you do a server install?

---

### Post by bob phillips on 2005-12-27
if you did do a server install, 'cause it's a slowish machine, you could try XFCE as a reduced overheads option ```
sudo apt-get install xubuntu-desktop
```

---

### Post by harveyvan on 2005-12-27
Must have been the "server only" problem -- I've reinstalled from the disk (boy, was *that* different to the first time), and I AM NOW POSTING FROM UBUNTU!

Yay!

Thanks for the responses;  I have a feeling this won't be my final post, though!

---

### Post by Iandefor on 2005-12-27
> Thanks for the responses;  I have a feeling this won't be my final post, though!

the first problem is rarely the last :).

---

