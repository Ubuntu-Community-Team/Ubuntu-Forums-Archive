---
title: "No Normal Visual effects."
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by LouisChappell on 2008-01-02
Hi, I'm very new to linux and had a real battle with my broadcom wireless, the new flash and a few other things. Got all those sorted but want to customise my desktop now. 
As the title says I can't get normal visual effects from the preferences>appearance. As it is through the GUI I can't give an error report and would be unsure anyhow if it was through terminal command.
I've had a thorough search to no avail and I'd really appreciate any help, Sorry for the long windedness of my post.

My card is an ATI Radeon (fglrx?) and I have 512 RAM if any of that helps.

---

### Post by (((X))) on 2008-01-02
what do you mean by ´normal´:-o

---

### Post by cecure on 2008-01-02
How do you know that the effects are not working... do you get an error message or is there a specific effect that you notice is not working?

---

### Post by Ub1476 on 2008-01-02
Post the output of:

```
lspci | grep VGA

compiz
```

---

### Post by (((X))) on 2008-01-02
never mind, I know what you mean by normal visual effects :)
Enable propriatory drivers, see it that helps

---

### Post by LouisChappell on 2008-01-02
I get a message saying: The Composite extension is not available.
Also when I try to execute compiz it flashes up for a millisecondish then goes away again.

---

### Post by LouisChappell on 2008-01-02
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955
is the readout of:
lspci | grep VGA

compiz

thanks so much for the quick replies!!!

---

### Post by Ub1476 on 2008-01-02
You need to install XGL.

```
sudo apt-get install xserver-xgl
```

Make sure the drivers are enabled in System>Administration>Restricted Driver Manager.

---

### Post by LouisChappell on 2008-01-02
@UB1476 I did that to no avail, Still can't get compiz or normal on, same error. Do I need to reboot? I'll try that just in case.
Cheers.

---

### Post by Ub1476 on 2008-01-02
Yes, you need to logout and login for XGL to take effect.

---

### Post by LouisChappell on 2008-01-02
Thanks for that, the normal setting works now! But still nothing on the compiz front, any ideas?

I've typed compiz in the terminal and it seems to be doing something at least :) but been at this for a few minutes now:

louis@ubuntu:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

I'll give it a few more mins.

---

### Post by cecure on 2008-01-02
Have you tried installing the ATI drivers, try to install the ATI binary X.org drivers from Applications>Add/Remove...  If that doesnt work take a look at this:[http://ubuntuforums.org/showthread.php?t=341149]("http://ubuntuforums.org/showthread.php?t=341149")
cheers

---

### Post by Ub1476 on 2008-01-02
Normal effects is Compiz (acutally Compiz-Fusion), it just doesn't have so many effects enabled. To customize Compiz-Fusion install ccsm from terminal:

```
sudo apt-get install compizconfig-settings-manager
```

or Add/remove

Applications>Search>Advanced Desktop Effects.

Remember to set Visual Effects to "custom" after it's installed to tweak it:)

Good luck!

---

### Post by LouisChappell on 2008-01-02
erm not too sure what i did there but the minimise, maximise etc bar has dissapeared as well as the two taskbars. I closed the terminal that i had started with the last post before it had finished and can't get out of it or start a new terminal. tried ctrl+c. HELP PLEASE I'M STUCK NOW!!! I usually do things like this :(

---

### Post by Ub1476 on 2008-01-02
Logout:

```
<Control>+<Alt>+<Backspace>
```

Login.

---

### Post by LouisChappell on 2008-01-02
HA HA thanks SOOOOOO much I thought I'd ruined everything! It said: Nautilus can't be used now, due to an unexpected error. 
When i logged back in is that bad? Sorry for being such a burden I should've just stuck with the out the box package!

---

### Post by LouisChappell on 2008-01-02
It's all ok now thanks very much for persevering with me. I am eternally grateful to all who've helped me in my most rediculous noobish moment ever. If there's anything I can ever do for anyone especially Ub1476 I will oblige.

---

### Post by Ub1476 on 2008-01-02
You can try to reinstall Nautilus (file-manager):

```
sudo apt-get install nautilus --reinstall
```

There are also a bunch of other file-managers available, like Thunar, Dolphin, PcManFm etc. Take a look [here]("http://www.psychocats.net/ubuntu/nonautilusplease").

EDIT: Ok, you got it sorted out. The best way to help is to help other Ubuntu newbies with your experience. That way this forum can stay the best community ever (just check the forum replies)! Happy 'bunting.

---

