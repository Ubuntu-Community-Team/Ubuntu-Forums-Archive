---
title: "Help needed to improve screen resolution"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Wee Nyaff on 2007-04-11
:confused: 
I have now been an Ubuntu user for all of 14 hours.  I am learning.

The latest matter I need direction is how to improve my screen resolution.

I am running a Viewsonic VA1912w monitor with a Nvidea 7600 GS graphics card.

The optimum resolution for the monitor is 1440 x 900 but the system gives me a maximum of 1024 x 768.

How do I improve on this?  Is there anything obvious I am missing apart from brain cells?

Thanks in advance,
Alan

---

### Post by heimo on 2007-04-11
Check this howto:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by ClinicalMistake on 2007-04-11
As the above post mentions, you need to edit the xorg.conf
I had a very similar problem and adding that resolution fixed my troubles :D

---

### Post by Wee Nyaff on 2007-04-11
> **heimo said:**
> Check this howto:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

I have tried this but it has raised a new problem for me.

When I open a terminal it already has [alan@alan-desktop:~$ ] in there.  I can cut and paste the required code after that but it then asks for my password.  When i try to put this in my keyboard refuses to respond.  The same thing happens when I clear out what is already there and type in the code. IE the keyboard refuses to work.

I do not know what to do next.
Alan

---

### Post by justleen on 2007-04-11
you wont actually see what you type, with the password. no *** like windows :)

Just type your own user passwd when promted

```

sudo gedit /etc/X11/xorg.conf 
```

Be sure to make a backup though!
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
```

---

### Post by Wee Nyaff on 2007-04-11
Thanks for this.  It worked, I feel such a fool.  Now all I have to do is find how to improve the screen resolution.
Alan

---

### Post by joewolz on 2007-04-11
Thanks everyone in this thread.  I am a complete Linux/Ubuntu newbie and was having the same issue as the OP.  With the pointers and advice here I finally fixed my resolution and refresh problem.

THANKS!

---

### Post by heimo on 2007-04-11
> **joewolz said:**
> Thanks everyone in this thread.  I am a complete Linux/Ubuntu newbie and was having the same issue as the OP.  With the pointers and advice here I finally fixed my resolution and refresh problem.

THANKS!

Always glad to hear good news. Hopefully Wee Nyaff also gets his resolution fixed. If not, please post back with any questions / extra information.

---

### Post by Wee Nyaff on 2007-04-12
Guys and Gals I am afraid I still need help.  I cannot get anything to change my resolution.  Following is a printout of what I get whenever I try something.
[alan@alan-desktop:~$ sudo dpkg-reconfigure xserver-xorg
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN6> line 13.
xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized]

What can I do now?

Thanks
Alan:confused:

---

### Post by heimo on 2007-04-12
Have you ... what have you done lately to your system? :) Seems abnormal and not very healthy. I'd try uninstalling a lot of X related stuff, then reinstalling. Or you could just ... and I rarely recommend this ... reinstall Ubuntu, as it might be quite easy for you if you haven't done much with it yet and can format partitions.

---

### Post by Wee Nyaff on 2007-04-12
> **heimo said:**
> Have you ... what have you done lately to your system? :) Seems abnormal and not very healthy. I'd try uninstalling a lot of X related stuff, then reinstalling. Or you could just ... and I rarely recommend this ... reinstall Ubuntu, as it might be quite easy for you if you haven't done much with it yet and can format partitions.

Thanks to everyone who tried to help. In particular heimo.  
Since I do not know how to uninstall items properly and realise that even then I may still have problems, I intend to start from scratch.
I notice that the next version Feisty Fawn is due out 19/4/07 so I may wait till that is available before doing anything.
I will mark my thread as resolved in the meantime.
Thanks again
Alan

---

### Post by heimo on 2007-04-12
> **Wee Nyaff said:**
> Thanks to everyone who tried to help. In particular heimo.  
Since I do not know how to uninstall items properly and realise that even then I may still have problems, I intend to start from scratch.
I notice that the next version Feisty Fawn is due out 19/4/07 so I may wait till that is available before doing anything.


You're welcome. Sorry we couldn't solve it, but I think your suggested approach will be good - sometimes it's just not worth "fighting the windmills". Trying Feisty next, about week from now, will be a good choice. And then we'll be here, if you'll need any assistance.

---

### Post by Wee Nyaff on 2007-04-13
Last comment on this for all people having trouble with screen resolutions or indeed any other problem.
The truth is out there.
Follow the advice given and/or read, read and more read what is available on the "net".
I am pleased to say that my resolution problem has been fixed by doing just that.

More thanks to all of those who tried to help me.

Alan:D

---

### Post by heimo on 2007-04-13
Great to hear, Wee Nyaff! Please, if you could give us any links or steps you followed, it'd be easier for the next person in same situation to fix it. Could you do that? Thanks!

---

