---
title: "3 Problems"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Stabilityonitsown on 2008-04-02
Hi guys, before we start I would just like to say im using Debian.

Anyways, the issues I am having is, everytime I convert RPM to DEB with alien I always get a folder instead of a deb file. I have tried, "alien -k blah.rpm""alien blah.rpm""alien -d blah.rpm", I am a complete noob so who knows... 

2nd everytime I install WINE it never shows up in the menu, but I can run .exe's that are on my desktop by using the command "wine /home/[username]/Desktop/blah.exe". I have also installed XWine and that didn't show in the menu too, I could open it with terminal using the command" xwine(I think it was that)". Also I have tried editing the menu with various programs. 

3rd I downloaded java and it came in a bin file and I opened it but it said "Gedit  has not been able to detect the character coding". So, could any of you guys help me out with this or am I doomed?

---

### Post by Xiong Chiamiov on 2008-04-02
Not sure if I can help, but I'll do what I can.

1. Not a clue.
2. You should be able to add an entry to your menu, yes?  If you tell me which things you want the in there (wine config, for example), I can give them to you.
3. You should be able to get java through your package manager, yes?

---

### Post by joshrobinson on 2008-04-02
> **Stabilityonitsown said:**
> Hi guys, before we start I would just like to say im using Debian.

Anyways, the issues I am having is, everytime I convert RPM to DEB with alien I always get a folder instead of a deb file. I have tried, "alien -k blah.rpm""alien blah.rpm""alien -d blah.rpm", I am a complete noob so who knows... 

2nd everytime I install WINE it never shows up in the menu, but I can run .exe's that are on my desktop by using the command "wine /home/[username]/Desktop/blah.exe". I have also installed XWine and that didn't show in the menu too, I could open it with terminal using the command" xwine(I think it was that)". Also I have tried editing the menu with various programs. 

3rd I downloaded java and it came in a bin file and I opened it but it said "Gedit  has not been able to detect the character coding". So, could any of you guys help me out with this or am I doomed?

1. ```
alien blah.rpm
``` is the right way to do it, -k preserves the version number. instead of increasing it by -1 (ex. original is 1.0-1 the alien one would normally do 1.0-2, but with -k option it would stay 1.0-1) what rpm are you trying to convert? if you have a link ill look at it

2. have you tried right clicking appications and go to edit menu's? for me wine shows up under system tools in its own menu

3. bin files are executables, have you tried installing the java in the repo's instead? but to run the bin file you need to do this

```
sudo chmod +x java.bin
```
```
sudo ./java.bin
```
replace java.bin with the bin's real filename

---

### Post by Stabilityonitsown on 2008-04-02
Ok so I am going to try to do what you guys said(use repo's) but now I am confused as to which one I get, here is what I am seeing so you guys arent guessing out of the blue.
[http://img399.imageshack.us/img399/1187/screenshotob7.png](http://img399.imageshack.us/img399/1187/screenshotob7.png)
and also heres the error I get when trying to open java with that command you gave me.
[http://img363.imageshack.us/img363/9572/screenshot1wm5.png](http://img363.imageshack.us/img363/9572/screenshot1wm5.png)

---

### Post by joshrobinson on 2008-04-03
just hit java common for now
are you trying to use java in firefox? or to run a java application?

also, when you are on your desktop in a terminal you dont need to enter the file's location
ex
username@ubuntu:/home/username/Desktop # sudo chmod +x java.bin
you dont need to add the /home/username/Desktop/java.bin

---

### Post by Xiong Chiamiov on 2008-04-03
Ah yes, the abundance of Java packages ;).  You'll probably want the one called sun-java-1.6 I think?
EDIT: nvm, josh is right.  If you're doing java programming you'll prolly want something more.

2nd, I see that you're opening the .bin with gedit.  Did you do both commands he gave you, in that order?

---

### Post by Stabilityonitsown on 2008-04-03
Okay, so I installed java through package manager(i installed the common one), and I did the test on both browsers (epiphany and iceweasle) and both browsers failed the test. 
And I also ran the command "alien blah.rpm" still didn't work. Just created a folder that I couldn't delete and had to use the terminal delete thingy(cant post the command because rules don't let me).

Edit: Ok so I forgot to install the plugin for browser in package manager,so now java is working.

Editedit:Only problems left are RPM to DEB and WINE showing up in menu.

---

### Post by Xiong Chiamiov on 2008-04-03
> **Xiong Chiamiov said:**
>  I see that you're opening the .bin with gedit.  Did you do both commands he gave you, in that order?

If you're requiring Java for web use, you'll need to install one of the packages that has "plugin" in the name, eg j2re1.4-mozilla-plugin.

---

### Post by joshrobinson on 2008-04-03
> **Stabilityonitsown said:**
> Okay, so I installed java through package manager(i installed the common one), and I did the test on both browsers (epiphany and iceweasle) and both browsers failed the test. 
And I also ran the command "alien blah.rpm" still didn't work. Just created a folder that I couldn't delete and had to use the terminal delete thingy(cant post the command because rules don't let me).

search in your package manager for java, and then scroll down and see if you can find one along the lines of java-plugin

could you link me to the rpm you are trying to convert?

---

### Post by Stabilityonitsown on 2008-04-03
Ah yes here is the link
[Click on me]("http://downloads.sourceforge.net/wine/wine-0.9.58-mdv2008.0.i586.rpm?modtime=1206193584&big_mirror=1")

---

### Post by Xiong Chiamiov on 2008-04-03
Not that this will help your problem, but you really should install wine using [the repositories]("http://winehq.org/site/download-deb"), like they tell you to.  It'll make your life much easier.

---

### Post by Stabilityonitsown on 2008-04-03
I did but it never ever shows up in the menu :(.....

---

### Post by Xiong Chiamiov on 2008-04-03
> **Stabilityonitsown said:**
> I did but it never ever shows up in the menu :(.....

Well, the rpm will just extract it somewhere, if I'm not mistaken.  In any case, it won't automatically add it to your menu.

> **Xiong Chiamiov said:**
> 
 If you tell me which things you want the in there (wine config, for example), I can give them to you.


---

### Post by joshrobinson on 2008-04-03
> **Xiong Chiamiov said:**
> Well, the rpm will just extract it somewhere, if I'm not mistaken.  In any case, it won't automatically add it to your menu.

it will make a .deb file for you with alien, well its supposed to, i got ALOT of errors trying to convert it to a .deb

your better to just try to get his menu's working

---

### Post by Stabilityonitsown on 2008-04-03
> **Xiong Chiamiov said:**
> Well, the rpm will just extract it somewhere, if I'm not mistaken.  In any case, it won't automatically add it to your menu.Well I will reinstall it using the repo''s and can you tell me how to get it onto the menu plzzz.

Edit: Installed it through repo and now I need help adding it to main menu.

---

### Post by Xiong Chiamiov on 2008-04-03
Do you know how to edit your menu and add new items?

If you do, then:

Browse C:\ Drive
```

xdg-open ~/.wine/drive_c

```

Configure Wine
```
winecfg
```

Uninstall Wine Software
```
uninstaller
```

---

### Post by Stabilityonitsown on 2008-04-03
Edit: Sorry I miss read your post, ok I am confused as to what I am supposed to do with those commands that will help me add WINE to my menu...?

---

### Post by Xiong Chiamiov on 2008-04-03
Sorry, I perhaps should have been more clear.

I'm not sure of the exact procedure in Debian, but in Kubuntu... darn KDE.  Uhm, let me look.
Ok, well, I came up with [this]("http://wiki.debian.org/EditGnomeMenus?highlight=%28menu%29").  I can't really help you with the specific app, since I'm not using Debian *or* gnome, but if you can somehow figure out how to add a new option to your menu, then those things I posted above are the commands to add to your menu.  I hope that makes sense, but please don't hesitate to ask me to clarify.

---

### Post by joshrobinson on 2008-04-03
right click applications, click edit menu's
click new menu, call it wine, and select an icon
then select new item, add the names and commands Xiong Chiamiov gave you

---

### Post by Stabilityonitsown on 2008-04-03
Okay, I don't know if you get what I am saying, I am a linux noobie, and I have no clue as to how I add wine to my Menu, I got gnome-menu already.

---

### Post by Xiong Chiamiov on 2008-04-03
Well, the problem is a combination of your lack of experience, and the fact that you're using a different distro than us.  We can try to help you along the best we can, but you'd probably do better at the Debian forums.

---

### Post by Stabilityonitsown on 2008-04-03
Well Debian is Ubuntu's father so I don't get what you mean, they are the same, Ubuntu is based off Debian. So I don't get why thats a problem.

---

### Post by Xiong Chiamiov on 2008-04-03
Just because Ubuntu is based off of Debian does *not* mean that they are exactly alike.  They are much more similar than say, Fedora and Ubuntu, but they are *not* the same.  In addition, I'm using Kubuntu, which uses KDE instead of GNOME, so that also limits how I can help you.

---

### Post by Stabilityonitsown on 2008-04-03
Ok then I see where you are coming from, in that case can I ask what command do I use to put in WINE entry in the menu.

---

### Post by Xiong Chiamiov on 2008-04-03
There isn't really any command to add things to the menu (that I know of), but you should be able to do it with the GUI somehow.  Try what Josh said
> **joshrobinson said:**
> right click applications, click edit menu's
click new menu, call it wine, and select an icon
then select new item, add the names and commands Xiong Chiamiov gave you
and also see what you can do with gnome-menu.

EDIT: t[his]("http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html") might be helpful

---

### Post by joshrobinson on 2008-04-03
ok this might not work, but we are going to try it anyway

```
cd /etc/xdg/menus/applications-merged
```
```
sudo wget http://www.ruins-edge.com/wine.menu
```
```
sudo killall gnome-panel
```

---

### Post by Stabilityonitsown on 2008-04-03
> **joshrobinson said:**
> ok this might not work, but we are going to try it anyway

```
cd /etc/xdg/menus/applications-merged
```
```
sudo wget http://www.ruins-edge.com/wine.menu
```
```
sudo killall gnome-panel
```
lol you thing didn't work out correctly...
```
bash: Cd: /etc/xdg/menus/applications-merged: No such file or Directory
```

---

### Post by joshrobinson on 2008-04-03
> **Stabilityonitsown said:**
> lol you thing didn't work out correctly...
```
bash: Cd: /etc/xdg/menus/applications-merged: No such file or Directory
```

well it was worth a shot, thats where the wine-menu config file is located at on my install
im out of idea's

---

### Post by Stabilityonitsown on 2008-04-03
Ok, I just added wine to the menu using winefile command, now theres a new problem, everytime I try to open a program I installed in wine it just refreshs and doesn't do anything.

---

