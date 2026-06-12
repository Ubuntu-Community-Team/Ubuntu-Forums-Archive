---
title: "Don't know how to setup tilda"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-03-07
Hi guys,

I've recently installed Tilda with aptitude. But I don't know how to get it running :(

I know this brings up the configuration editer:

```
tilda -C
```

But how do I set the keybindings? It seems kinda funny, when I click on the keybindings tab, and on the empty box there, its kinda like a text box, not a box that records what I click(i.e. I hit "F1" and "F1" appears on the box), so I'm kinda manually typing in "F1" into that box. And that doesn't work. Am I missing some step?

I launch the program by using (from the terminal):

```
tilda&
```

If I were to set it up to launch every startup, would that be the same code I'm supposed to run at start up?

Any help would be great, thanks :)

Kinson

---

### Post by SuSUntu on 2007-03-07
I understand what you mean about the config applet not auto-capturing your keystrokes.

But, as you have guessed, you simply type the keys in manually. For example, my keybinding is usually:

```

Alt+z

```

I believe 'None+F1' is the default, and that appears to be what you are trying to achieve by just typing in 'F1' which doesn't work because I'm pretty sure that Tilda is expecting a format of:

Key1+Key2

where Key1 = None or Control or Alt or Win (or similar keys) and where Key2 is any other key (most other keys?). So these are valid:

Alt+d
Win+l
Control+x
None+F2
Alt+grave (grave is the tide (~) to Tilda)

F1 (None+F1) in Ubuntu is mapped to 'Help', so it's best to choose a keybinding not already in use by another program otherwise you lose some functionality (if you don't care about 'Help', then no big deal).

To start Tilda when your session starts, just add:

```

tilda

```

To Main Menu > System > Preferences > Sessions: Startup Programs: Add

Edit:

The & symbol is used in the terminal to return control to the terminal after launching an application without waiting for that application to terminate, so it is not applicable to launching Tilda at start-up via Sessions.

Edit 2:

If you have applied or are going to apply any MetaCity animation removal tweaks, you may want to read my post here:

[http://ubuntuforums.org/showthread.php?t=368795](http://ubuntuforums.org/showthread.php?t=368795)

as the tweaks cause some conflicts with Tilda. Although I didn't post this fact in the above thread, I got rid of the terrible MetaCity animations by not using MetaCity altogether. I now run XFWM (the XFCE Window Manager) on top of Gnome. It works great, it's fast, it looks good, it has compositing, and it doesn't have MetaCity's ugly animations. :)

---

### Post by kinson on 2007-03-07
Yeah, it did come in the format "None+F1". I guess I changed it with me itchy fingers :P It didn't make much sense to be back then.

> F1 (None+F1) in Ubuntu is mapped to 'Help', so it's best to choose a keybinding not already in use by another program otherwise you lose some functionality (if you don't care about 'Help', then no big deal).

I hate the help window popping up if I accidently hit the F1 key anyways, cause it takes a couple of seconds, and it wastes my time, so no loss there(using None+F1) ;)

I'll give it a try again tonight with the advice you gave me (I'm at work now).

I new to this, so I don't realli know what metacity is, so I don't think I did anything to it :P

Cheers,
Kinson. (Hopefully I'll have good news tonight ;) )

---

### Post by kinson on 2007-03-08
Hi, I've managed to get the "None+F1" working, but I've still a few questions :/

#1
When I set transparency(this happens with the normal terminal as well), instead of it being "transparant", its actually just using the desktop background. Its fine if I'm using it on a desktop with windows all minimized, but if I use it while using firefox...its weird...kinda looks like I've got a portion on my desktop on firefox :/

#2
I've changed some of the display settings for tilda (green font on black background), And when I click "apply/ok", it applies it, but when I kill tilda or run it again, its back to white font on black background? but when I type "tilda -C", it says that its green font on black background :confused: 

Cheers, and thanks for the help :)
Kinson

---

### Post by SuSUntu on 2007-03-08
> **kinson said:**
>  ... I've still a few questions :/

#1
When I set transparency(this happens with the normal terminal as well), instead of it being "transparant", its actually just using the desktop background. Its fine if I'm using it on a desktop with windows all minimized, but if I use it while using firefox...its weird...kinda looks like I've got a portion on my desktop on firefox :/


Transparency in Gnome / Metacity is not true transparency. As you have noted, it is simply an image of the underlying desktop. The ill effects of such a scheme is exacerbated if you use a complex or busy image for your wallpaper. That's not the fault of Tilda, it has to do with the capabilities of your desktop / windows manager. I use XFWM as my windows manager (as a replacement for Metacity) in Gnome. It provides for compositing (true transparency and shadows) and Tilda adapts to this environment quite well. The setup is not complex and uses the built-in AIGLX. You could also use Enlightenment or go the full-blown eye-candy route of Beryl / XGL Beryl / AIGLX. I'm not much into all the fancy stuff, so I haven't bothered with Beryl yet.     

> **kinson said:**
> 
#2
I've changed some of the display settings for tilda (green font on black background), And when I click "apply/ok", it applies it, but when I kill tilda or run it again, its back to white font on black background? but when I type "tilda -C", it says that its green font on black background :confused: 


Sounds like Tilda is being run as one user and the configuration utility is being run as another, thus when Tilda runs its still picking up the default settings. Otherwise, I can't explain that behavior.

Here's my suggestion though:

- close Tilda
- delete your /home/username/.tilda folder (which contains the configuration file(s)) 
- now, instead of running 'tilda -C', just run 'tilda'. This will automatically launch the configuration utility because Tilda won't find your configuration file since you deleted it (if Tilda doesn't find a config file, which usually occurs the first time you run Tilda, the config utility is automatically launched)
- set up your preferences again and see if that doesn't make things "stick"

---

### Post by kinson on 2007-03-08
I followed your steps and It seems to work so far, thanks :)

After I closed tilda, I ran it again, and it said:
```

kinson@ubuntu:~$ tilda
Unable to open config file, showing the wizard
: No such file or directory
kinson@ubuntu:~$

```

Then I entered the settings and clicked apply. And so far its working :)

Btw, when you say kill tilda. Is it bad to close tilda by using:
```

ps aux | grep tilda
kill <job number>

```

I *just*realized I could have just typed "exit" from tilda, but since I'm already typing this, I might as well asked :P Cause I read in another thread that its not good to close programs this way.

Cheers,
Kinson

---

### Post by SuSUntu on 2007-03-08
> **kinson said:**
> I followed your steps and It seems to work so far, thanks :)

Glad it worked.



> **kinson said:**
> 
Btw, when you say kill tilda. Is it bad to close tilda by using:
```

ps aux | grep tilda
kill <job number>

```

I *just*realized I could have just typed "exit" from tilda, but since I'm already typing this, I might as well asked :P Cause I read in another thread that its not good to close programs this way.


Well, first of all I said 'close' Tilda, not 'kill' Tilda. You used the word 'kill'. :)

Exiting a GUI application via its native exit functionality (usually provided in a menu) is the best way to close it. The main reason is that the application may immediately terminate and may not write out all its memory to disk if kill is used, so you may lose data. As an example, if you were killing Tilda in this way all along, it **may** have explained why the config file seemed to reset to default after you terminated / re-launched Tilda. I say **may** have been the cause because not all apps behave the same way ... some immediately write changes out to disk and some may not (the behavior may be intentional or bad programming). NOTE: I just checked Tilda, and it seems that its behavior is to immediately write configuration file changes to disk. 

Anyway, I'm surprised your grep'ing the PID in order to kill an application, especially a GUI app. I think you're making life with Linux too complicated. :) Such a command definitely has a place in scripts or in instances where you have no choice but to use it. If you do find you need to send a kill signal to an application for whatever reason, try in this order (least abrupt to most abrupt):

kill -SIGHUP <PID>
kill -SIGTERM <PID>
kill -SIGKILL <PID>

The reason you may have to try more than one signal is that the app may, for example,  not respond to SIGHUP, but it must respond to SIGKILL.

The named signals' vallues can be substituted in the commands:

-SiGHUP = -1
-SIGTERM = -15
-SIGKILL = -9

Default for 'kill' to send signal SIGTERM (15), so specifying it is optional.

Anyway ... just close your GUI apps via GUI. :)

------
By the way, have a look at 'pidof'. It allows you to find the PID of a process without the grep:

foxpid="$(pidof -s firefox-bin)"
kill -15 $foxpid

Way off the Tilda topic, but since you were looking up PID processes programmatically, I thought I'd throw that one out at you.

---

### Post by kinson on 2007-03-08
> **SuSUntu said:**
> Well, first of all I said 'close' Tilda, not 'kill' Tilda. You used the word 'kill'. :)

Anyway, I'm surprised your grep'ing the PID in order to kill an application, especially a GUI app. I think you're making life with Linux too complicated. :) Such a command definitely has a place in scripts or in instances where you have no choice but to use it.

Anyway ... just close your GUI apps via GUI. :)

------
By the way, have a look at 'pidof'. It allows you to find the PID of a process without the grep:

foxpid="$(pidof -s firefox-bin)"
kill -15 $foxpid

Way off the Tilda topic, but since you were looking up PID processes programmatically, I thought I'd throw that one out at you.

I wouldn't mind killing exiting tilda without the command line, but there isn't a little "X" for me to click on :P So that was the only way I could think of :/

Do *all* apps have an exit command from the terminal? I know I do seem like I'm trying to make my linux life a little more difficult, but I'm a keyboard aficionado, and its one of the reasons why I'm moving to linux. :)

Thanks for suggesting the "pidof" app. I welcome all these suggestions :) I'll give it a try when I can. :)

Cheers,
Kinson

---

### Post by SuSUntu on 2007-03-09
> **kinson said:**
> I wouldn't mind killing exiting tilda without the command line, but there isn't a little "X" for me to click on :P So that was the only way I could think of :/

Do *all* apps have an exit command from the terminal? I know I do seem like I'm trying to make my linux life a little more difficult, but I'm a keyboard aficionado, and its one of the reasons why I'm moving to linux. :)

Kinson

To shut Tilda down without the command line is as simple as right-clicking anywhere within Tilda whenever it is in use and selecting '**Quit**' from the pop-up menu. You'll also notice that '**Quit**' in the menu shows the equivalent  keyboard shortcut as '**Ctrl+Q**'.

That should actually be '**Shift+Ctrl+Q**' which is the same shortcut for closing the gnome-terminal window (at least I couldn't get plain '**Ctrl+Q**' to work in Tilda, and it makes sense that the shortcuts would be compatible between gnome-terminal and Tilda).

Plain '**Ctrl+Q**' does work for closing lots of Gnome apps (from within the app) but it is not universal. Just learn the appropriate shortcuts for your favorite apps if you don't like the menus or the window control icons in the apps titlebar for closing your GUI programs.

Now, as far as your question regarding closing apps launched from the terminal (I assume that's what you meant when you asked about an 'exit' command from the terminal):

- if you launch an app, for example 'gedit', from the command line with '**gedit**' (no ampersand), then a universal keyboard shortcut (from within gnome-terminal) to close the app would be '**Ctrl+C**'.

-  if you launch an app, for example 'gedit', from the command line with '**gedit &**', then you will have to use other means to close the application because the ampersand returns control of the command line back to the user and puts the launched application in the [terminal] background. To stick with the terminal (as opposed to simply closing the app from within the GUI), you would issue the '**fg**' command to bring the application back to the foreground, and then you could at this point issue '**Ctrl+C**' from within the terminal to close the application.

Using '**Ctrl+C**' from the terminal, however, results in the same concerns about closing an application with '**kill**'. For example, using the application-specific shortcut from within the app will generally prompt you with a 'save confirmation' (if you have your apps set that way and if the app supports such functionality); however, if you close the application launched from the terminal with '**Ctrl+C**' from within the terminal, the app just closes. If you have unsaved documents open, too bad.

Sorry it took me so long to get back to you on this. But, at any rate, this seems all so academic when it is easier and generally safer for your open documents to just close the GUI app from within the GUI environment. I understand your reasoning for liking Linux because of the command line and keyboard shortcuts, but if you are using a Linux desktop environment and GUI apps, you should use them as they were designed to be used. That doesn't mean that you can't use the keyboard, as most GUI apps have a nice compliment of keystroke combos you can use to control various aspects of their functionality.

---

### Post by kinson on 2007-03-10
> **SuSUntu said:**
> Just learn the appropriate shortcuts for your favorite apps if you don't like the menus or the window control icons in the apps titlebar for closing your GUI programs.


If I type "man tilda", the only commands it returns are "-T" and "-C" :( (No quit command).

> 
Sorry it took me so long to get back to you on this.

No problem whatsoever. This forum had the absolute best response time I've ever seen anywhere. I'm grateful for any help that comes my way :) (thanks btw :) )

> 
 But, at any rate, this seems all so academic when it is easier and generally safer for your open documents to just close the GUI app from within the GUI environment. I understand your reasoning for liking Linux because of the command line and keyboard shortcuts, but if you are using a Linux desktop environment and GUI apps, you should use them as they were designed to be used. That doesn't mean that you can't use the keyboard, as most GUI apps have a nice compliment of keystroke combos you can use to control various aspects of their functionality.

Yeah, perhaps I was taking the whole "keyboard" thing a bit too far. I guess I kinda forget that I am using GUI apps as you said, and not working directly from a terminal. I suppose I took the term "you can do everything from the command line" a bit to literally, heheeh :p But seriously, I get what you mean :) GUI apps are meant for GUI environments, so their controls will most likely be geared towards GUI(buttons, etc). :)

Thanks a million :)
Kinson

---

### Post by wilberfan on 2007-03-18
I just installed Tilda on Feisty (Herd 5) and I think I've got it figured out -- but when I set it to 'transparency', the letters disappear as I type them...!   All seems fine if I turn that off.   (I don't have beryl, or anything like that installed...  yet!)

Any idea what could be going on here?

---

### Post by kinson on 2007-03-18
Apparantly there's some problem with transparency with GNOME. If you read back a couple of posts, there's a post from SuSuntu explaing it in more detail. You'll probably find his answer more enlightening than mine :p

Cheers,
Kinson

---

