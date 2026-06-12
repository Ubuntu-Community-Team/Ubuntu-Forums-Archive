---
title: "What the xorg.conf can do to you? Careful with this..."
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by donamai on 2007-03-24
Hi, Like everyone else in here I have no knowledge of Linux at all.


I installed Ubuntu 6.10 yesterday I encounter bugs a long the way but finally I was able to get it up and running. 

**Situation**

Since I have to screens, I wanted to set both to work with this operating system. Yeah! I dared to move forward and not wait to learn a bit about Linux. 

**Problem:**

So my problem is that I read this thread where it says that I could make two monitors work. I have a  dual head Matrox G400 card installed. So I followed the advice and read the instructions to the letter but somehow I made a mistake somewhere in the following file.

gksudo gedit /etc/X11/xorg.conf


Check the this link for the instructions I followed:

[http://ubuntuforums.org/showthread.php?t=301961&highlight=matrox+screen+setup](http://ubuntuforums.org/showthread.php?t=301961&highlight=matrox+screen+setup)


**What I did:**

So I followed the instructions but again I think I made an unseen mistake. Now the problem is that when I turn the computer on I get an error in a blue square telling me of the error.

[B]My questions:
[/B]
Is there a way to re-start the computer and set the setting to default?

Is there a command that I have put in if I go to the recovery choice at the startup?

What is the best way to solve this problem without re-installing the software again?


I would appreciate any help you could provide.

here is a screen shot I took with my everywhere-camera.

[IMG]http://www.geocities.com/runonplace/one.jpg[/IMG]

[IMG]http://www.geocities.com/runonplace/two.jpg[/IMG]

---

### Post by jbayone on 2007-03-24
Reboot in recovery mode, then ```
sudo dpkg-reconfigure xserver-xorg
```
Go through all of that, then ```
sudo /etc/init.d/gdm start
```

---

### Post by LookTJ on 2007-03-24
or ctrl+alt+f1, login

```
sudo dpkg-reconfigure xserver-xorg
```or edit yourself

```
sudo nano /etc/X11/xorg.conf
```

then after you edited it

```
sudo /etc/init.d/gdm restart
```

ctrl+alt+f7

---

### Post by donamai on 2007-03-24
Thank you  jbayone and Taylor

I am grateful for your collaboration and help. I mentioned that I don't know anything about Linux so my questions to you know are:

Where do I have to type that info in? Will i get a prompt? or do I have to wait for any cursor to come up? I used to use DOS a long time a go so I am familiar with command lines but on here I am in the dark as to where I have to put the commands.

I know these are the most simple questions but I am extremely new to this language. I am sure  one day I will look back and say. Darn it! what was I asking?:(  but in the mean time I have to lower my head and ask for guidance.

Thank you for the help.

By the way, where do you guys find cool avatars here? I have seen members have great images!

---

### Post by khedron on 2007-03-24
As soon as you boot up, you should get a menu of the OS's you have installed. (This is the Grub menu, if you know what that is.) Somewhere on that list there should be a "Recovery Mode" option. Select that with the arrow keys and press enter. You should eventually get into a command line.

Then type in ```
dpkg-reconfigure xserver-xorg
``` and go through the menu until it finishes. Then type in ```
shutdown -r now
``` and let the computer reboot. The error shouldn't appear now.

---

### Post by kelbizzle on 2007-03-24
> know these are the most simple questions but I am extremely new to this language. I am sure one day I will look back and say. Darn it! what was I asking? but in the mean time I have to lower my head and ask for guidance.

Thank you for the help.

By the way, where do you guys find cool avatars here? I have seen members have great images!

Just stick with it linux is great. as for avatars. I got mine from google images with a search for marley. try  a search for "linux xp" that might bring some good stuff.

---

### Post by donamai on 2007-03-24
Man! you guys are fast!

I will try the solutions you guys provided.[http://www.ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://www.ubuntuforums.org/images/smilies/new_popcornsmiley.gif)
:popcorn:

Let you know of any error or success.

---

### Post by IYY on 2007-03-24
> Where do I have to type that info in? Will i get a prompt? or do I have to wait for any cursor to come up? I used to use DOS a long time a go so I am familiar with command lines but on here I am in the dark as to where I have to put the commands.


As mentioned above, Ctrl+Alt+F1 will give you a console, and Ctrl+Alt+F7 will take you back to a GUI. This is good to know whenever your system appears to be stuck: chances are it's just the GUI that's stuck, and the system itself is still fully functional.

---

### Post by donamai on 2007-03-24
Thank you again for the help. I could manage to fix the problem but I think that I passed the  information on the menu choices that come up after the first command is in. In other words, during the menu that comes up for the xorg server I did know what information to type in or accept. 

Now I think that computer system sees my card as just a Generic Screen monitor and there is a delay with the the scrolling when browsing the internet.  

Also, my mounted hard drives had the names of the Operating system (which I had name with in the other OS I have installed) and this names would show up on the screen once the system was loaded. Now, they each show the hd1 numbers sequentially but I am not worry about that yet.

Thank you again. I will learn this info as soon as possible.

Take care!

---

