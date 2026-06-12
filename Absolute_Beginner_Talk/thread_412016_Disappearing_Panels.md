---
title: "Disappearing Panels"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by p3_Arme on 2007-04-17
Hiya, Well um, HELP :)  

After I've downloaded stuff I had to restart due to a crash, Now my panels (Top & Bottom) have disappeared. Everything else works, I can right click my mouse and get my usual menu, and everything else works, apart from my panels, I can't even get the panels section in Xfce to open. 

So any suggestions would be helpful. (I can't download as I don't have internet, I have put things onto a Flash Drive, then I transfer them to my HD, or Install them. I had downloaded and Installed xmms, and was transfering other files, when it stopped transfering, I then quit out and restarted, then when it reloaded no panels.)

What have I done?, I can take stick as I'm new to this :) 

Emma

I'm running Xubuntu 6.10.

---

### Post by LaRoza on 2007-04-17
Make new panels and add what ever you want to them. 
Right click and follow the intuitive prompts.

---

### Post by p3_Arme on 2007-04-17
Sorry to be stupid, how do I do that?

---

### Post by LaRoza on 2007-04-17
You can add new panels by right clicking the desktop and selecting "add new panel" or something like that. I do not have Ubuntu in front of me so I can tell for sure.

You can move the panels around the same way you move links. (I have four of them, one for each side of the screen)

You can add apps to the panels by droping their icons on it. You can add other things by right clicking the panel and selecting the option that says some thing like "add to panel". You will get a Window with all sorts of useful, and not-so-useful things. Shutdown is useful, geyes is not, I have both though.

---

### Post by p3_Arme on 2007-04-17
I don't have that option on my menu.

My panels have disappeared altogether...oopps...:) I can't add panels unless there is a way through the Terminal or through another programme. In the Xfce Setting Manager I have a Panels Button, but it wont open or run the program.

Thanks for helping through.

Emma

---

### Post by LaRoza on 2007-04-17
Panels are in Gnome. I don't know about the other desktops. Try using Gnome when you log on.

---

### Post by p3_Arme on 2007-04-17
I apparently have in my Sessions & Startup, in advanced settings Have a Launch Gnome services on startup, which is ticked but I am unsure of where to find it in my menus.

Any help on that would be very grateful :)

Thank you for replying so quick.

Emma

---

### Post by LaRoza on 2007-04-17
Could you send a screen shot? I am confused over what is wrong. I am assuming you are using Ubuntu 6.06 or later, and used the GDE at one point as a default.

Is that all correct?

I have class in a few minutes so I can only stay for a few minutes.

---

### Post by LaRoza on 2007-04-17
Log out and then log back in, if you are not using the Gnome desktop.

---

### Post by p3_Arme on 2007-04-17
Okay trying that

I have 4 options for my session

Last

1. xfce Session
2. Default System Session
3. Failsafe Gnome
4. Failsafe Terminal

I have selected 3. Failsafe Gnome and try that


Nope I don't have GNOME installation It will run the Failsafe xterm instead.

I've restarted, don't worry about it, I'll find another way around it, I could try downloading GNOME. 
I'm running Xubuntu 6.10 and have xfce running as the main system.

---

### Post by strabes on 2007-04-17
Don't know if this will work but try:

```
sudo dpkg-reconfigure xfce4-panel
```

If that doesn't work, then try reinstalling it:

```
sudo aptitude purge xfce4-panel && sudo aptitude install xfce4-panel
```

---

### Post by p3_Arme on 2007-04-17
um I can't connect to the internet, so before I re-install is there anything I need to do?

---

### Post by Brendantb on 2007-04-17
Hi, 

You don't need to reinstall. Just put this in the terminal; code: 

xfce4-panel 

Funnily enough, this was my first problem in Linux! 

[http://ubuntuforums.org/showthread.php?t=352685](http://ubuntuforums.org/showthread.php?t=352685)

---

### Post by p3_Arme on 2007-04-17
Okay, :) Any idea why it does this disappearing act, is it trying to keep up on our toes!!!!!

I've typed it in and they've come up, just waiting for the terminal to finish thinking and it should be fine.

Thanks

Emma

---

### Post by p3_Arme on 2007-04-17
um nothing is happening I've typed it in and pressed return and waited, it brings the panels back, and its gone to the next line. But it hasn't brought up my <username>@laptop line back, and when I close it, the panels disappear. Is there anything else I should do.

Thanks for helping

---

### Post by LaRoza on 2007-04-17
I don't know exactly what is going on over there, but I don't have the internet at home either, I'm in school now, so I use the Ubuntu DVD. I just ordered the new Feisty DVD's so I can get things from the repos without an internet connection. It makes life easier. You can also get a DVD which has four Ubuntu flavours, live and install, on one disk. I know it doesn't help with the panels, but I'm sure it could be useful.

[http://www.thelinuxstore.ca/](http://www.thelinuxstore.ca/)

---

### Post by p3_Arme on 2007-04-17
duh!!!! Silly me, I restarted and now it's fine as is my stress levels, :) phew I do wonder why my friend gave me this 'cause it is not good for my stress levels or blood pressure!!!!!

But admittedly I am enjoying Linux as you can do so much with it, and rather than keep on re-installing things like in Windows, Linux is so much more flexable, okay harder but so much more fun :)

---

### Post by Brendantb on 2007-04-18
Hi, 

Sorry for not keeping up with the thread - different time zones I guess. 

The panel disappearance only occurred with me when I was configuring the panels at the start; it hasn't recurred, so don't worry, your installation should be stable. 

Learning Linux has a very steep learning curve, because it is so different to windows/macosx. But once you get the hang of it, the stress levels go down quickly... :)

---

### Post by p3_Arme on 2007-04-18
Solved that one :) Linux is fun and is admittedly a steep learning curve, but now I have another problem. 

As I don't have Internet on my Ancient old laptop, I have the use of another one :) with XP and Internet, So I can download the packages I need to get things I'd like (The Debian Edgy Packages) Most of them I've managed to install, how I have a problem with two of them. 

They want themselves installed as part of the depencies list. However it seems I can't install them, they keep crashing out.

I've tried installing from the Flash Drive, I've put the onto CD and tried that, and the HD. So now i'm at a loss. Just so you know, I'm the UK too, South London, near Croydon.

Emma

---

### Post by LaRoza on 2007-04-18
(It is seven in the morning here)
I'm back...

Why don't you put Ubuntu on the computer with XP?

---

### Post by p3_Arme on 2007-04-18
No chance, my boyfriend wont even think along those lines. Anyways I have my own PC with a Dual boot of XP and Linux with Ubuntu 6.10 on it :)

---

### Post by LaRoza on 2007-04-18
You don't need his permission...

The install disk will do everything for you...:)

---

### Post by p3_Arme on 2007-04-18
He does the admin jobs, so afraid not :( 

Never mind I have to figure out another problem ATM on Linux.

---

### Post by qriopal on 2007-05-01
Hi,

I have the same problem as described in the first post in this thread. Except that it happened after I plugged an ipod into my newly installed Xubuntu 7.04 through my usb port. My system hung up and I had to press the power button and restart. After I restarted, I couldn't find the top panel of my Xfce desktop. I was trying to follow the advice posted in this thread. 

First I tried to login to my xfce by "failsafe Terminal" at the session options. (This because I did not know how to get to the terminal window; my top panel disappeared including the applications menu on it through which I used to go to the terminal window earlier.)  I then tried "xfce4-panel " in the terminal window. This brought the top panel but without the "applications" menu. Also, it did not stay there when I rebooted. So I restarted the computer and tried in the failsafe terminal again the following command:
"sudo dpkg-reconfigure xfce4-panel". 

That too did not work. Next I tried the following:
"sudo aptitude purge xfce4-panel && sudo aptitude install xfce4-panel"

This ultimately brought back the top panel with the exception of the "Applications" menu. I now have the top panel but just have the firefox icon and the "Home" folder icon on the top left-hand side and the time and "quit" button on the top right-hand side in this panel. I also have a new icon at the extreme right, next to the quit button, which says "lock screen". Also the desktop background changed to complete black. 

Can anyone suggest what I should do to get back my "applications" menu. Also, at some point in time, I right-clicked on the desktop and in the configuration, I had done something to hide all the options it showed when I right click on the desktop. So now I do not get anything when I right click on the desktop. That means I cannot go to any of my applications except firefox which has an icon on the top panel. 

Hope someone can help me bring back the default top panel as it was before I plugged the ipod. Thanks.

Qriopal

---

### Post by Eddi3 on 2007-05-01
@qriopal

Just right click the panel, select "Add New Item," then scroll all the way down to where it says "Xfce Menu," and drag that wherever you want it.

After that, you can name it whatever you want by right clicking the menu, selecting "properties," and editing the Button Title.

 - Eddie

---

### Post by qriopal on 2007-05-02
Hi Eddi3, 

Thanks for your prompt reply but I remember I had tried it earlier. Anyway, that does not work because I do not see "xfce menu" in the "add item to the panel" list. Is there a way to add that to the list somehow? 

Thanks.

Qriopal

---

### Post by qriopal on 2007-05-02
Anyone else who can suggest me something to bring back my "applications" menu? I really would like to have to re-install Xubuntu all over again just to fix this thing. Thanks very much.

---

### Post by qriopal on 2007-05-02
Ok...new discovery. I found the following link:
[http://spuriousinterrupt.org/projects/xfce4/](http://spuriousinterrupt.org/projects/xfce4/)

Scrolling down on the above linked page on #12 in the FAQ list, it says:

"12 Help! My Xfce desktop disappeared! It looks like GNOME! And the
 desktop menu is gone too! What do I do?

    * You ran nautilus, didn't you? By default,
        Nautilus takes over the desktop when it runs. First you need to kill
        Nautilus, and then you should run xfdesktop to
        make sure Xfce's desktop manager is running. In the future, when you
        run Nautilus, pass it the --no-desktop option
        to instruct it to avoid drawing the desktop. A more permanent
        solution is to set the gconf key /apps/nautilus/preferences/show_desktop
        to "false" (the --no-desktop will no longer be
        required). This can be done using the graphical gconf-editor, or the
        command-line gconftool utility."

This seems similar to my problem. So I logged out and logged back to xfce in "failsafe terminal" session. I then typed "xfdesktop" but it said that its not installed on my system. So I did apt-get xfdesktop and installed. It did help bring back the original desktop background and the original desktop icons but still the applications menu on the top panel in the xfce desktop is missing. When I click on the Home icon next to the firefox icon on the top left-hand corner, it gives me an error message "Launch Error: Unable to launch "blacky": This feature requires a file manager service present (such as that supplied by Thunar)." So, it seems that Thunar has stopped working now.

Can anyone help bring back Thunar and the other applications on the top xfce panel?

---

### Post by LinGNUbie on 2008-06-26
Upon rebooting after an update/remove session my top and bottom panels had disappeared. After another reboot assuming that it did not load correctly, the desktop again had no panels but loaded my /home/[user] folder in nautilus in the middle of the screen. A simple navigation to **/usr/bin** and double-clicking **gnome-panel** restored the panels correctly, no downloads, connections, or terminal use required. Hope it helps someone else!

---

