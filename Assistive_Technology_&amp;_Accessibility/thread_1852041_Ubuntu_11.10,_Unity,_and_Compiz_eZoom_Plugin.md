---
title: "Ubuntu 11.10, Unity, and Compiz eZoom Plugin"
date: 2011-09-29
forum: Assistive Technology &amp; Accessibility
---

### Post by RKCole on 2011-09-29
Hello, everyone.

Ubuntu 11.10 is due to be released here very soon, and I would like to upgrade to it. I have been wanting to use Unity to test it out since it was first available. I heavily rely on the Compiz eZoom magnification plugin so that I may effectively use my computer system.

In Ubuntu 11.04, eZoom was able to zoom the desktop area, but the Unity panel and dock stayed zoomed out. Does anyone know if this has changed in Ubuntu 11.10?

I would test this myself, but I do not have a testing machine for this purpose at this time.

Thanks for any input which can be offered.

Take care.

---

### Post by ohm314 on 2011-10-15
Hi RKCole,

I just upgraded to 11.10 and am happy to say that the Compiz enhanced zoom still works! It still behaves the same as in 11.04. Just make sure when logging in to not choose "Unity 3D" as your desktop (but quite honestly, I'm not seeing the difference yet :) )

best,

-o

---

### Post by RKCole on 2011-10-15
Hello, ohm314.

So, Compiz eZoom works with Unity 2D?

When you zoom in, is the desktop area the only area zoomed, or does the Unity Dock and top panel zoom in as well? I know that with Unity 3D the top panel and dock remain un-zoomed, and that only the desktop area is zoomed in.

Thanks for the reply.

---

### Post by Pendulum on 2011-10-16
I just wanted to put a note out there that the problem with the eZoom Plugin is a Unity issue that applies to most, if not all, Compiz plugins. It's something that I know the accessibility team is really pushing to get fixed for 12.04. (I, for one, plan on bugging the Unity developers in person at UDS about it ;-) )

---

### Post by RKCole on 2011-10-16
Hello, Pendulum.

Thanks for the reply, and thanks for your concern with this situation; I kind of felt like I was a lost cause. :)

My biggest frustration is that I am too inexperienced to do anything about the whole zooming issue in Unity. I always like to have the latest Ubuntu release installed, but without complete magnification Ubuntu 11.10 *would be* almost unusable to me. I wish that I had more experience with tracking bugs and such (I am trying to learn)--debugging, finding associated logs, etc--so that I could be a help to the community rather than juI am primarily a screen magnifier user, but I did install Ubuntu 11.10 on my laptop (I will not install it on my primary desktop yet) so that I could try out Orca (I know enough to be able to get it going without having to look at the screen :) ), and I must say that it does a really great job right out of the box. I was able to connect to my wireless network, install additional drivers, browse the Web (although I think the latest version of Firefox has caused a few minor issues), run commands in the terminal, check my e-mail via Thunderbird, and a few other things (I didn't have a whole lot of time to try it out). I am very impressed!st getting frustrated because something is not working the way it is supposed to. I really want to learn all of this sort of thing.

I will say this, though...

I am primarily a screen magnifier user, but I did install Ubuntu 11.10 on my laptop (I will not install it on my primary desktop yet) so that I could try out Orca (I know enough to be able to get it going without having to look at the screen :) ), and I must say that it does a really great job right out of the box. I was able to connect to my wireless network, install additional drivers, browse the Web (although I think the latest version of Firefox has caused a few minor issues), run commands in the terminal, check my e-mail via Thunderbird, and a few other things (I didn't have a whole lot of time to try it out). I am very impressed with Orca's performance! I hardly ever used my laptop because I couldn't see the screen, and I would have to break my neck to use a screen magnifier on it. Now I can actually use it! And better yet, I can use Linux on it!! so I am going to keep learning Orca and make an adventure of it; it will save a lot of eye strain in the long run.

Thanks again for your concern, Pendulum. It is much appreciated.

Take care.

---

### Post by kubulai on 2011-11-18
The eZoom appears to mostly work now in Unity after updating today. A reboot was required for the changes to take effect. [http://jdnash.com/2011/11/ubuntu-zoom-now-works-sort-of-in-11-10/](http://jdnash.com/2011/11/ubuntu-zoom-now-works-sort-of-in-11-10/)

---

### Post by linbetwin on 2011-11-18
Is Unity 2D magnified by the Enhanced Zoom plugin or do the launcher and the panel stay unmagnified, as in Unity 3D?

And another question, for people who use magnification: How do you manage without text insertion focus? I use a pretty big magnification factor which means that I have to pan after every word I write. Because this would slow me down a lot, I still can't use Linux. I use Windows 7 and the built-in magnifier. How do you make Enhanced Zoom follow your text insertion or what "tricks" do you use to be able to see what you are writing?

---

### Post by RKCole on 2011-12-22
Hello, linbetwin.

I can't personally say how well eZoom works in Unity2D; I will have to test it out. 

As far as focus tracking goes, I believe that this is something which is in the working for Ubuntu 12.04. focus tracking/keyboard tracking, as far as I understand, is also in the working for a later release in the GNOME 3.x series. I have loved working with Compiz eZoom over the years, but (for some reason) as of around Ubuntu 10.04 it did not zoom in as far as it used to. The GNOME shell magnifier, however, allows me to zoom in a whole lot more than I would even need. :)

My eyes have been getting tired much more quickly as of recent months, though, so I have begun to work with Orca. it is coming along, and I am looking forward to seeing how well it will work in the near future.

If I find out anything about Unity2D and the panel/launcher under magnification I will post back here for you.

Take care.

---

### Post by RKCole on 2012-01-21
To linbetwin and anyone else interested,
I was using Linux Mint for awhile because of the magnification issue in Ubuntu, but I found that in some ways Linux Mint was less accessible than Ubuntu. I installed Ubuntu 11.10 back onto my desktop and decided to try with the eZoom plugin again.

Under Unity3D the top panel and launcher dock on the left hand side of the screen still remain unmagnified, but they are actually magnified in Unity2D.

You can do the following to get this working for you.

**NOTE:** Please do not give me the credit for all of the material presented here. [This AskUbuntu page]("http://askubuntu.com/questions/71369/using-compiz-by-default-in-unity-2d") was a tremendous help to me in getting everything working on my system.

**A NOTE FOR FELLOW BLIND USERS**
There is no magnification available until Compiz is enabled and until shortcuts are set for eZoom's Zoom In and Zoom Out features. If you do not have sighted assistance, Orca should do the trick for you in all of the following steps.

First, open a terminal (CTRL+ALT+T is probably the fastest way to do this) and install the Compiz Config Settings Manager (CCSM) package:

```

sudo apt-get install compizconfig-settings-manager

```

Unity2D uses Metacity as its default Window Manager rather than Compiz. You basically have two options at this point:

[LIST=1]
[*]Temporarily use Compiz during your current session
[*]Set Compiz as the default Window Manager for Unity2D
[/LIST]

To temporarily use Compiz during your current Unity2D session, simply press ALT+F2 and then enter this command:

```

compiz --replace

```

This will replace Metacity with Compiz for the current session. Metacity will be restored after logging out and then logging back into Unity2D. If choosing this option, you will have to press ALT+F2 and run the above command to replace Metacity with Compiz each time you login to an Unity2D session.

Your other option is to set Compiz as he default Window Manager so that it will be started automatically when logging into Unity2D. This is slightly more complex than the previous method as you will need to edit a file containing parameters for the ubuntu-2d (Unity2D) session. The file containing parameters for the Unity2D session is located here:

```

/usr/share/gnome-session/sessions/ubuntu-2d.session

```

**WARNING!!** The following steps require you to run commands as the root user. Be sure that you follow the following steps closely, as not doing so could cause problems. I do not believe in giving instructions for a particular task unless I have successfully done it on my own system first; the below steps worked just fine for me.

**ALWAYS PLAY IT SAFE!! MAKE A BACKUP OF YOUR ubuntu-2d.session FILE.** Believe me, I have learned over the years that you can save yourself a lot of pain and trouble by making backups. Before we continue on we will make a backup of the ubuntu-2d.session file, backing it up to our /home directory. Enter the following command to accomplish this:

```

sudo cp /usr/share/gnome-session/sessions/ubuntu-2d.session ~/ubuntu-2d.session.backup

```

If something goes wrong, or if you want the old settings back, you can restore your ubuntu-2d.session file by issuing the following command:

```

cp ~/ubuntu-2d.session.backup /usr/share/gnome-session/sessions/ubuntu-2d.session

```

Now, use your favorite text editor for the following procedure (I used nano out of preference, but any text editor should do. Take note, however, that if using a graphical text editor such as Gedit, you should replace the sudo command with gksudo). For the sake of clarity, I will use nano in the following command, but when you do this on your system just replace nano with your text editor of choice.

```

sudo nano /usr/share/gnome-session/sessions/ubuntu-2d.session

```

Look for the line which reads:

```

DefaultProvider-windowmanager=metacity

```

Replace metacity with compiz (all lowercase letters), and then save your file. From now on, Compiz should start automatically when logging into Unity2D.

At this point, you should have the Compiz Config Settings Manager installed, and you should have Compiz running. So, let's get eZoom up and running.

Press ALT+F2 and enter the following command to run the Compiz Config Settings manager:

```

ccsm

```

By default, eZoom is quite jumpy when run out-of-the-box. This can be easily fixed, and it is the first thing which we will do. In the Filter text box at the top left of the CCSM window, type in the following exactly:

```

polling

```

This will filter out any Compiz plugins which do not contain the word 'polling'.

There should only be one entry, **Mouse position polling**, in the larger part of the CCSM window. Left-click once on this entry to open the Mouse position polling General settings. There should only be one setting which can be altered here--**Mouse Poll Interval**. Just drag the slider which appears in this dialog all the way to the left and that's it! Click on the Back button located at the bottom left corner of the window to go back to the main CCSM window (You can alternatively use the ALT+B keyboard shortcut to do this).

On the left-hand side of the CCSM window, click on the Accessibility tab to display all Accessibility-related plugins. Click on the Enhanced Zoom Desktop icon to open a dialog with settings for eZoom. All that you will need to do here is set the shortcuts for Zoom In and Zoom Out. By default, the Zoom In and Zoom Out features are disabled.

**NOTE:** There are Zoom In/Zoom Out settings for both the keyboard and the mouse. I personally only edit the settings for the mouse, leaving the keyboard settings as "Disabled". 

When setting your Zoom In and Zoom Out shortcuts, you have the option of using any combination of the following keys along with the scroll wheel on your mouse: Shift, Super (the Windows key), Ctrl, and Alt. There is also a combo box in each dialog for the Zoom In and Zoom Out features. I have not tested anything other than Button4 for Zooming In (scrolling the mouse wheel away from you) and Button5 for Zooming Out (scrolling the mouse wheel toward you). For a general example, my settings are as follows:

Zoom In: Shift+Button4
Zoom Out: Shift+Button5

To avoid any possible conflicts, I would advise against using the Super (Windows) key as this key is also used to open the Unity Dash.

If you successfully completed the above steps, then...

**CONGRADULATIONS!!** You should now be able to fully use Unity2D with the eZoom plugin.

**ONE FINAL NOTE:** You may notice that any given window, when maximized, will display its title bar along with what is presented in the global menu bar on the top panel. There are two ways to fix this:

[LIST=1]
[*]Run the following command in a terminal:

```

gconftool-2 -s -t string '/apps/compiz-1/plugins/decor/screen0/options/decoration_match' '!state=maxvert'

```

This will set a Gconf registry key which will disable a feature in the Compiz Window Decoration plugin.


[*]You can accomplish the same thing from within CCSM. Open CCSM and click on the Effects tab on the left side of the window. Open the dialog for the Window Decoration plugin settings by clicking on the respective Window Decorations icon. Find the text box which has **Decoration windows** as its corresponding label. Set its value to:

```

!state=maxvert

```
[/LIST]

Either option you choose, that should do it for you!

Thanks for taking the time for reading this post, and I hope that it has been helpful to you.

---

### Post by RKCole on 2012-01-21
Although magnification is not working properly under Unity3D, I am going to mark this thread as solved because I am successfully using Unity2D with screen magnification, and it works great!

---

