---
title: "edit xorg.conf?"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Tozen on 2006-12-16
Im a total beginner to Xubuntu and I need to ask a basic question.
I have installed Xubuntu 6.10 om a Dell Inspiron 8000, eveything went fine untill I booted the machine, the display looks like three displays in th same time. I read a thread about this and the solution was to edit the "/etc/x11/xorg.conf file"...

Where is it?
How do I do it? 
Can I do it when I'm booting since I cant see the desktop?

I would really appreciate answers to this and especially "basic" answer since Im a TOTAL beginner to linux end xubuntu.

/confused beginner

---

### Post by taurus on 2006-12-16
Boot into recovery mode from GRUB menu and edit it...

```
nano -Bw /etc/X11/xorg.conf
```

---

### Post by Tozen on 2006-12-16
Thanks for your help!
I can get to a promt that says "grub>" but when Im using "nano -Bw /etc/x11/xorg.conf" its a "error 27 unrecognized command"... what am I doing wrong?

---

### Post by taurus on 2006-12-16
That, "grub>", is a GRUB prompt!!!  So you see the options in the menu and the second option is about recovery mode?  When your first boot your machine, press Esc to display the GRUB menu...

---

### Post by linux4me on 2006-12-16
I'm also a total beginner, but I've been where you've been just recently so I will give you the step-by-step.

When you reboot (Ctrl-Alt-Del) if you're at a scrambled screen was my approach, but I'm not sure that's best, get ready to push the Escape key to see the Grub menu mentioned in the previous post. 

Choose the option for recovery mode of your version of Ubuntu using the up/down arrow keys and hit Enter.

Wait for everything to load, and you'll be taken to a command prompt. 

You may want to back up your copy of xorg.conf before you start editing it. You do that with the copy command, "cp". Type:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

and then hit Enter.

Then it's safe to edit your xorg.conf file using the text editor Nano, which works both at the command line and in Terminal. Type:

sudo nano /etc/X11/xorg.conf

and hit Enter.

When you're done making changes to the file, use Ctrl+O (that's the letter, not a zero) to save the file. Nano will default to the existing file name. Press enter to save the changes.

Press Ctrl+X to exit Nano back to the command prompt.

Type "exit" at the command prompt to restart and give your changes a try.

---

### Post by taurus on 2006-12-16
> **linux4me said:**
> I'm also a total beginner, but I've been where you've been just recently so I will give you the step-by-step.

When you reboot (Ctrl-Alt-Del) if you're at a scrambled screen was my approach, but I'm not sure that's best, get ready to push the Escape key to see the Grub menu mentioned in the previous post. 

Choose the option for recovery mode of your version of Ubuntu using the up/down arrow keys and hit Enter.

Wait for everything to load, and you'll be taken to a command prompt. 

You may want to back up your copy of xorg.conf before you start editing it. You do that with the copy command, "cp". Type:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

and then hit Enter.

Then it's safe to edit your xorg.conf file using the text editor Nano, which works both at the command line and in Terminal. Type:

sudo nano /etc/X11/xorg.conf

and hit Enter.

When you're done making changes to the file, use Ctrl+O (that's the letter, not a zero) to save the file. Nano will default to the existing file name. Press enter to save the changes.

Press Ctrl+X to exit Nano back to the command prompt.

Type "exit" at the command prompt to restart and give your changes a try.

When you boot into recovery mode, you don't need to use "sudo" anymore because you are root now...  Besides, this one command can do both, copying and opening a editor for you...

```
nano -Bw /etc/X11/xorg.conf
```

---

### Post by Tozen on 2006-12-16
Yes, I have pressed the "esc" button during start-up and got in to the menu where "recovery-mode" is an option, but I pressed "c" to get the command-line instead of acutally booting in that mode and get the second promt... sorry...

Know Im in the xorg.conf edit-promt I might get back here since it seems a bit tricky...
thanks!

---

### Post by Tozen on 2006-12-16
Now I have made the changes and hit "ctrl + O" but it says that "error writing /etc/x11/xorg.conf no such file or directory"? 

uh? what? 

Im not sure if Im changing it the right way... Im supposed to go to the section "monitor" and write:
HoriSync 31-82
VertRefresh 40-110
Can i just write it in the promt? or do I have to find the section? How do I do it?
I appreciate your help!

---

### Post by taurus on 2006-12-16
It's X11 as in capital **X** and number 11.  Linux/Unix is case sensitive...

---

### Post by linux4me on 2006-12-16
Taurus- Thanks for the comment about the command you used and the unnecessary "sudo".

---

### Post by Tozen on 2006-12-16
It was the "x11" to "X11" that did it! :)
But know I got in to the next problem, how is the exact syntax?

Im supposed to add the two lines:
HorizSync	31-82
VertRefresh	40-110 

to the 'section"monitor"'

I found the line:
monitor "Generic Monitor"

Do I just add the lines below? It doesn't seem to work....

---

### Post by tommcd on 2006-12-16
Here is the same section from my xorg.conf file:

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 65.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Just change the numbers to what you want. Be sure you have backed up the file first, or use the -B option with nano as suggested.

---

### Post by taurus on 2006-12-16
```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync 31-82
    VertRefresh 40-110
    Option         "DPMS"
EndSection

```
(just before the **Section "Device"**...)

---

### Post by Tozen on 2006-12-16
Sorry... I hadn't looked through the file enough... guess my eyes are getting to tired.
l missed that the line should be "section monitor" and not just "monitor"...
I tried to add the lines in the right place and the computers display are running smooth.
I will now enter the xubuntu-world... jiiha

Thanks all of you for lighting up my novice-darkness!

---

