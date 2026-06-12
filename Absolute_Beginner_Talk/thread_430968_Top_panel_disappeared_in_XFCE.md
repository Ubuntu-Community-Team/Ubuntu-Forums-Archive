---
title: "Top panel disappeared in XFCE"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by qriopal on 2007-05-02
Hi,

I have the same problem as described in the first post in [this ]("http://ubuntuforums.org/showthread.php?t=412016&highlight=xubuntu+panels+disappeared")thread. Except that it happened after I plugged an ipod into my newly installed Xubuntu 7.04 through my usb port. My system hung up and I had to press the power button and restart. After I restarted, I couldn't find the top panel of my Xfce desktop. I was trying to follow the advice posted in the above mentioned thread.

First I tried to login to my xfce by "failsafe Terminal" at the session options. (This because I did not know how to get to the terminal window; my top panel disappeared including the applications menu on it through which I used to go to the terminal window earlier.) I then tried "xfce4-panel " in the terminal window. This brought the top panel but without the "applications" menu. Also, it did not stay there when I rebooted. So I restarted the computer and tried in the failsafe terminal again the following command:
"sudo dpkg-reconfigure xfce4-panel".

That too did not work. Next I tried the following:
"sudo aptitude purge xfce4-panel && sudo aptitude install xfce4-panel"

This ultimately brought back the top panel with the exception of the "Applications" menu. I now have the top panel but just have the firefox icon and the "Home" folder icon on the top left-hand side and the time and "quit" button on the top right-hand side in this panel. I also have a new icon at the extreme right, next to the quit button, which says "lock screen". Also the desktop background changed to complete black. I have tried to put the XFCE menu on this new panel by right clicking on the panel, and selecting "Add New Item," and adding "Xfce Menu" from the list. But that does not work in my case because I do not see "xfce menu" in the "add item to the panel" list.

Can anyone suggest what I should do to get back my "applications" menu. Also, at some point in time, I right-clicked on the desktop and in the configuration, I had done something to hide all the options it showed when I right click on the desktop. So now I do not get anything when I right click on the desktop. That means I cannot go to any of my applications except firefox which has an icon on the top panel.

Hope someone can help me bring back the default top panel as it was before I plugged the ipod. I really would like to avoid having to re-install Xubuntu all over again just to fix this thing. Thanks very much.

Qriopal

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

This seems similar to my problem. So I logged out and logged back to xfce in "failsafe terminal" session. I then typed "xfdesktop" but it said that its not installed on my system. So I did apt-get xfdesktop and installed. It did help bring back the original desktop background and the original desktop icons but still the applications menu on the top panel in the xfce desktop is missing. When I click on the Home icon next to the firefox icon on the top left-hand corner, it gives me an error message "Launch Error: Unable to launch "blacky": This feature requires a file manager service present (such as that supplied by Thunar)." Also, when I reboot my computer now I get the following message when I log in:

"Unable to contact the Xfce Trash service.
Make sure you have a file manager installed that supports the Xfce Trash service, such as Thunar." 

So, it seems that Thunar has stopped working now.

Can anyone help bring back Thunar and the other applications on the top xfce panel?

---

