---
title: "I want rid of Gnome."
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-02-12
I installed XFCE today, and all went smoothly, until I set it as the default in the "sessions" menu at the log in screen. 

Then, I lost the ability to get a right click menu, and I can't set a wallpaper - I'm stuck with this solid brown colour.

I don't think that I'll be using Gnome anymore. And it's ruining XFCE. How do I get rid of it?

Thanks

---

### Post by wrtpeeps on 2006-02-12
i think it's nautilus. i had this problem. You need to run nautilus with --no-desktop if i remember correctly.

---

### Post by Jimmey on 2006-02-12
Thankyou very much. :)

---

### Post by wishyjr on 2006-02-12
i've got similar issues too Jimmey, i worked out that if you type xfdesktop into a terminal your wallpaper changes should come through. Its a bit odd that the desktop doesnt 'refresh' after a change, i wonder if its something to do with theh other desktop (i.e. gnome/kde). 

i notice that you've lost your right-click menu too -maybe the issues are related somehow.

wrtpeeps: yuo suggest that nautilus needs to be ran in a different way, would this be ture for konqurer too (im running kubuntu)?

thanks

---

### Post by wrtpeeps on 2006-02-12
i have heard about konqueror doing this too. But i am not sure of the option for it. Sorry

---

### Post by alfonz on 2006-02-12
what version of xFce are you guys running?

add these repos in ur /etc/apt/sources.list

```
## xFce repositories - uncomment if to check if there are updates only
#deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports main universe
#deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports-staging main universe
#deb http://www.os-works.com/debian testing main
```

sorry the comment i made for myself lol, anyway uncomment them to get xFce updates if there are any. apt-get update will give you error for public key, don't worry get the updates and comment them back once your done

---

### Post by Jimmey on 2006-02-12
The one that comes with apt-get. How I check, I don't know.

---

### Post by alfonz on 2006-02-12
add the repos to get updates, its what i did and fixed some issues i was having.

make sure to comment them out again so u don't get error messages

---

### Post by wishyjr on 2006-02-12
hey, hat got my right-click menu back -thanks. Xfce still doesnt load my wallpaper correcty though - running xfdesktop in my terminal gets it back, is there a way of automating that? or maybe a setting ive missed? 

also, alot of stuff doesnt remain in my session when i exit, things like firefox, limewire, and my ROX windows etc. My terminal stays there as well as XMMS and Konversation. Is that something that could be amended?

cheers

---

### Post by Jimmey on 2006-02-12
Alt + f2 >> 
"xfdesktop".

Log out, and click "Save settings", or whatever.

I think that works.

---

### Post by wrtpeeps on 2006-02-12
[QUOTE=wishyjr]hey, hat got my right-click menu back -thanks. Xfce still doesnt load my wallpaper correcty though - running xfdesktop in my terminal gets it back, is there a way of automating that? or maybe a setting ive missed? 

also, alot of stuff doesnt remain in my session when i exit, things like firefox, limewire, and my ROX windows etc. My terminal stays there as well as XMMS and Konversation. Is that something that could be amended?

cheers[/QUOTE]

run xfdesktop in terminal. However, if you run nautilus, it will go back to the way it was, unless you alias the command 'nautilus' to 'nautilus --no-desktop' and change the command in the icon on the 'bar'

---

### Post by wishyjr on 2006-02-13
ok cool. but i run konqurer not nautilus, does the '--no-desktop' parameter work with that too? and where do i need to add that? sorry, still learning here and there. thanks.

---

