---
title: "xubuntu ibook g3 help!!!"
date: 2009-02-24
forum: Apple Hardware Users
---

### Post by chort27 on 2009-02-24
So I installed Xubuntu 8.10 on my iBook G3 - 
I have to type Linux video=ofonly at the Yaboot screen to get past the black screen.
Once i get to the login window, I can login fine with no problem. I see the light blue screen, then the desktop wallpaper loads with 3 icons on the desktop. Then the top and bottom bar start to load, but by the time the top bar fully loads, the icons on the desktop have disappeared. I now can't open anything. If I try to open a file browser, it will flash on the screen for a second, but then disappear as well. Nothing shows up on the bottom bar, except for the flash when the window opens for a second. . . sometimes it opens for a few seconds and i can interact with it but then it closes.

ANY HELP!?
Thanks,
Chort27

---

### Post by mkvnmtr on 2009-02-24
Do you have enough ram to run the system?

---

### Post by ghostz on 2009-02-25
yea ram has to be the issue for intrepid i had it on my own ibook g3 dual usb 500Mhz but if u can max the ram out i think the max should be 640 depending what logic board u have

---

### Post by chort27 on 2009-02-25
i dont know how to do that :-\

---

### Post by ghostz on 2009-02-25
ok well the ibook should have 128 built on to the logicboard and u can add more ram from under the keyboard u can add another 512mb to it and with that is maxed out the ram should be pc-100 sdram.

---

### Post by Gen2ly on 2009-02-25
could be a nautilus problem too?  nautilus controls the desktop and is the file browser too.  try to load nautilus from the terminal.

---

### Post by chort27 on 2009-02-25
> **Dirk.R.Gently said:**
> could be a nautilus problem too?  nautilus controls the desktop and is the file browser too.  try to load nautilus from the terminal.
Command for this?

---

### Post by mkvnmtr on 2009-02-25
If you have 128 Mb of ram you might have trouble opening nautilus. The command from the terminal is just to type in nautilus and then press enter. I have learned the hard way it won't work if you don't spell it correctly.

---

### Post by Gen2ly on 2009-02-26
nautilus.  gnome-terminal in launcher.  Might Leave a bit offeedback.

---

### Post by chort27 on 2009-02-26
> **mkvnmtr said:**
> If you have 128 Mb of ram you might have trouble opening nautilus. The command from the terminal is just to type in nautilus and then press enter. I have learned the hard way it won't work if you don't spell it correctly.

typed it in failsafe terminal mode, got the message:
bash: command not found

when i run it normally  logged in with alt-f2 i get:
The command "nautilus" failed to run:
Failed to execute child process "nautilus" (No such file or directory)

---

