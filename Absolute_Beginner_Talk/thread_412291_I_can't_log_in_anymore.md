---
title: "I can't log in anymore"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-04-17
Hello all,


Here is a new trick from Ubuntu. I have just installed Virtual Media with Automatix2. After restarting the PC I entered my username and password at the prompt. 

The following error message came up:

> 
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

[OK]

:confused: :confused: :confused: What is happening to my computer? Any help would be appreciated!!! :)

---

### Post by dbbolton on 2007-04-17
in the lower left corner, click "options > session" and choose "failsafe gnome."

if it works, then there is a probably problem with your start up programs in the regular gnome session.

---

### Post by the8thstar on 2007-04-17
Hmm... That didn't work. I got the exact same message as before and the session sent me back to the splashscreen. 

It bites... the big one.

---

### Post by tonyr1988 on 2007-04-17
Is it possible for you to get to a terminal? If so, try to do these:

> chown *[username]* ~/.dmrc
chmod 644 ~/.dmrc

If either one of those complains about a permissions error (or similar), try them again with "sudo" in the front. Just a guess...

---

### Post by dbbolton on 2007-04-17
> **tonyr1988 said:**
> Is it possible for you to get to a terminal? If so, try to do these:



If either one of those complains about a permissions error (or similar), try them again with "sudo" in the front. Just a guess...
you can do that by choosing "recovery mode" from the GRUB menu

---

### Post by the8thstar on 2007-04-17
Thanks **Tonyr** and **ddbolton**.

Here's the feedback I got from the OS:

Me: chown [username] ~/.dmrc

OS: root/.dmrc no such file or directory

Me: chmod 644 ~/.dmrc

OS: root/.dmrc no such file or directory

:rolleyes: Maybe a raindance would help... or a fresh Windows XP install?

---

### Post by dbbolton on 2007-04-17
when you're logged in as root, ~ is /root instead of /home/[username]

just do those commands but type ```
/home/[username]/.dmrc
``` instead of ~

---

### Post by the8thstar on 2007-04-17
Ok, so I if I'm understanding you correctly, here is the proper syntax I should use:

> chown [username] home/[username]/.dmrc
chmod 644 home/[username]/.dmrc

Is this accurate?

---

### Post by embrodak on 2007-04-18
make sure it's  /home/username  .  The first slash is important.

---

### Post by dbbolton on 2007-04-18
> **the8thstar said:**
> Ok, so I if I'm understanding you correctly, here is the proper syntax I should use:



Is this accurate?

> **embrodak said:**
> make sure it's  /home/username  .  The first slash is important.

yes

---

### Post by the8thstar on 2007-04-18
Thanks for the precision Embrodak. I hope it'll work.

---

### Post by the8thstar on 2007-04-18
It didn't work.

The console didn't even return anything after the commands I entered. I ended up with typing "exit" and I was sent back to the splashscreen

When I entered my password, the message I had in the beginning popped back up.

Questions:

- Can I force the boot with the Ubuntu 6.10 DVD in the drive?
- If I do so, what are the risks?
- Will my programs and documents be erased?

---

### Post by the8thstar on 2007-04-18
I'm replying to myself, which is not a good sign I guess. I'm going to go ahead and reinstall Ubuntu with the disc. I hope that it will work.:confused:

---

### Post by the8thstar on 2007-04-18
Well, all done. I reinstalled the OS. All my settings have been wiped out and I have to start the painstaking job of getting my desktop back to the way it was before the system hung.

I still don't know what went wrong though.

---

### Post by the8thstar on 2007-04-22
[SIZE="6"]**NOOOO!!! It's happened again!!!**[/SIZE]

It seems that my trouble started after I changed the splashscreen. That's very odd. Any great ideas guy?

---

