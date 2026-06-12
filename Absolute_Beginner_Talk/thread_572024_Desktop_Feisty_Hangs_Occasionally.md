---
title: "Desktop Feisty Hangs Occasionally"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by LordKelvan on 2007-10-10
Hi All:

Every now and then my computer freezes (it actually just froze).  My music is still playing, but my computer will not respond to keyboard/mouse input.  I was right-clicking a page in Firefox, although I don't think this is the root cause (I seem to recall I was doing other things when it froze other times).  So I have a couple of questions:

1)  Is there some equivalent of Ctrl+Alt+Delete for Ubuntu?  I have seen online people talking about Alt+SysRq+K, but that is a bit drastic since I don't want to reset.  What I want to be able to do is shut down the offending application (I am sure its some app that is hogging the CPU).  It is very annoying to have to basically restart/reload Ubuntu.

2) Is there some way to limit CPU usage on my computer, say to 90% or something?  I am thinking this might be a way to prevent my computer from freezing completely, since I could always bring up a terminal and launch "kill" on the malfunctioning program.

3) Where can I find information on what is causing my computer to freeze?  Is there some log which keeps track of, say, which app was hogging the CPU before I was forced to restart?

Thanks in advance,
LK

---

### Post by bobplano on 2007-10-10
you can run 'top' from a terminal and that will list all the running apps, how much ram and cpu they are using too. there's killall and there's some Gui thing to close a window but the gui one needs the mouse working and i'm not too sure about the terminal way. you could try running this stuff in a virtual terminal (ctrl+alt+F1; (ctrl+alt+F7 to get back)

---

### Post by ravenwere on 2007-10-10
I have had a similar problem now for a few months.... usually occurs when scrolling in the browser or while using akregator in the Kontact frontend. The problem occurred in feisty and continues now I have started using gutsy.

It even occurs when using kde with Openbox as the windows manager. I was blaming konqueror and/or the graphics card/setup but am not 100% sure.

I have a kde environment. Radeon 9800 Pro. AMD Sempron 2800. 1 Gig RAM

When this occurs only the mouse pointer moves on screen but all other functions are frozen. Downloading will continue, Music will keep playing. The only combination of keys that seems to work is Alt+SysRq+b.

This is obviously in the gui environment and occurs on average once every two days.

I don't want to lead this thread off track so ,,,,,,,,, Is this similar to your issue? Are you able to get any response from the keyboard or on screen? What gui environment are you using? What hardware? And can anyone advise on what logs to check out after the event?

---

### Post by vikasmk on 2007-10-10
mine too. it freezes so i just uninstalled it. 
switched back to windows.

---

### Post by LordKelvan on 2007-10-10
I am not sure if my problem is the same, as I really don't know what is causing it.  I should mention that I am using Feisty Fawn (7.04) with Gnome.  I usually have Azureus, Amarok, Pidgin and Google Desktop running in the background. Sometimes I have jEdit, Adobe Reader and Firefox running as well.  I believe I am using the open-source ATI drivers (my card is x800xl).

bobplano: The problem is that usually my keyboard is dead and my mouse cursor moves, but I can't click on anything (so the use of killall and top won't work).  Actually, my computer just crashed, and this was pretty severe.  My task bar disappeared, there were some graphical artifacts on the screen, and both my keyboard and mouse were dead.  The only way to get out of it was using Alt+SysRq+B. 

Anybody else have ideas/help/suggestions?

---

### Post by steveneddy on 2007-10-10
Try a different (older, stable) video driver.

Try VESA as a video driver and see if that helps. VESA is a generic driver that won't do 3d, but if it doesn't crash, it may be the video driver you are using for ATI.

Do a memtest.

At boot, go into Grub and select the memory test.

:popcorn:

---

