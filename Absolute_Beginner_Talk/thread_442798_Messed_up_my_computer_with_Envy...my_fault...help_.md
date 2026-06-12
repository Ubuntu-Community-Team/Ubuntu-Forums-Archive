---
title: "Messed up my computer with Envy...my fault...help me fix it, please!"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-05-13
I went to install Envy and I selected the wrong nvidia version.  Now all I can get is the text version of ubuntu and I have no idea where to go from there.  I really screwed up!  I'm writing from my hubby's laptop so any info would be great before tomorrow when he has to go to work and take it with him!

I have the nVidia geForce 6200 Limited Edition.

And I have been using ubuntu for less than a week.

---

### Post by taurus on 2007-05-13
There should be a backup copy of your xorg.conf in /etc/X11 before you configured your X with envy so all you have to do is rename it.

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm start
```

---

### Post by overdrank on 2007-05-13
> **bean77 said:**
> I went to install Envy and I selected the wrong nvidia version.  Now all I can get is the text version of ubuntu and I have no idea where to go from there.  I really screwed up!  I'm writing from my hubby's laptop so any info would be great before tomorrow when he has to go to work and take it with him!

I have the nVidia geForce 6200 Limited Edition.

And I have been using ubuntu for less than a week.

Hi *sudo dpkg-reconfigure xserver-xorg* and follow the prompts and you should be ok. Good luck!

To late again !

---

### Post by bean77 on 2007-05-13
OK, I'll go try that.  Before I re-do the nVidia thing, how do I know which version I need?

---

### Post by overdrank on 2007-05-13
> **bean77 said:**
> OK, I'll go try that.  Before I re-do the nVidia thing, how do I know which version I need?

May I ask which version of ubuntu you are using? edgy, feisty?

---

### Post by bean77 on 2007-05-13
Feisty.

---

### Post by bean77 on 2007-05-13
> **overdrank said:**
> Hi *sudo dpkg-reconfigure xserver-xorg* and follow the prompts and you should be ok. Good luck!

To late again !


OK, I did that and am now back at the prompt.  Should I restart?

---

### Post by Happy_Man on 2007-05-13
when you get to the terminal (for that is what the text version is called) enter the following code:
```
sudo dpkg-reconfigure xserver-xorg
```
and answer the questions. When it finishes, press ctrl-alt-backspace and cross your fingers.

EDIT: or, y'know, ```
/etc/init.d/gdm start
``` works just as well....

---

### Post by bean77 on 2007-05-13
Excellent-I'm off to do that now

---

### Post by bean77 on 2007-05-13
Crap-it didn't work.  Now what?

---

### Post by Happy_Man on 2007-05-13
Could you post the output of 
```
cat /etc/X11/xorg.conf
``` please? Along with how big your monitor resolution gets.

---

### Post by taurus on 2007-05-13
When you used envy to install nvidia (or ATI) driver for your graphic card, it made a backup copy of your /etc/X11/xorg.conf.  Why don't you post the output of this command?

```
ls -la /etc/X11
```

---

### Post by bean77 on 2007-05-13
[Here is the monitor I have]("http://www.westinghousedigital.com/details.aspx?itemnum=60")

---

### Post by bean77 on 2007-05-13
Monitor's Horizontal Sync range?  Where do I find that?

---

### Post by bean77 on 2007-05-13
> **Happy_Man said:**
> Could you post the output of 
```
cat /etc/X11/xorg.conf
``` please? Along with how big your monitor resolution gets.

no such file or directory

---

### Post by bean77 on 2007-05-13
> **Happy_Man said:**
> Could you post the output of 
```
cat /etc/X11/xorg.conf
``` please? Along with how big your monitor resolution gets.

Sorry, typo on my part.

I got a whole bunch of stuff but I can only read tha last bit on my screen.

---

### Post by bean77 on 2007-05-13
> **taurus said:**
> When you used envy to install nvidia (or ATI) driver for your graphic card, it made a backup copy of your /etc/X11/xorg.conf.  Why don't you post the output of this command?

```
ls -la /etc/X11
```

I did this and got a page of text, starting with "total 100" and ending with -rw------ 1 root root  614 2007-04-15 07:50 Xwrapper config


(I didn't know the X had to be capitalized)

Sorry I am such a dunce...I am so new at this.  I am determined not to go back to windows.  I really want to learn!

---

