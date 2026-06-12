---
title: "Where do I find the Root Terminal?"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by Goober on 2005-10-17
Ok guys, I need to find the "Root Terminal".  I am trying to install VMware, and it asks me for the "Super User", but I can't find the Root Terminal?  Can anybody help me?  It seems so obvious, yet . . .

Thanks in advance.

---

### Post by Murgle on 2005-10-17
in any terminal type the sudo command and you will have root permissions for that command once you type your normal users password

---

### Post by Murgle on 2005-10-17
also if you really need a term ran as root you can go to Applications -> System Tools -> Run as a different user and then type xterm or gnome-term whatever terminal you prefer

---

### Post by migueljacq on 2005-10-17
If you don't want to type sudo and use the direct root terminal, you can also follow these instructions:
Go to Applications >> System Tools >> Applications Menu Editor

In the Menu Editor, go to 'System Tools' and then press in the button next to 'Root Terminal' that is currently unpressed. Close Menu Editor and the root terminal can now be found under Applications >> System Tools >> Root Terminal.

Miguel

---

### Post by Goober on 2005-10-17
[QUOTE=migueljacq]If you don't want to type sudo and use the direct root terminal, you can also follow these instructions:
Go to Applications >> System Tools >> Applications Menu Editor

In the Menu Editor, go to 'System Tools' and then press in the button next to 'Root Terminal' that is currently unpressed. Close Menu Editor and the root terminal can now be found under Applications >> System Tools >> Root Terminal.

Miguel[/QUOTE]

Ok, I successfully installed it, but it doesn't work.  When I clicked on it after I installed it, well, it says its Opening, the little spinning thing on the mouse spins, but then it simply doesn't open.  Any suggestions?

---

### Post by ecobuntu on 2005-10-17
do you have the appropriate drivers?  I thought you needed drivers with VMWare 5.0 and the 2.6 kernel

---

### Post by ecobuntu on 2005-10-17
[QUOTE=Murgle]in any terminal type the sudo command and you will have root permissions for that command once you type your normal users password[/QUOTE]

Alternatively

sudo -s 

will bring you to the root terminal!

---

### Post by Vicsun on 2005-10-17
[QUOTE=Goober]Ok, I successfully installed it, but it doesn't work.  When I clicked on it after I installed it, well, it says its Opening, the little spinning thing on the mouse spins, but then it simply doesn't open.  Any suggestions?[/QUOTE]
Try prefacing all the commands which should be otherwise put in the root terminal with *sudo*

---

### Post by Goober on 2005-10-17
[QUOTE=Vicsun]Try prefacing all the commands which should be otherwise put in the root terminal with *sudo*[/QUOTE]

Yes, I know how to do that, but the VMware install asked me to change to my Super User account, which I assume is my Root Terminal, and continue with the steps.  Well, I am not having luck with that.

And I tried the "sudo -s" thing, it currently says this:

```
nathan13@nathan13:~$ sudo -s

```

And the cursor is on the next line blinking, doing nothing . . . unless it takes a couple minutes to get to the Root Terminal account, which doesn't make much sense . . .

And I have no clue if I have the right Drivers, I am simply following the instructions on the VMware Website, and a thread in these Forums somewhere.

Thanks for the continued assistance, btw.

---

### Post by ecobuntu on 2005-10-17
[QUOTE=Goober]Yes, I know how to do that, but the VMware install asked me to change to my Super User account, which I assume is my Root Terminal, and continue with the steps.  Well, I am not having luck with that.

And I tried the "sudo -s" thing, it currently says this:

```
nathan13@nathan13:~$ sudo -s

```


Did you hit enter?  When I hit enter I get this.

```
chris@ubuntu:~$ sudo -s
Password:
root@ubuntu:~#

```

---

### Post by Murgle on 2005-10-17
alternatly to get a root bash term you can type 'sudo bash' and that is the same as typing su but you only need to know the user password

---

### Post by ecobuntu on 2005-10-17
[QUOTE=Murgle]alternatly to get a root bash term you can type 'sudo bash' and that is the same as typing su but you only need to know the user password[/QUOTE]

though the sudo/su password is the same as the users by default.

---

### Post by migueljacq on 2005-10-17
Sounds like he did press enter, hence the 'and the cursur is on the next line blinking'
It's strange. I installed breezy on a formatted partition (i.e, no pre-installed drivers present) and my root terminal works. So it would suggest that the Breezy installation would install everything necessary to run the root terminal. 
So by process of elimination, could it be the method of installation you used?
*shrug*
Miguel

---

### Post by Goober on 2005-10-17
Yes, I typed in "sudo -s", pressed enter, and, well, its currently sitting there, blinking away at me.

sudo bash does the exact same thing . . . very, very mysterious . . .

Well, I'm gonna file a bug report after rebooting, thanks for the help guys.

---

### Post by Goober on 2005-10-18
Well.  It's the damndest thing, but I just restarted my computer, and, lo and behold, the sudo -s worked perfectly, allowing me to enter the root.

I guess a restart is needed every so often for Ubuntu . . . I've gotten quite out of habit since I stopped using XP, lol.

---

### Post by migueljacq on 2005-10-18
[QUOTE=Goober]Well.  It's the damndest thing, but I just restarted my computer, and, lo and behold, the sudo -s worked perfectly, allowing me to enter the root.

I guess a restart is needed every so often for Ubuntu . . . I've gotten quite out of habit since I stopped using XP, lol.[/QUOTE]

Reminds me of the time when all of a sudden my modem wouldn't work. I pulled the line out and plugged it straight back in and bingo!
Glad it worked :)

---

