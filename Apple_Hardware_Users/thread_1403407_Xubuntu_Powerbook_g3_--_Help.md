---
title: "Xubuntu Powerbook g3 -- Help"
date: 2010-02-10
forum: Apple Hardware Users
---

### Post by Masterkick on 2010-02-10
Hullo!
 
I have a Powerbook g3 Lombard at had installed mac os 9. I really wanted to install Xubuntu, but the cd image of Xubuntu 9.10 alternate for PPC was too big for a cd, so I downloaded Xubuntu alternate 8.10 for PPC and finally managed to install it.
 
I read a lot of guides in this forum that helped me, but now I got a problem i can't fix. Xubuntu boots right, I put on the boot "console" linux video=ofonly nosplash (if not i get the black screen) then it shows loading... it loads perfectly, finishes loading, but then when i suppose it should show the desktop,i only see a black screen with a blue line across it. Please, i need help, and i got a feeling I am almost there!
 
 
Live long and Prosper,

---

### Post by linuxopjemac on 2010-02-10
you need to get into a console tty and change the /etc/X11/Xorg.conf file to something simple like:

with 

sudo nano /etc/X11/Xorg.conf

```
Section "Device"
Identifier "ATI Rage 128"
Driver "ati"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 60-60
VertRefresh 43-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection

```

---

### Post by linuxopjemac on 2010-02-10
also nice link for you:
[http://ubuntuforums.org/showthread.php?t=1114297&highlight=ibook+tutorial](http://ubuntuforums.org/showthread.php?t=1114297&highlight=ibook+tutorial)

---

### Post by Masterkick on 2010-02-10
> **linuxopjemac said:**
> you need to get into a console tty and change the /etc/X11/Xorg.conf file to something simple like:
 
with 
 
sudo nano /etc/X11/Xorg.conf
 
 
Thanks for the fast answering! But... how do i get into a console tty?
 
Thanks in advance!,

---

### Post by linuxopjemac on 2010-02-10
I don't know if it still works in Ubuntu alternate installer, but Debian uses CTRL+alt+F-key (e.g CTRL+alt+F1).

---

### Post by Masterkick on 2010-02-10
> **linuxopjemac said:**
> I don't know if it still works in Ubuntu alternate installer, but Debian uses CTRL+alt+F-key (e.g CTRL+alt+F1).
 
I have tried, but when i do it the small line in the screen dissapears and i get a completely black screen.
 
Thanks, and; would you like a video of the computer starting perhaps, so you can see the problem?
 
Live long and Prosper!

---

### Post by Bq32 on 2010-02-10
> **Masterkick said:**
> I have tried, but when i do it the small line in the screen dissapears and i get a completely black screen.
 
Thanks, and; would you like a video of the computer starting perhaps, so you can see the problem?
 
Live long and Prosper!

Try all of the F-keys up to F6 (So, Ctrl-Alt-F1, Ctrl-Alt-F2, Ctrl-Alt-F3...) until you come up to a prompt.

But it sounds like it'd be a problem with your video card. Are you sure you have the minimum requirements for Xubuntu (video/CPU wise)? Do you see any "Ubuntu is in Low-Graphics Mode"-type window?

If you do happen to get to a prompt, try and see if you can use it, try "echo Hello" and see if it sends "Hello" back.

---

### Post by Masterkick on 2010-02-10
> **Bq32 said:**
> Try all of the F-keys up to F6 (So, Ctrl-Alt-F1, Ctrl-Alt-F2, Ctrl-Alt-F3...) until you come up to a prompt.
 
[COLOR=red]**Ive tried that, no effect.**[/COLOR]
 
But it sounds like it'd be a problem with your video card. Are you sure you have the minimum requirements for Xubuntu (video/CPU wise)? Do you see any "Ubuntu is in Low-Graphics Mode"-type window?
 
[COLOR=red]**I think i got them, if it could run Mac os X i think it will be able to run Xubuntu. I dont see any windows, it's the whole black screen with a very small line that goes from up to down of the screen.**[/COLOR]
 
If you do happen to get to a prompt, try and see if you can use it, try "echo Hello" and see if it sends "Hello" back.
 
Answers in [COLOR=red]**Red**[/COLOR]
I Forgot saying it before, but sorry for my english.
[COLOR=black]Thanks for all the help you are giving to me[/COLOR]
 
Live Long and Prosper!

---

### Post by linuxopjemac on 2010-02-10
Do you really need Ubuntu, or is Debian also fine?

---

### Post by Masterkick on 2010-02-10
> **linuxopjemac said:**
> Do you really need Ubuntu, or is Debian also fine?
 
Would Debian work, and is it user friendly as Ubuntu? If it is, I download it at warp speed.
 
Thanks, many thanks!

---

### Post by Bq32 on 2010-02-10
> **Masterkick said:**
> Would Debian work, and is it user friendly as Ubuntu? If it is, I download it at warp speed.
 
Thanks, many thanks!

Actually, Ubuntu is based off of Debian, and the only difference is that Ubuntu/Debian run GNOME (different from Xubuntu, which runs XFCE, another GUI). If Debian were to run slow, and you had it installed, you could just install xfce to Debian, or (if it shows on Debian), xubuntu-desktop.

And yes, Debian is about the same as Ubuntu in User-friendlyness (and last time I checked, it looks about the same as Ubuntu, too).

---

### Post by linuxopjemac on 2010-02-10
Go for Debian, the installer works for you without glitches. As was posted earlier, you can install XFCE later. You can then opt for this display manager after boot at the GUI login screen.

I own a Pismo with lenny on it :)

---

### Post by Masterkick on 2010-02-10
Well, i will give Debian a try. If it works I will post here and I'll give you everything you may want (?)
 
Live Long and Prosper!

---

