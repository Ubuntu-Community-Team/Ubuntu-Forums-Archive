---
title: "Appearance Problems"
date: 2012-07-16
forum: Any Other OS
---

### Post by BBaumer on 2012-07-16
I'm having a couple issues related to appearance.

[LIST]
[*]I cannot click and drag windows with my cursor.
[*]The Minimize, Maximize/Restore and Close buttons do not show up on my windows.
[*]In Firefox, when I click on a menu item and move my cursor down, the menu automatically collapses. There is no issue with lateral movement and I can use the arrow buttons to manually raverse the menu list. This issue does not occur when I navigate the menu in the Home Folder.
[/LIST]The theme I am using is called "Slickness-Black". I can tried changing the icons, and changing the theme. No Joy. I'm left with the same symptoms. What should I do to resolve this?

---

### Post by Frogs Hair on 2012-07-16
What Ubuntu version ? Slickness Black is a GTK 2.xx theme and the latest version 12.04 uses GTK 3.4 .

---

### Post by BBaumer on 2012-07-16
I'm running Backtrack 5 R2.

---

### Post by BBaumer on 2012-07-16
I've ben playing with Firefox some more, and got the window to move. However, I've found that if I double click empty space in the upper boarder, it causes the application to crash.

---

### Post by Frogs Hair on 2012-07-16
Sorry , I have never used Backtrack.

---

### Post by Toz on 2012-07-16
Which desktop environment are you using? Xfce, gnome, kde? It sounds like the window manager has crashed and needs to be restarted.

---

### Post by BBaumer on 2012-07-17
> **Toz said:**
> Which desktop environment are you using? Xfce, gnome, kde? It sounds like the window manager has crashed and needs to be restarted.
 
I'm using GNOME. How do I restart the window manager?

---

### Post by Toz on 2012-07-17
I don't have a backtrack install available to check. Which version of Gnome does it use? 2, 3, or one of the forks MATE or Cinnamon?

I believe the window manager for gnome 2 was metacity:
```
metacity --replace &
```

---

### Post by BBaumer on 2012-07-17
Is it version 2.30.2, distibuted be Ubuntu. The build date is 6/25/2010.
 
I ran your code, and it appeared to work for a minute. The buttons appeared (on the top left, though, instead of top right). I tried launching Firefox and it opened full screen, as expected. When I tried close the terminal and browser windows though, it appeared to crash again. The buttons disappeared, and the windows did not close. When I right click on the application at the bottom of he screen and choose Close, nothing happens (none of the options respons).

---

### Post by madjr on 2012-07-17
can you attach a pic (hit the prt-sc key)

---

### Post by BBaumer on 2012-07-17
> **madjr said:**
> can you attach a pic (hit the prt-sc key)
 
I'm trying, but I don't think so. the Prnt Scrn is a dual function key (F11), requiring the Fn key to be pressed first. I don't think that works (I don't know if it did prior to this crop of issues).
 
I'll have to take pics with my iPhone. I can make a vid too, so you can watch the symptons as they play out. I don't know if I can attach a vid here or not though.

---

### Post by Toz on 2012-07-17
> **BBaumer said:**
> Is it version 2.30.2, distibuted be Ubuntu. The build date is 6/25/2010.
 
I ran your code, and it appeared to work for a minute. The buttons appeared (on the top left, though, instead of top right). I tried launching Firefox and it opened full screen, as expected. When I tried close the terminal and browser windows though, it appeared to crash again. The buttons disappeared, and the windows did not close. When I right click on the application at the bottom of he screen and choose Close, nothing happens (none of the options respons).

Try running it from either the run dialog (which should be Alt+F2) or with the nohup command so it can survive the terminal close:
```
nohup metacity --replace &
```

---

### Post by BBaumer on 2012-07-17
The vid is a no-go. Can't make it small enough for a zip file. Shoot me a message if you want work out a solution on the side to pass you the file.
 
Here are some photos I've taken of the static issues (obviously I can't capture the menu/cursor problem). Sorry for the poor quality - but I wanted to capture something...
 
The last two photos are a new symptom. When I click on the Firefox window, all the menu bars and what not disappear. In order for them to return, I have to move my cursor over the top left corner. The craziness continues...

---

### Post by BBaumer on 2012-07-17
> **Toz said:**
> Try running it from either the run dialog (which should be Alt+F2) or with the nohup command so it can survive the terminal close:
```
nohup metacity --replace &
```
 
Cool, so this seemed to work. I opened an closed different windows a couple times and it all seemed to be working as advertised. 
 
When I logged out and logged back in though, the problem returned.
 
What is "nohup", and what should I try next?

---

### Post by madjr on 2012-07-17
maybe wise to upgrade to a newer version.

I had some of that stuff happened to me a few times when I was tinkering around :D

but is hard to pin point what messed up, so I just install a new version.

if you backup and reinstall you probably good to go in an hour or less!

You can try a newer **ubuntu like 12.04 (unity) or xubuntu 12.04 (xfce).**

but if you want to stay with the old gnome, try gnome-fallback or maybe even a fork called "Mate".

for classic gnome fallback (and other tweaks):

[http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html)

or install mate in ubuntu:

[http://www.webupd8.org/2012/04/mate-desktop-12-released-install-it-in.html](http://www.webupd8.org/2012/04/mate-desktop-12-released-install-it-in.html)


Else, you can also reinstall BackTrack if you think you still need it. But any distro you plan to tinker around a lot is better to keep in a separate hard drive partition and not your main partition in case you break something and need to reinstall quickly.

good luck!

---

### Post by Toz on 2012-07-17
> **BBaumer said:**
> Cool, so this seemed to work. I opened an closed different windows a couple times and it all seemed to be working as advertised. 
 
When I logged out and logged back in though, the problem returned.
 
What is "nohup", and what should I try next?

Try adding it to your startup programs. IIRC, Control Panel->Sessions->Startup.

Just add it as:
```
metacity
```
...and see if that works.

---

### Post by BBaumer on 2012-07-17
> **Toz said:**
> Try adding it to your startup programs. IIRC, Control Panel->Sessions->Startup.

Just add it as:
```
metacity
```...and see if that works.

 I'm not tracking. I can open the start list as follows: System > Preferences > Startup Applications. From there, I don't understand how to add a terminal command as I think you've suggested. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif) Sorry, I'm a n00b.  As for reinstalling, I need to keep the Backtrack distro as I'm using it as a security testing platform for work.

---

### Post by Toz on 2012-07-17
> **BBaumer said:**
> I'm not tracking. I can open the start list as follows: System > Preferences > Startup Applications. From there, I don't understand how to add a terminal command as I think you've suggested. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif) Sorry, I'm a n00b.  As for reinstalling, I need to keep the Backtrack distro as I'm using it as a security testing platform for work.

Sorry, but I'm doing this all from memory. If you click Add, you should get a dialog box. Enter **metacity** for both the name and the command. Click Add again.

---

### Post by BBaumer on 2012-07-17
*** SOLVED ***  Thanks for your assistance. Adding metacity to the list of startup programs solved the problem. I'm good with this for now, though I don't think it has actually *solved* the issue, but is rather a work around.

---

