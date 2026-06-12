---
title: "how do you install things from disk?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by makinde on 2007-07-10
I realy don't know how, I open up the disk and copy the setup but not even that works

---

### Post by wthanna on 2007-07-10
Give us a little more detail.  What is it you are trying to install? Is this a windows application? An Ubuntu install CD? An .exe file you are trying to run?

---

### Post by aysiu on 2007-07-10
Any special reason you're installing from disk?

What disk are you using by the way?

Most of the time, software installation is done over the internet:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by makinde on 2007-07-10
I'm trying to install a game called guildwars

---

### Post by aysiu on 2007-07-10
Is it a Windows-only game? Or is it made for Linux?

In the meantime, check out [this link](http://ubuntuforums.org/showthread.php?t=283122).

---

### Post by makinde on 2007-07-10
i think it's windows only but according to the wine website it works on it

---

### Post by twiceasworn on 2007-07-10
If you are using wine all you would need to do is 

```
wine *installer.exe*
```

obviously replace installer.exe with whatever the setup/install file is.   It should proceed like a normal windows program install after that.

This is all assuming that you have installed wine...


EDIT:  I suppose it is important to note that you must first navigate to the directory where the file is before executing the said command.

---

### Post by aysiu on 2007-07-10
I'd seriously suggest you take a look at the link I posted earlier.

---

### Post by makinde on 2007-07-10
> **aysiu said:**
> I'd seriously suggest you take a look at the link I posted earlier.
did, but I didn't realy understand

---

### Post by aysiu on 2007-07-10
Okay. We'll take it one step at a time.

Are you using 32-bit Ubuntu or 64-bit Ubuntu?

---

### Post by makinde on 2007-07-11
32 bit

---

### Post by aysiu on 2007-07-11
Download to your desktop the first link at the bottom of [the post I linked to earlier.](http://ubuntuforums.org/showpost.php?p=1653894&postcount=1)

You should now have a file on your desktop called *winebuild.sh*.

Paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cd ~/Desktop
sh winebuild.sh
```

---

### Post by makinde on 2007-07-11
yay! it's patching now! one more question, If wine is required for this to work, where is wine? I can't find it on my programs menu but I must have it because guild wars is working

---

### Post by makinde on 2007-07-11
ok guildwars loaded but it doesn't work. It basicly freezes and only moves every 20 seconds, any way to solve this?

---

### Post by Nekiruhs on 2007-07-11
> **makinde said:**
> yay! it's patching now! one more question, If wine is required for this to work, where is wine? I can't find it on my programs menu but I must have it because guild wars is working
Wine isn't a normal application. It "reads" windows programs and trys to tell Linux how to run them. Its more of a compatibility layer then an application.

---

### Post by makinde on 2007-07-11
> **Nekiruhs said:**
> Wine isn't a normal application. It "reads" windows programs and trys to tell Linux how to run them. Its more of a compatibility layer then an application.

strange thing is that I recall somewhere on the forums where you can click "open with" on a certain application and wine would be there

---

