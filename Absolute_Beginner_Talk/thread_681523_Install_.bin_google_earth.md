---
title: "Install .bin google earth"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-29
Hello!
I downloaded google earth from google website. It's a .bin file, How can I install it?
Thank you.

---

### Post by erfahren on 2008-01-29
the site's instructions are as good as I could type out:
[http://earth.google.com/support/bin/answer.py?answer=44713&topic=1135](http://earth.google.com/support/bin/answer.py?answer=44713&topic=1135)

a good page on the basics of installing different file types: 
[How to install *ANYTHING* in Ubuntu!](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Hoom@n on 2008-01-29
Thank you. But please tell me how to navigate in Ubuntu terminal? I mean something like cd in windows(dos) I have a folder "Downloads" in my home folder. How can I navigate there?
Thank you.

---

### Post by RomeReactor on 2008-01-29
Hi. To navigate to the Downloads folder:
```
cd Downloads
```
Then make the file executable:
```
chmod +x GoogleEarthLinux.bin
```
Then to install:
```
sudo sh GoogleEarthLinux.bin
```
Or:
```
sudo ./GoogleEarthLinux.bin
```

After it's installed you can find it in 'Applications->Internet', or use the launcher on your desktop.

---

### Post by Kougaiji on 2008-01-29
nevermind, he beat me to it.

---

### Post by wesleybailey on 2008-01-29
In your terminal type:

$ cd ~/Downloads

The "~" in the above example is an alias for your home folder. Remember that all Linux commands are case sensitive.

---

### Post by Hoom@n on 2008-01-29
I navigated and I used just: sh googleearthlinux.bin and everything was good. now to open google earth i've to navigate to my home folder and type sh googleearth. I dont want this. How can I add google earth to Applications->Others? I mean the top left corner,
Thank you.

---

### Post by erfahren on 2008-01-29
oh, yeah - you probably would need to make the file executable (the "chmod +x" command that RomeReactor gave) - you can also do that through the GUI by right-clicking on the file > Properties > Permissions tab

anyway, for future reference, here's a link to a guide for using the terminal:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
- and just in case you want to see this (some good information here):
[https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html](https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html)

---

### Post by Hoom@n on 2008-01-29
What? I cant get what you said. I think it's not related on adding googleearth to Applications menu. Please explain how to add it.
(Now there is a googleearth in my home directory and too start google earth i've to type sh googleearth in terminal, but I wanna start it with mouse click from the Applications menu on top left side of ubuntu)
Thanks.

---

### Post by erfahren on 2008-01-29
> **Hoom@n said:**
> I navigated and I used just: sh googleearthlinux.bin and everything was good. now to open google earth i've to navigate to my home folder and type sh googleearth. I dont want this. How can I add google earth to Applications->Others? I mean the top left corner,
Thank you.
it *should* show up under "Internet" (or "Network" - I forgot what the Gnome menu says)

if it doesn't you can run this in the terminal or (press Alt+F2 to and run it there):
```

killall gnome-panel

```
(that will cause the panel to restart, refreshing the menu)

(my previous post was just some additional information to your other question - sorry. I'm moving a little slow.)

---

### Post by Hoom@n on 2008-01-29
Thank you.
I didn't use that. But after I restarted my computer I got it in my desktop and menu. Is it an ubuntu bug?

---

### Post by erfahren on 2008-01-29
> **Hoom@n said:**
> Thank you.
I didn't use that. But after I restarted my computer I got it in my desktop and menu. Is it an ubuntu bug?
not really a bug. Sometimes newly installed apps won't show up in the menu until it's refreshed. 

on rare occasions (especially with some of the older, smaller programs installed through Synaptic) there won't be a menu entry made at all. Some programs don't include the file needed for an entry to be created. In those cases you just need to create one.

---

### Post by Hoom@n on 2008-01-30
Thank you, so there is no need to report!

---

### Post by RomeReactor on 2008-01-30
[This bug report]("https://bugs.launchpad.net/gnome-panel/+bug/24669") is somewhat related, so the developers *are* aware of the issue. Just remember that after installing an application, if it doesn't immediately show up in the menus, you can go to 'System->Administration->System Monitor', find **gnome-panel**, right-click on it and select 'Kill process', which will restart the panels, and the icon should show up then. If it doesn't, it might be a rare instance of an application not making a menu entry, in which case you can make one yourself.

---

### Post by dcstar on 2008-01-30
> **Hoom@n said:**
> Hello!
I downloaded google earth from google website. It's a .bin file, How can I install it?
Thank you.

I find this a better way:

[http://ubuntuforums.org/showthread.php?t=601272](http://ubuntuforums.org/showthread.php?t=601272)

---

### Post by hyper_ch on 2008-01-30
Ahem, google earth is in the medibuntu repos. Just add them and install it through apt-get/aptitude/synaptic/adept...

---

### Post by paradoc on 2008-01-30
For sudophobes,  there's a simpler way to get the active icon on your desktop,(as in March PCWorld, p136):)

Go to [http://earth.google.com](http://earth.google.com) and download (upper left) the .bin file.

R.click on file>>permissions>>properties.
Tick the 'Allow executing file as program' option.
Double-click the .bin file, select 'Run in terminal' and follow the prompt.

Sit back and watch it all happen!

(Yes...I know that erfahren mentioned this in #8, this just elaborates it a little more for the AB newcomers)

I tried this on two 7.04 Ubuntu installations. It worked like clockwork on one, but stalled and wouldn't download the Google Earth prog. on the other....but then, on this particular PC the Windows version was very reluctant to appear too, and I don't know why, yet:confused:

---

### Post by dcstar on 2008-01-30
> **hyper_ch said:**
> Ahem, google earth is in the medibuntu repos. Just add them and install it through apt-get/aptitude/synaptic/adept...

And you are at the mercy of whatever version exists in that repository, whereas the "googleearth-package" program automatically downloads and makes a .deb out of the latest version available from the GoogleEarth site.

---

### Post by Hoom@n on 2008-01-30
I downloaded the file and then I went to terminal and typed sh googleearthlinux.bin and istalled it and it was working just there weren't icon and I had to use sh googleearth. I restarted my computer and after the restart there is an icon on desktop and in applications. So just I had to restart before!
But thanks for helps.

---

### Post by hyper_ch on 2008-01-30
> **dcstar said:**
> And you are at the mercy of whatever version exists in that repository
Same goes for all repos, right? :popcorn:

---

### Post by erfahren on 2008-01-30
I wanted to mention something I just thought of regarding the launchers not showing in the menu right away. It seems that I can remember a few times when that happened I would go to edit the menu to create my own but the launcher would then be there in "alacate" (the menu editor).  I'd close alacarte and the launcher would be in the list then.

Everytime that happened I just figured that I must've overlooked it the first time I looked in the menu, but thinking back, it seems that has happened quite a few times. 

So maybe it isn't necessary to kill the panel process to refresh the menu, but just open the menu editor and it will read the menu items that are supposed to be there (by their .desktop entry files) which would thereby also refresh it. 

Someone should try that sometime if a menu item isn't created right away. - Just right-click on the menu and "Edit" and then close the editor and see if the launcher is in there then.

---

### Post by Hoom@n on 2008-01-30
Thank you.

---

