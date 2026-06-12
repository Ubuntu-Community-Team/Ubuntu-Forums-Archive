---
title: "Firestarter Error"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by taekwondodogoof on 2007-05-31
Through the application menu, firestarter won't start. So, I went to terminal and did sudo firestarter. It gave me this error
```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:7672): Gtk-WARNING **: cannot open display:  

```

Thanks for all your help!

---

### Post by TheOtherShoe on 2007-05-31
When you went to the terminal, did you open a terminal window or did you press Alt+F1 to switch to a virtual terminal (replace F1 with whatever function key you might have used)? In the latter case a graphical application like the Firestarter GUI won't work, and you should try running that command again in gnome-terminal.

If that is not the problem then there are other things to consider. Are you running XGL? Or have you made any other custom modifications to your Xorg configuration? You can have multiple Xservers running; by default the first one runs on display ":0.0", which is a code for virtual terminal 7. It is possible that your computer is configured to run X on a different display and that Firestarter isn't picking up on that for some reason. If this is the problem then the following command should return something other than ":0.0" :
```
echo $DISPLAY
```

---

