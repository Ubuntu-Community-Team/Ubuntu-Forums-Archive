---
title: "How to log on?"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by CUSTADD on 2006-06-03
I have done searching, both on Google & these forums, but I'm really not even sure what to search for.

I did a hard drive install of Ubuntu, it seemed to be successful, and now when I boot the system, I get a lot of white text on black screen--the boot process I think. It asks for my ubuntu login and password and that I get through successfully.  Then I end up with a prompt that looks like this:  [username]@ubuntu:~$

I don't know how to get past this.  I typed "help" without quotes, but most of the commands went off the screen before I could read them.  What do I do from here?  Thank you in advance for any suggestions!

---

### Post by skinnygmg on 2006-06-03
type startx

---

### Post by taurus on 2006-06-03
At the prompt, type the following command and see if you get can get into Gnome (window manager)...
```

startx

```
Just curious.  How did you install it?  Did you install a server version of did you just hit the enter key at the prompt, after booting from the CD?

---

### Post by CUSTADD on 2006-06-03
Thanks for the suggestion!  You folks in these forums are awesome!

Unfortunately, when I type startx, I get this response:

-bash: startx: command not found

I'm not sure how to answer the question about how I installed it, but I'll try. I downloaded the link that said PC (Intel x86) server install CD. I set my computer to boot from the CD drive (with the Ubuntu ISO image on it). It went through a lot of questions and processes.  Once it said it was finished, it said to remove the CD and reboot the computer. Once I did that, I had the experience I related in my original post.

---

### Post by skinnygmg on 2006-06-03
you need the desktop d/l not the server.  sorry to have to tell you that :(

---

### Post by taurus on 2006-06-03
Since you installed the server one, there is no window manager running on your machine!  So, either install the x86 version over again or run this from a terminal,
```

sudo apt-get install ubuntu-desktop

```
Wait for it to finish and run "startx" again to see what happens...

---

### Post by RRS on 2006-06-03
If you used the server install CD then you need to install a GUI seperately, the desktop CD also offers the option of a server install, hence taurus' question.

I've got to check on the exact command to enter for the gui installation, unless someone else has it handy.

Edit; Thanks taurus. Also typo's

---

### Post by CUSTADD on 2006-06-03
Oh, so I downloaded the wrong one.  It must have changed within the last few weeks, because the live download was called Live somewhere in the name and the Install was called Install somewhere in the name and I was just remembering that and not paying close attention to the name.  

So is it correct that the one called Desktop (instead of Server) is both for Live use and Install?

---

### Post by taurus on 2006-06-03
This is the one you need, ubuntu-6.06-desktop-i386.iso.

---

### Post by skinnygmg on 2006-06-03
[QUOTE=CUSTADD]So is it correct that the one called Desktop (instead of Server) is both for Live use and Install?[/QUOTE]

YES:)

---

### Post by CUSTADD on 2006-06-03
Thank you, thank you!  I can't tell you how appreciative I am for the quick, friendly help!

---

### Post by RRS on 2006-06-03
Seems to me that ```
sudo apt-get install ubuntu-desktop
``` from the command line you've allready got would be quicker and easier.

After entering the command you'll be prompted for a password, type in the one you created during installation (it won't apear as you type) and "enter"

---

