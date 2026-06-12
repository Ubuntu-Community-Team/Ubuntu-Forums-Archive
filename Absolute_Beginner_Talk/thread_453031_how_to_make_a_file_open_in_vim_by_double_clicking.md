---
title: "how to make a file open in vim by double clicking?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2007-05-23
is there a  way to make a file open with vim by double clicking it?

when i right click and go to opens with then do custom command and type vim it tells me it cant add it to the application database...

thanks

---

### Post by glennric on 2007-05-23
Try using the custom command

```
vim %f
```

Actually you will probably have to use gvim.  So try 

```
gvim %f
```

---

### Post by linfidel on 2007-05-23
> **jinxjinx said:**
> is there a  way to make a file open with vim by double clicking it?

when i right click and go to opens with then do custom command and type vim it tells me it cant add it to the application database...

thanks
Try right-clicking the file, choose properties, then "Open With".

---

### Post by jinxjinx on 2007-05-24
yeah i dont want gvim i want vim from the command line..
when i do open with and type those custom commands i get "cannot add application to database"

---

### Post by ahmatti on 2007-05-24
You need  to use a command to open also the terminal. To make a document open in vim inside xterm just type "xterm -e vim" in the "custom command" field.

---

### Post by jinxjinx on 2007-05-24
thanks!

the command works

but when i "open with other application" and "use a custom command" 
it tells me

Could not add application
Could not add application to the application database

it tells me this regardless of what i type in the custom command 


any ideas???

---

### Post by GlorytheWIz825 on 2007-12-09
I'm having similar problems as the OP. I want vim as my default text editor. 

I have created a text file on the desktop, but when I double click it, it opens up with gedit. How do I change the default to vim?I tried doing a custom of /usr/share/vim with "Open with", but nothing happens. VIM does not open. Any tips guys? Thanks!

---

### Post by hugmenot on 2007-12-10
You specified a directory as the custom command.

Try this
```
gnome-terminal -x vim
```

---

