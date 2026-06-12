---
title: "can i get some help please"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by vdub03 on 2007-06-09
ok i got beryl installed but when i start it i lose the close, minimize, and maximize buttons as well as my terminal just comes up as a white screen. so i'm asking for help getting these things to work and also asking for a very dumbed up way of telling me how to do this. also i need some help on how to us my emerald themes, not sure how i'm susposed to apply them. so please someone help me but keep in mind i'm not so computer smart.

---

### Post by Kobalt on 2007-06-09
Check this out : [http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#My_windows_don.27t_have_any_decorations_.28title_bar.2C_resize_handles.2C_minimize.2Fmaximize.2Fclose_buttons.29](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#My_windows_don.27t_have_any_decorations_.28title_bar.2C_resize_handles.2C_minimize.2Fmaximize.2Fclose_buttons.29)

---

### Post by vdub03 on 2007-06-09
well thanks for the link but i'm not sure what there trying to say.can you explain this a little more

---

### Post by Kobalt on 2007-06-09
The simplest is to open up a Terminal and type these commands : ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
sudo nvidia-xconfig -composite
sudo nvidia-xconfig -allow-glx-with-composite
sudo nvidia-xconfig -render-accel
sudo nvidia-xconfig -add-argb-glx-visuals
```
Then log out and restart X with Ctrl+Alt+Backspace. Now you should have you window decorations.

---

### Post by vdub03 on 2007-06-09
not sure if i did it right but tried it twice and it didn't work

---

### Post by vdub03 on 2007-06-09
this is what i keep getting in my terminal as long as i have it open before i start beryl otherwise its just a white screen
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: unsupported window depth for thumbnail
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: unsupported window depth for thumbnail
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: unsupported window depth for thumbnail

---

### Post by Tux Aubrey on 2007-06-09
Just so you know, those instructions are for nVidia cards and are referring to a file called xorg.conf which lives in the/etc/X11/ folder in the filesystem.  

It is a read-only file, so you have to open it in administrator mode.  The easiest way to edit it (in ubuntu) is to open a terminal (from the menu choose Applications>Accessories>Terminal) and cut and paste this command:

```
gksudo gedit /etc/X11/xorg.conf
```

You will be asked for your password.

**NOW - MAKE A BACKUP OF THE FILE **(It is really important!)

ie File>save as> xorg.conf.bak (or something similar) then reopen xorg.conf

You can now edit according to the instructions in [http://wiki.beryl-project.org/wiki/T...ose_buttons.29](http://wiki.beryl-project.org/wiki/T...ose_buttons.29).  Just cut and paste the new lines it suggests into the right Sections of xorg.conf.

Save and restart X (Ctrl+Backspace).  Log in and start Beryl to  see if it worked.

If you accidentally killed the X server with your edits, Go to a terminal (Ctrl+Alt+F2 is one), log-in and type the following at the prompt (might be an idea to write this down):

```
mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

(Note that X11 has a capital X)

At least that should have you back to where you started before you edited!

All this worked for me when I had the same problem, but you have to be really careful playing with xorg.conf or you will loose your desktop/window manager completely.  

There are, of course, recovery strategies, but you have to know them to use them.

By the way, this is one of the reasons Beryl comes with warnings - Beta software doesn't always work 100% every time.  But it is fun!

Good luck.

(EDIT: I started this before I saw your reply to Kobalt and the error messages.  I have no idea what they mean, but if you are careful with the editing instructions and use a backup, you should be safe to try the solution offered)

---

### Post by vdub03 on 2007-06-09
the link you sent me comes up saying there is no text in the page, but i agree it is very fun, plus its helping me understand what i am doing here

---

### Post by vdub03 on 2007-06-09
also i suppose i should show you what happened when i typed the first command you gave me
gksudo gedit /etc/X11/xorg.conf
(gedit:8281): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by bodhi.zazen on 2007-06-09
> **vdub03 said:**
> this is what i keep getting in my terminal as long as i have it open before i start beryl otherwise its just a white screen
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: unsupported window depth for thumbnail
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: unsupported window depth for thumbnail
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: unsupported window depth for thumbnail

Not sure where you are at, but, for beryl: GLXFBConfig for depth 32


		Add this to the "Screen" section of xorg.conf :

> 			Option "AddARGBGLXVisuals" "True"
			Option "DisableGLXRootClipping" "True" 

---

### Post by vdub03 on 2007-06-09
ok  thanks all i took the first reply i got and added the instructions into the command and i got it all back i'm so happy

happy happy joy joy
ohhhh joy:popcorn:

---

### Post by Kobalt on 2007-06-09
You're welcome :)

---

### Post by vdub03 on 2007-06-09
now if i can just remember how i get my windows to come off the cube when i rotate it i'll be set, then i got to find keyba doc. not sure if i spelled it right

---

