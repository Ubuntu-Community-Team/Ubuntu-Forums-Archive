---
title: "change keyboard language"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by bird_gal on 2008-01-03
I am slightly challenged when it comes to computers and I can't figure this one out. It's a bit complicated so be patient ;) 
here goes....

I posted earlier because I had trouble with my panels disappearing ([http://ubuntuforums.org/showthread.php?p=4066662#post4066662](http://ubuntuforums.org/showthread.php?p=4066662#post4066662)). I followed somebody's advice which in the end left me with my keyboard language set to US english. This is rather inconvenient since I have a german laptop and typing is slightly nerve wrecking like this.
I tried to change the language following this advice:

> **flamelab said:**
> Simple !
I found that on wiki ( I did the same things )

```
How to Setup Keyboard (Language) Indicator & Install Foreign (Language) Fonts in Ubuntu:


1. On an Empty area of the Menu, right-click & select "Add to Panel...".

2. On the "Add to Panel" window that shows up, scroll down with the scroll bar on
the right & under the Utilities section, select "Keyboard Indicator".

3. Click on the button named "Add" & a Keyboard Indicator Icon should appear in
the middle of your Menu Toolbar (e.g. in My Computer, a "USA" keyboard
indicator showed up - in your PC, a diff Language could show, depending on
what Keyboard you selected when you installed Ubuntu)

4. Right-click on your "Keyboard Indicator" & select "Open Keyboard Preferences".

5. On the "Keyboard Preferences" window that shows up, select the Tab named
"Layouts".

6. Under the "Keyboard model", you should see the "Generic 104-key PC".

7. Under the "Selected layouts" section, YOUR installed Keyboard Layout should
show (e.g. as I said before in my case it is "U.S. English"). Click on the button
named "Add", to install a Second Keyboard Layout.

8. In my case, I selected "Greece".
Note:
If you select to install a Greek Keyboard Layout, do NOT expand the "Greece"
folder (you would get: Eliminate dead keys, Extended & Polytonic). Just select
"Greece" & click on the button named "OK". For other Keyboard Languages, you
are on your own to experiment & find out which selection works for you.

9. Now you should be able to see your installed "Selected layouts".
Note:
To install more Keyboard Layouts, follow steps 7-9.
To remove a Keyboard Layout, first select it & click on the button named
"Remove".

10. On the "Keyboard Preferences" window, select the Tab named: "Layout
Options"

11. Look for the option named: "Group Shift/Lock behavior" & expand it, to see its
options.

12. The following two options should be selected:

a. "Both Alt keys together change group." (this should already be
checked - leave it checked)
b. "Alt + Shift changes group." (check this too)
Note:
The combination "Alt+Shift", should change your Keyboard (Input)
Indicator, the same way it works in the Windows environment.

13. Click on the button named "Close" & test your "Alt+Shift" or "Alt+Alt"
combination to see whether the Keyboard (Input) Indicator changes on your
Menu Toolbar.

14. To Test whether your Ubuntu's Editor (mine is "gedit"), works with ALL your
installed Keyboard Layouts, select "Alt+F2". "Alt+F2" is the shortcut (way) to
launch the similar to Windows "Start\Run" window.

15. Inside the input box, type your favorite Editor's name (mine is "gedit").

16. Inside the Editor, try to type something in your English Keyboard & then try to
switch to your Greek Keyboard (or the one YOU installed), by pressing
"Alt+Shift". Again, try to type something in your (newly installed) Greek
Keyboard (or the one YOU installed) & voila!!! your Country's Keyboard is
setup & works Great!!!


Important Notes:

1. The (New) Keyboards you have ADDED, are installed ONLY for the User you are
currently Logged In as. If your Computer is used by MORE than one User, each
User MUST separately ADD / INSTALL their own preferred Keyboards. And that
includes the "root" user too!!!

2. The The (New) Keyboards you have ADDED, can ONLY be used to type Keyboard
(Language) Characters in applications / programs embedded to your Operating
System. The fact that you have installed them, does NOT mean that you can
USE them in separate applications / programs ALSO (such as the Open Office's
Writer - e.g. the equivalent to Microsoft Word).

3. In order to be able to type in your Open Office Writer with YOUR Language's
Fonts, you MUST install the appropriate Fonts for your Language.
For Example:
To be able to type in Open Office Writer (e.g. the equivalent to Microsoft Word) in
Greek you MUST go into a Windows PC and copy the ".ttf" (True Type Fonts) that
are used more often in typing Greek. In our case, copy: the "Times New
Roman.ttf", the "Arial.ttf" & the "Sans Seriff.ttf".
Alternatively, you could also search for these Fonts in the Internet.
Note:
You can NOT install ".fon" type Fonts in Ubuntu. ONLY ".ttf" (True Type Fonts).

For more information on installing Fonts, visit the following link:

http://linuxhelp.blogspot.com/2005/1...-in-linux.html <http://linuxhelp.blogspot.com/2005/12/adding-windows-fonts-in-linux.html>

Note:
Keep in mind that Open Office does NOT use the SAME Fonts installed / used by
the Operating System (e.g. Ubuntu). However, the Fonts installed are
independent from the User. Every User can access / use ANY installed Font.
And there is NO Greek Font available for the "root" User.
To make things more clear, just visit the link specified above.

Have Fun!!!
```

German is now the default language in the "layout" tab in keyboard preferences, but it didn't change my keyboard at all, still set to english. I do get an error message when I open Keyboard preferences, could this be part of the problem? :

"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

And then there's still the old problem with the panels....;)

HALP;)

cheers
Nora

---

### Post by Sef on 2008-01-03
> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

(Below assumes you are using Ubuntu)

Applications > Accessories > Terminal

then type

```
sudo apt-get update
```

then next

```
sudo apt-get install gnome-settings-daemon
```

That should install it and hopefully that problem will disappear.

.

---

### Post by bird_gal on 2008-01-03
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

this is what i get when i run that first command,.. should i just continue then...?

thanks!!

---

### Post by bird_gal on 2008-01-04
Hey,
I tried again what Sef suggested and got the following lines:

nora@linus:~$ sudo apt-get install gnome-settings-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-settings-daemon
nora@linus:~$ 

Does that mean it didn't work?
Any other suggestions?
Thanks

---

### Post by Sef on 2008-01-06
Didn't work.

> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Something is  not write.  

Open the terminal and type this code:

```
gksudo gedit /etc/apt/sources.list
```

That will be your sources list.  Paste that here.

---

### Post by bird_gal on 2008-01-08
thanks sef!
I'm at work, will try and get onto it tonight.
thanks!

---

### Post by bird_gal on 2008-01-12
I get the same thing again:

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-security multiverse


# wicd repository
deb [http://wicd.longren.org](http://wicd.longren.org) gutsy extras

Is there a serious problem? I might have to give my computer so somebody who know what they're doing (not that I really have the money but I'm definitely not getting anywhere by myself!)

N.

---

### Post by iris-n on 2008-01-12
Don't panic =)

Your sources appear to be fine. And through my pc i couldn't find that package either.
The thing is, the keyboard layout depends on the gnome-settings, and if you can't load that you can't turn your keyboard to german either.

But, if you said your computer started showing these weird problems after a forced shutdown, it may be that some files in your hard disk were corrupted, and in that case it would be better to reinstall the system.

Otherwise, you could try reinstalling gnome, but i'm not sure how to instruct you there.

---

