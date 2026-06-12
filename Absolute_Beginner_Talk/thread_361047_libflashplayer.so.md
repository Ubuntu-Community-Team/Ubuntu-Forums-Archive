---
title: "libflashplayer.so"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by BJinMontreal on 2007-02-13
I am trying to install flash player 9 and have received the error message:

chmod: cannot access '/home/.mozilla/plugins/libflashplayer.so'  No such file or directory

Where can I get the file(s) I need to complete this installation?

Thanks
BJ

---

### Post by taurus on 2007-02-13
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by BJinMontreal on 2007-02-13
Thanks - that was a heck of a lot easier than the instructions on the Adobe site.  I installed Ubuntu 6.06 on Sunday and have been trying to work my way through it without any manuals, etc. - so don't be surprised to see more questions in the future.  I think this community help forum is going to be my best learning tool.
BJ

---

### Post by taurus on 2007-02-13
People here are more than eager to help you so if you have a question, search for an answer first and if you can't find any, create a thread.

Good luck and have fun.

---

### Post by BJinMontreal on 2007-02-13
Thanks again Taurus,
The Flash Player works now, but I seem to be having trouble listening to the radio - it is telling me that additional plugins are required. I don't suppose you have a link to getting the Linux version of RealPlayer (that didn't work from their site either)?
BJ

---

### Post by aysiu on 2007-02-14
**Step 1**: Enable extra repositories:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

**Step 2**: ```
sudo aptitude update
sudo aptitude install realplayer
```

---

### Post by nalioth on 2007-02-14
If you add this to your sources.list, and update, you'll have flashplayer, realplayer, opera web browser and some more stuff
```

deb http://archive.canonical.com/ubuntu edgy-commercial main
```

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by BJinMontreal on 2007-02-14
Thanks aysiu and nalioth.  I must admit that asking questions, no matter how simple they seem and finding really helpful information posted within minutes, and sometimes even hours is beyond anything I ever experienced trying to get technical help with Windows problems.
BJ

---

### Post by BJinMontreal on 2007-02-14
Now I need a bit more help - where do I find sources.list so I can edit / update it?

I should mention - I only installed Linux on Sunday and am still trying to familiarize myself with it and what it can do.
Thanks
BJ

---

### Post by Maestro23 on 2007-02-14
> **BJinMontreal said:**
> Now I need a bit more help - where do I find sources.list so I can edit / update it?

I should mention - I only installed Linux on Sunday and am still trying to familiarize myself with it and what it can do.
Thanks
BJ

/etc/apt/sources.list

Use an editor(vi, gedit, nano, vim, mousepad, etc..) to open the file and edit it.

Ex: I use nano.

> sudo nano -B /etc/apt/sources.list 
(-B) makes a backup copy for me before I actually edit the file.

Make your changes then save, exit.

Links to get you feet wet with linux:

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Install Anything: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
                        [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Good luck.

---

### Post by BJinMontreal on 2007-02-14
Where in the file sources.list would I add the line:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

at the beginning or end - or does it matter?

Also, when I first tried to save the changed file I was notified it was read-only - so I didn't. Can I save it anyway with the added line
BJ

---

### Post by Maestro23 on 2007-02-14
> **BJinMontreal said:**
> Where in the file sources.list would I add the line:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

at the beginning or end - or does it matter?

Also, when I first tried to save the changed file I was notified it was read-only - so I didn't. Can I save it anyway with the added line
BJ

I would just put it at the end, with a comment about what it's for.

##This is for.....
deb http:.....

Don't forget to use "sudo" in front of your terminal command because you are trying to alter a file owned by "root".

---

### Post by BJinMontreal on 2007-02-15
I've amended my sources.list file but I am still getting an error message when I try to connect to an internet radio station.  Any suggestions?
BJ

---

