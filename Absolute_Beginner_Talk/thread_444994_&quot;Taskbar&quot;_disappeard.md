---
title: "&quot;Taskbar&quot; disappeard"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by helgi on 2007-05-15
Hello there,

I am as fresh as they can get when it comes to linux user.  I just finished installing xubuntu on my machine a few days ago. I think its quite an accomplishment for a novice like me.

Anyway I managed to make the "taskbar" disappear. I've tried getting it back by using Panel manager(I think its called) I have the option enabled of accessing the programs that appear in the taskbar menu by clicking on the desktop, but I want my taskbar back.

Helgi
-Iceland

---

### Post by Kobalt on 2007-05-15
By "taskbar" do you mean the icons for such program as Gaim, the power manager or the network-manager when they are running in background ? If so, then it's a notification area you're searching for. You can add it with a right-click on a panel and selecting Add to the panel...

---

### Post by heimo on 2007-05-15
I was wondering the same thing. Other possibility could be that list of open windows is missing. In that case, right-click on panel -> Add to Panel -> Window List. If one of the two panels is missing, right click on panel and choose New Panel.

---

### Post by lopagof on 2007-05-15
right click on the panel and add new item you should scroll down and see it

---

### Post by helgi on 2007-05-15
sorry guys I am refering to the thing that is like the taskbar with the "Start button" in Windows.

---

### Post by heimo on 2007-05-15
> **helgi said:**
> sorry guys I am refering to the thing that is like the taskbar with the "Start button" in Windows.

Ok. Same method (right-click etc), but it's called Menu Bar.

---

### Post by big-chip on 2007-05-15
Im having a similar problem. I just booted Xubuntu from a cd and there are no windows like start bars in place like the picture i saw had one at the top and bottom. How do i get them to show?

---

### Post by crimesaucer on 2007-05-15
Nice avatar heimo...

you could also try this if you are not able to add a new panel.

Click alt + F2, then enter the code:

(I don't use gnome so it might be either Gnome-panel & or gnome-panel &)

```
Gnome-panel &

```

but for xubuntu it was xfce-panel & that worked for me:

```
xfce-panel &

```

---

### Post by big-chip on 2007-05-15
Do i run that code in terminal?

---

### Post by Happy_Man on 2007-05-15
Yeah....

---

### Post by crimesaucer on 2007-05-15
or just press: alt + F2

it will run that one line of code.

---

### Post by big-chip on 2007-05-15
The first one doesnt work and when i tryed gnome it asked me to install it by typing stuff in so i did but that didnt work either. My computer isnt connected to the net im surfing from my mac at the moment.

---

### Post by crimesaucer on 2007-05-15
> **big-chip said:**
> Im having a similar problem. I just booted Xubuntu from a cd and there are no windows like start bars in place like the picture i saw had one at the top and bottom. How do i get them to show?

You can also right click your menu, select Settings-->--Settings Manager. click it. and then click Panel.

Then try to add a panel using the "plus" sign. If you are able to add a panel, and it is blank, then right click onto the panel, and click "Add New Item" to see a list of what you can add to your panel. You will probably want to start with the "Xfce Menu".

Now if you can't get the Panel added that way, then try to run that Terminal code.

---

### Post by crimesaucer on 2007-05-15
> **big-chip said:**
> The first one doesnt work and when i tryed gnome it asked me to install it by typing stuff in so i did but that didnt work either. My computer isnt connected to the net im surfing from my mac at the moment.

You are using xubuntu, so you need to do this one:

```
xfce-panel &

```

But try to do it through your menu first, the way I instructed, in my post above this one.

---

### Post by Happy_Man on 2007-05-15
Have you tried auto-adjusting your monitor? Sometimes it's a monitor issue...

---

### Post by big-chip on 2007-05-15
I clicked the panel button and nothing happened :( 

I typed in xfce-panel & into Terminal and pressed enter and it gave me

> ubuntu@ubuntu:~$ bash: xfce-panel: command not found

Did i break xbuntu allready?

---

### Post by big-chip on 2007-05-15
Ok how do i do this monitor ajusting thing then? everything is looking large maybe its off the edge of my screen.

---

### Post by helgi on 2007-05-15
Im following along. I tried the xfce-panel & command  in alt+F2 but it does nothing.

I have managed to create the xfce menu panel. but its not like the original that stretches over the top of the screen and has the clock on it.

Guess it will have to do..

---

### Post by crimesaucer on 2007-05-15
> **big-chip said:**
> I clicked the panel button and nothing happened :( 

I typed in xfce-panel & into Terminal and pressed enter and it gave me



Did i break xbuntu allready?

Ok, if you clicked the panel button and it didn't do anything, then you do have to do it through terminal or alt + 2.

Try this:

```
killall xfce-panel
```

Then try:

```
xfce-panel &

```

and beyond that, I'm not sure what to say.

again...with the & sign.

---

### Post by big-chip on 2007-05-15
no still no results :(

Maybe this is a sign form the linux gods telling me to keep to osx

---

### Post by crimesaucer on 2007-05-15
> **helgi said:**
> Im following along. I tried the xfce-panel & command  in alt+F2 but it does nothing.

I have managed to create the xfce menu panel. but its not like the original that stretches over the top of the screen and has the clock on it.

Guess it will have to do..

To make it the full length, right click onto it and select "Customize Panel".

Now select "Fixed Position" radio button, and then select "Full Width" in the gtk drop down menu that's below the Freely Moveable radio button.

Adjust size in the Appearance Size Pixels.

You can add a second panel for the top also.

Now for the clock, right click it and select "Add New Item". Scroll through the list (about 6 items down) and add the clock. Or scroll about 15 items down and select "Orage Clock" which I like better because it has a calendar.

Also...Don't give up big-chip, everything gets really easy soon.

---

### Post by Happy_Man on 2007-05-15
Oh, and btw, the auto-adjust is on your monitor menu, not part of the OS. But then, you're running a Mac, so you wouldn't have it.... nvm.

---

### Post by crimesaucer on 2007-05-15
> **big-chip said:**
> no still no results :(

Maybe this is a sign form the linux gods telling me to keep to osx

You should start a new thread for the more experienced moderators to help you with. You should explain your problems from start to finish, and I bet someone helps you solve it very quickly and easily.

---

### Post by big-chip on 2007-05-15
Ok sorry i have a mac im typing on here but ubuntu is on an old unused windows laptop i have kicking about so xubuntu is on my pc not mac.

---

### Post by crimesaucer on 2007-05-15
Also, this is a common problem for xubuntu and ubuntu, search the threads about missing panels, these are some threads that helped me:

[http://ubuntuforums.org/showthread.php?t=429563&highlight=gnome+panel+gone](http://ubuntuforums.org/showthread.php?t=429563&highlight=gnome+panel+gone)

and:

[http://ubuntuforums.org/showthread.php?t=352685&highlight=panels](http://ubuntuforums.org/showthread.php?t=352685&highlight=panels)

But to have the panel there after a reboot, I think you need the & sign after it like I put:

```
xfce-panel &

```

---

### Post by helgi on 2007-05-15
Thanks crimesaucer. This has been helpful.

---

### Post by crimesaucer on 2007-05-15
No problem.

---

### Post by big-chip on 2007-05-15
Indeed thank you for your help. :)

Alas i still cant get the panels up so i have started a nwe thread with as much info as i can on them. Hopefully someone can help this isnt a great start for linux but im quite enthusiastic to struggle through as its this or windows.

---

