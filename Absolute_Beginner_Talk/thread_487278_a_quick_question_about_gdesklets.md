---
title: "a quick question about gdesklets"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Mostlyharmless42 on 2007-06-28
i just installed gdesklets earlier today.  I've seen lots of screen shots w/ them on and none of them have the ugly black boxes like mine does.  I changed a setting and one of my desklets went translusent, but then i restarted and it is black again and i can't find the setting.  Where is this setting???

---

### Post by ryanVickers on 2007-06-28
How did you get it to start!? On my computer, it just opens the window, waits a bit, then closes!

---

### Post by Mostlyharmless42 on 2007-06-28
It just worked, do you have the accelerated drivers for you're graphics card???

---

### Post by ryanVickers on 2007-06-28
Yeah, they're fine - even my _*virtual machine*_ can render 3D like a native OS!

---

### Post by dagrump on 2007-06-28
Right click the desklet, & configure. Turn off the borders. No black boxes.

---

### Post by Mostlyharmless42 on 2007-06-29
it's not a border, it's a solid box.  All borders do is make the black box bigger.  I found the option, but it is still marked.  It just stopped working.

---

### Post by Dr. Nick on 2007-06-30
do you have beryl or compiz? I found if you stop either of them the boxes appear. Thats was awhile ago, my new install gdesklets is crashing so i cant help to much now

---

### Post by ubonetu on 2007-07-02
They are screen outlines from translucency that gets made before Beryl or Compiz has fully started.  I was having problems with even getting borders like they were windows.

The fix is pretty easy, just quit out of gDesklets and make a text file with gedit somewhere memorable that says this:```
#!/bin/bash
sleep 7 && /usr/bin/gdesklets
```

The script sleeps for seven seconds and when successfully slept, runs gdesklets.  

Save the file and quit gedit.

Make that script file excecutable:```
chmod +x <yourfilename>
```

Finally, under the System menu, open Sessions under Preferences, click on the Current Sessions tab and remove instances of gdesklets (if you were having trouble with multiple instances, this is where that problem is from).  Now just click on the Startup Programs tab, make a new entry (Call it, Ward is Great ;-) and click browse to find your script file you made.

Log out and back in and it should work (you may need to tweak the timing a bit if you have the Beryl logo show or have a slow system).

My clock desklet still shows it's edge when I log in but one click on the desktop and it's gone.  I'm counting that as Beryl-1, Ward-1, gDesklets-1, Bugs-0

Take care,
me

---

### Post by CaptainInsaneO on 2007-07-05
ubonetu, your fixed worked partway for me... so thanks!

The problem I'm having now is I have two windows in my bottom panel that say "gdesklets-daemon". They're my eth and mem desklets. How do I prevent these from showing up? When I'm using Metacity as my window manager, everything is perfect but as soon as I switch it to beryl as the window manager everything goes awry. :(

---

