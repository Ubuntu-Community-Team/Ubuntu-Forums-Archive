---
title: "Lost top and bottom tool bar"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by marsia on 2008-02-12
hello there

I run linux ubuntu and for some reason i have lost top and bottom tool bar, nothing else. how do I bring them back? If you tell me how, then I know how to add things and buttons on them. 

thank you. 

marsia (i love linux)

---

### Post by pedro_orange on 2008-02-12
You can add a panel to the desktop, by simply right-clicking going into the context menu and selecting add panel. 

Are you sure this is not a screen resolution problem if you're not seeing the toolbars. Try changing your resolution and see if that helps

---

### Post by jhenager on 2008-02-12
> **pedro_orange said:**
> You can add a panel to the desktop, by simply right-clicking going into the context menu and selecting add panel. 

Are you sure this is not a screen resolution problem if you're not seeing the toolbars. Try changing your resolution and see if that helps

That's what I thought, too, but you can add a panel only by right clicking on an existing panel.
I would see if you can adjust your vertical size on the monitor itself. Hopefully, that's where the panels are.

---

### Post by marsia on 2008-02-12
no, this is not a resolution problem. when i righclick on the screen it says create launcher, create URL link, create folder, create from tamplete, and desktop settings, no context menu...

---

### Post by marsia on 2008-02-12
it has happened before and i seem to remember my friend had to do it via the terminal

---

### Post by Technoviking on 2008-02-12
Try running the following in a terminal or Alt-F2 (for run a program).
```
gnome-panel &
```
and see what happens.

---

### Post by jhenager on 2008-02-12
> **Mike said:**
> Try running the following in a terminal
```
gnome-panel &
```
and see what happens.

I am curious as to the resolution of this problem, and I tried this on my system which has a panel running. It replies back with 'A panel is already running.'
That command might help.

---

### Post by Leperous on 2008-04-20
I lost my bars after having to restart Ubuntu the CTL-ALT-BACKSPACE way a couple of times in succession (after EVE's memory leak crashed my laptop...).

The way I fixed it was to open a terminal, type **top** to see the list of processes running, get the process ID for gnome-panel (the leftmost number), and then typing **kill *process ID***.

You should then be able to run **gnome-panel** in a terminal and get your bars back again. Note that you can CTRL-C out of it or close the terminal, since Ubuntu will 'wake up' and realise the bars should be there.

---

### Post by Dropi on 2008-05-10
I had the very same problem just a few minutes ago, I tried the ```
gnome-panel &
``` and it said I didnt have gnome installed, so I did a ```
sudo apt-get install gnome-panel
``` and yay, they appeared with all my former settings and a few errors regarding trashcan..

---

### Post by Dropi on 2008-05-10
although now I am faced with a different problem, some of my applets for Gnome Panel refuse to work, when I try to add trashcan back to the bar I simply get an error that it wont load and it asks if I want to delete it from the list or not ... if I do press delete nothing happens besides that pesky window leaving... same happens with volume control, cpu frequency monitor and one or two others

---

### Post by cedarmark on 2008-06-17
> **Leperous said:**
> I lost my bars after having to restart Ubuntu the CTL-ALT-BACKSPACE way a couple of times in succession (after EVE's memory leak crashed my laptop...).

The way I fixed it was to open a terminal, type **top** to see the list of processes running, get the process ID for gnome-panel (the leftmost number), and then typing **kill *process ID***.

Having CTL-ALT-BACKSPACE a few times, l get the error message "The greeter application appears to be crashing. Attempting to use a different one." & an ok button.

In regard to using Terminal l do not know how to access this, as l would normally do this through the top toolbar. Please advise.
Thanks in advance.

---

