---
title: "Screenshot"
date: 2010-07-29
forum: Apple Hardware Users
---

### Post by jaco223 on 2010-07-29
Hi

Does anyone know how to take a screen shot using the imac aluminum keyboard? I'm using Lucid on my imac ...I want to take a screen shot of cube I'm using kubuntu 10.04 ...

---

### Post by cj.surrusco on 2010-07-29
The command to use a screenshot (assuming you are using gnome) is 'gnome-screenshot'. So you can set a keyboard shortcut to that and then you would be able to choose the keys to press for a screenshot. 

To do that, go to **Preferences>Keyboard Shortcuts**. Just make a new one with the screenshot command and choose the keys.

---

### Post by jaco223 on 2010-07-30
> **cj.surrusco said:**
> The command to use a screenshot (assuming you are using gnome) is 'gnome-screenshot'. So you can set a keyboard shortcut to that and then you would be able to choose the keys to press for a screenshot. 

To do that, go to **Preferences>Keyboard Shortcuts**. Just make a new one with the screenshot command and choose the keys.

CJ ...

Thanks but I'm using Kubuntu 10.04 ...I Googled it, and there's not really an answer for it using Kubuntu

---

### Post by 23dornot23d on 2010-07-30
Top set of keys on your keyboard - print screen - usually works 

Next key on the right of F12 usually although looking at the [keyboard layout very minimalistic]("http://images.google.com/images?q=imac%20aluminum%20keyboard&biw=1382&bih=655").

Says [F14 in this thread though]("http://discussions.apple.com/thread.jspa?messageID=11558340")

Interesting .....[ this then says F13]("http://seanp2k.com/2008/05/new-imac-keyboard-hack-for-windows-printscreen-scroll-lock-etc/") .....

Problem exists with this particular keyboard by the looks ....

---

### Post by ankspo71 on 2010-07-31
Hi,
I am using Kubuntu Maverick (pre-release) so I might be able to help, though since we're using different versions of KDE the instructions may not be accurate. KSnapshot is the utility used for making screenshots and the application itself can be found in the 'Applications > Graphics' menu. I usually just use the application itself, and if I wanted to take a screenshot of the cube, I would tell it to take a new screenshot after a delay of about 5 to 10 seconds. I know this isn't always convenient though.

Next is to figure out what button KDE's PrintScreen function is bound to if you are not using a keyboard with a 'Prt Scr' button or similar:

Go inside System Settings, and look around for the utility to configure your shortcuts. On my version of KDE, it is located at Applications > Settings > System Settings > Shortcuts and Gestures. 
Once you have Shortcuts and Gestures open, click on the Global Keyboard Shortcuts category on the left. 
At the top will be a drop down menu that says "KDE Component: KDE Daemon". Select "khotkeys" from the dropdown menu.  
You should see the PrintScreen function there. Mine is set as "PrintScreen > Print". 
If you see PrintScreen but it isn't assigned to anything, you can assign a new shortcut to PrintScreen from there. 
Hope this helps.

---

### Post by Roger W on 2010-07-31
Isn't it just cammand shift 3 for the whole screen and Command shift 4 to select an area of the screen? or have I mis-read the question?

---

### Post by seanp2k on 2011-05-15
Hey, I found this thread due to the incoming link and just wanted to clarify:

I actually just posted an article about remapping keys using xmodmap because I was frustrated that the "Command" key is where "Alt" should be.  Using this technique, along with 'xev' to see what the key code of the key you want to remap "from" and "to" is, you can fix the problem mentioned in this thread:

[http://seanp2k.com/2011/05/using-xmodmap-to-swap-keys-in-linux/]("http://seanp2k.com/2011/05/using-xmodmap-to-swap-keys-in-linux/")

Hopefully someone finds this useful.  It took me a while to figure out how to do this properly.  Also, just naming the file ~/.xmodmap didn't work for me; I had to put the following in my .bashrc:
```

# fix apple keyboard
cat ~/.xmodmap | xmodmap -

```

Here is my .xmodmap:

```

remove mod4 = Super_L
keycode 133 = Alt_L
remove mod1 = Alt_L
keycode 64 = Super_L

```

(again, this is to swap the "Command" and "Alt" (Option) keys on the aluminium iMac wired keyboard with numpad.  YMMV with other makes / models but the same techniques should work.

Other useful resources relating to this problem:
[http://superuser.com/questions/193200/etc-x11-xmodmap-doesnt-work-for-ubuntu]("http://superuser.com/questions/193200/etc-x11-xmodmap-doesnt-work-for-ubuntu")
[http://superuser.com/questions/185345/why-wont-my-xmodmap-command-run-on-startup-login]("http://superuser.com/questions/185345/why-wont-my-xmodmap-command-run-on-startup-login")

Good luck, and sorry for reviving this zombie thread...but it's still relevant.

EDIT:  You might have better luck naming the file '~/.Xmodmap' (note the capital X) or using the 'keysym' directive, which is described in detail here: [http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap]("http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap")

---

