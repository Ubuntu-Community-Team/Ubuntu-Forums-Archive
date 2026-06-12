---
title: "How do I change my current window manager?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-06-01
I never knew that I can use a different window manager for a desktop environment until I saw this thread--> [http://ubuntuforums.org/showthread.php?t=457423](http://ubuntuforums.org/showthread.php?t=457423) .

How do I change the Window Manager for KDE and GNOME?

---

### Post by arochester on 2007-06-01
To get KDE use the command: > sudo apt-get install kubuntu-desktop

To get Gnome use the command > sudo apt-get install ubuntu desktop

On the screen where you log in the icon on the left, like a page, will allow you to choose the kind of session you want

---

### Post by seshomaru samma on 2007-06-01
To install icewm run this command:```

sudo aptitude install icewm icewm-themes
```
basic tutorial [here]("http://forums.debian.net/viewtopic.php?t=5450")
if you want desktop icons
```
sudo aptitude install idesk
```

the command for fluxbox is probably 
```
sudo aptitude install fluxbox
```
basic tutorial [here]("http://forums.debian.net/viewtopic.php?t=5382")


if you want to change your WM just log out and choose a new WM in the logon screen

---

### Post by AndyCooll on 2007-06-01
And continuing on the desktop environments. To install Xubuntu:

```
sudo apt-get install xubuntu-desktop
```

:cool:

---

### Post by wersdaluv on 2007-06-01
> **seshomaru samma said:**
> To install icewm run this command:```

sudo aptitude install icewm icewm-themes
```
basic tutorial [here]("http://forums.debian.net/viewtopic.php?t=5450")
if you want desktop icons
```
sudo aptitude install idesk
```

the command for fluxbox is probably 
```
sudo aptitude install fluxbox
```
basic tutorial [here]("http://forums.debian.net/viewtopic.php?t=5382")


if you want to change your WM just log out and choose a new WM in the logon screen


Can I run IceWM or Fluxbox on KDE or GNOME?

---

### Post by rillip on 2007-06-01
arochester: This isn't what he's trying to do, actually.  He's trying to stop using metacity and use a different Windows manager in those two desktop environments.

Now, as to how to do that... well, I'm honestly not sure.  A quick search of the forum revelead a lot of threads like this, where someone asks about the window manager, and people start throwing around gnome/kde talk.  Seems like most don't adventure into replacing metacity.  I'd recommend you try a google search, I'm sure there's a guide out there somewhere.

The only way I did find to do it is to install Beryl, as it has is own windows manager, however, that's a lot of extra baggage too, and only has one. You'd install it the same way you do any other program, then unistal when done.  Not sure if you can switch between them or not.

Edit: yes, you can run IceWM or Fluxbox on them.

---

### Post by GrueTamer on 2007-06-01
I've done this before.  The window manager that I used with gnome at first was enlightenment.  Enlightenment automatically makes session entries for E-Gnome and E-KDE.  To get it, type ```
sudo apt-get install enlightenment
```

Another thing to try if you already have the window manager installed is the --replace command.  I've found that this works better in E-Gnome.  But, for instance, to use icewm with Gnome, inside of E-Gnome, you would do ```
icewm --replace
```

I'm sure you can change window managers in Gnome+metacity (default Gnome), but the process has proved to be harder when you don't want to change to something like compiz or beryl.

---

### Post by AndyCooll on 2007-06-01
Ahhh ...made the mistake of confusing "Window Manager" with "Desktop environment". As mentioned in a post just above, he wants to change from Metacity to something else (_not_ GNOME to KDE etc)


I found this awhile ago and copied these notes. I haven't actually tried them yet though, so I can't vouch for their accuracy!
> How do I change my default Window Manager that starts when I run startx?

The default for all users is set in /etc/X11R6/blah/blah so only edit this if you want to change it for everyone. The best way is to override this setting if you want to change your own window manager is to create a file in your home directory called .xinitrc and contains:

exec openbox

obviously change “openbox” to your desired window manager. You can use the following options depending on which Desktop Environment/Window manager you wish to be the default:

KDE, all versions:
exec startkde

GNOME 1.x or 2.x depending on which you have installed:
exec gnome-session

Blackbox:
exec blackbox

Fluxbox:
exec fluxbox

Enlightenment:
exec enlightenment

Windowmaker:
exec windowmaker

:cool:

---

### Post by seshomaru samma on 2007-06-01
> arochester: This isn't what he's trying to do, actually. He's trying to stop using metacity and use a different Windows manager in those two desktop environments.
is he? in the link that he posted the suggestion was to replace gnome with another windows manager

---

### Post by ggaaron on 2007-06-01
> **seshomaru samma said:**
> is he? in the link that he posted the suggestion was to replace gnome with another windows manager

Gnome isn't a window manager - it's a desktop environment - metacity is a window manager for gnome.

Search for beryl and how to use it - beryl is a window manager, just don't download/install it, but it the guide you'll find where you should place for example kwin/metacity/fluxbox to have it started every time you start X.

---

### Post by wersdaluv on 2007-06-01
I'm sorry if my first post is hard to understand, but what I intended to ask was how to use a window manager which is not running by default in a desktop environment.

---

### Post by wersdaluv on 2007-06-01
I guess Beryl really is the app to do the job, but since my laptop cannot run Beryl, I find it inconvenient to install it just to change the window manager. I hope there is a better solution.

---

### Post by wersdaluv on 2007-06-01
That looks like what I have been looking for but no such folder as /etc/X11R6/ exists in my computer.

---

### Post by ggaaron on 2007-06-01
No,no you don't have to install beryl - just follow the instructions you know changing every beryl for example to kwin. Maybe I'll make it clearer:
```
 Using KDE

KDE's window manager can be defined in an environment variable. Modify:
File: /etc/env.d/99kde-env OR /etc/env.d/*kdepaths*

KDEWM=/usr/bin/beryl

Then, update your environment:

# env-update

```
```
 Gnome Session Manager

In Gnome Panel under System/Prefs choose Sessions. Then go to Startup, use the plus sign for add and type in

beryl-manager 

Thats it.
[edit]
GDM

# mkdir -p ~/.config/autostart
# nano -w ~/.config/autostart/beryl-manager.desktop

The contents for beryl-manager.desktop are:

[Desktop Entry]
Name=No name
Encoding=UTF-8
Version=1.0
Exec=beryl-manager
X-GNOME-Autostart-enabled=true

```
```
We need to get Beryl-Manager to start after Xfce4. To do so we need to add the following to $HOME/.config/xfce4/xinitrc. The following code should work with either startx or xdm.
File: $HOME/.config/xfce4/xinitrc

 beryl-manager 2>&1 >$HOME/.beryl-log &
 emerald 2>&1 >$HOME/.emerald-log &
 exec sh /etc/xdg/xfce4/xinitrc


```

This are the sections that are relevant - change beryl to any other window manager in this sections - it's just a way to run any window manager as the primary one, in case I have missed anything in this sections here is the original text:
[http://gentoo-wiki.com/Beryl#Using_KDE](http://gentoo-wiki.com/Beryl#Using_KDE)

---

### Post by ggaaron on 2007-06-01
In fact I use KDE, and from what I can tell it's easiest to change window manager there...

---

### Post by wersdaluv on 2007-06-01
There is no such file as "/etc/env.d/99kde-env" or  "/etc/env.d/" on my Kubuntu. :(

---

### Post by extremecarver on 2007-06-01
May I join in this thread?
Somehow enlightenment started default for me (it was installed since ages) and I thought well if it allways runs on default and keyring and several other things don't work (meaning no internet) I uninstalled it completely.
Now startx produces an empty screen. How can I go back to metacity?
(at least I dual boot to MS Windoze so I can write here).

---

### Post by AndyCooll on 2007-06-02
> **wersdaluv said:**
> That looks like what I have been looking for but no such folder as /etc/X11R6/ exists in my computer.

Try /etc/X11 instead. I think those notes were Debian and XFree related. Hopefully the principles remain.

:cool:

---

### Post by wersdaluv on 2007-06-02
What exactly is the file under /etc/X11 should I edit?

Also what I am trying to do now is to use xfce's window manager in GNOME. How do I do it?

:KS

---

### Post by wersdaluv on 2007-06-04
I figured the answer out!

First, download the Window Manager.

Then, just create a file named ".gnomerc" under your user folder containing this text
```
export WINDOW_MANAGER=/usr/bin/*name of Window Manager*
```

or simply enter this code in the terminal
```
echo export WINDOW_MANAGER=/usr/bin/*name of window manager* >> ~/.gnomerc

```

Enjoy!

---

### Post by urukrama on 2007-06-04
I don't know if this has been mentioned yet, but if you install the latest version of Openbox, available [here]("http://icculus.org/openbox/index.php/Main_Page"), you can very easily log into gnome or kde with openbox as a window manager. You'll have entries in your 'sessions' menu in K/GDM for 'Gnome with Openbox' or 'KDE with Openbox. More information on the openbox site (which seems to be down...)

---

