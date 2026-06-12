---
title: "nautilus missing?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by aCanadian on 2007-06-19
hello everyone, this is my first post, and the third day of me trying out linux.
To give you a bit of background:
- 2 days ago I started on feather linux, I was having trouble and ubuntu seemed to have a lot of support (from all of you ;) ) so i switched to ubuntu today.
- I've recently created a my music, and my pictures folder on my desktop as well as installed pidgin and limewire (and system updates of course). The problem is, is that after I did all that, I restarted and POOF my desktop background is changed (to a blank ubuntu colour (no graphic)) and those folders have gone missing to, I also cant access my desktop when i go to "places" and I got a warning about Nautilus(?) not being started. Im sorry if this is a total noob question guys, but I am a total noob. PLEASE HELP ME :( 
-thanking you all in advance
     aCanadian

*edit* It would be great to get an email to regarding a fix for my problem [email]a__canadian__@hotmail.com[/email]

---

### Post by st0nes on 2007-06-20
One thing it could possibly be: did you log back in as the same user?  If you log in as a different user you will not have the same settings, so your desktop modifications will not be visible.

---

### Post by aCanadian on 2007-06-20
yes i did log in as the same user, I only have one account on here ;) and another thing thats a problem is i cant right-click to create a new folder or anything like  i could before :(

---

### Post by Rui Pais on 2007-06-20
and whats the output of 
```
ls ~/Desktop/
```

can you run gconf-editor, navigate to:
app->nautilus->preferences and ensure that the option 'show_desktop' is enabled?

---

### Post by aCanadian on 2007-06-20
the output of ls ~/desktop/ is:

LimeWireLinux.deb  mypics                   purple-plugin-pack_1.0-1_i386.deb
mymusic            pidgin_2.0.0-1_i386.deb

when i run gconf-editor, "show desktop" is enabled. 
Also when i try to go to a folder on my desktop "mypics" through "places" it says:
could not open location 'file:///home/gorak/Desktop/mypics' 'There is no default action associated with this location.

---

### Post by Rui Pais on 2007-06-20
ok, try this:
logout (and close any gnome session).
Go to a console (by pressing Ctrl+Alt+F1)
Login there and then type:
```
mkdir gnome_BAK
mv .gnome* gnome_BAK/
mv .gconf* gnome_BAK/
```
attention with typos, must be that precisely.

Type:
exit
and press Ctrl+Alt+F7
Login again at graphical manager. 
Check if it's ok.

good luck.

---

### Post by aCanadian on 2007-06-20
lol...well...nothing is changed? :S i think i did everything right. (except maybe "closing gnome session" not sure what you mean by that.

---

### Post by Rui Pais on 2007-06-20
> **aCanadian said:**
> lol...well...nothing is changed? :S i think i did everything right. (except maybe "closing gnome session" not sure what you mean by that.

Close sessions, just logout, if you are the single user of your machine. logout all users if anyone else use it (i assume not, but i don't know :))

If i didn't change nothing... then is not a broken gnome configuration...
What the output of:
```
ls -l .ICEauthority
```
?

---

### Post by aCanadian on 2007-06-20
well the output is...

gorak@gorak-desktop:~$ ls -l .ICEauthority

```

-rw------- 1 gorak gorak 519 2007-06-20 13:57 .ICEauthority

```

---

### Post by swoll1980 on 2007-06-20
Same thing happend to me last night I just restarted my cpu and it worked fine

---

### Post by Rui Pais on 2007-06-20
uhmm.. looks ok.

Did this happen with other users? If you are the only user do you mind to make another account just to check it, please (you can delete it after).

---

### Post by aCanadian on 2007-06-20
lol okay i made another user and I called it "test" and its set as an admin... now what? (ps I've restarted a few times since all this began, so i don't think thats gonna help lol.

---

### Post by Rui Pais on 2007-06-20
> **aCanadian said:**
> lol okay i made another user and I called it "test" and its set as an admin... now what? (ps I've restarted a few times since all this began, so i don't think thats gonna help lol.

:lol: login as test. :lol:

Does you *alter ego* test has issue with nautilus too?
If so something is wrong in your system. If not, maybe more cleanness of your /home/gorak/ is needed... (like the above with .gnome* and .gconf*)

---

### Post by aCanadian on 2007-06-20
I'm logged in as test, and same problem here :( am I going to have to reformat AGAIN? lol :P

---

### Post by swoll1980 on 2007-06-20
I ran dpkg-reconfigure -a    first restarted xserver by hitting cntrl alt backspace it didn't work so I restarted my cpu so maybe it was dpkg-reconfigure -a and restarting the cpu that worked

---

### Post by Rui Pais on 2007-06-20
yes, dpkg-reconfigure -a can't hurt...

you can too do:
```
sudo aptitude reinstall nautilus
```
or even:
```
sudo aptitude reinstall ubuntu-desktop
```

another nice thing to do would uninstall 1st. those debs that you install it. maybe they are conflicting with something, (since your problem is at system not at user conf level).

Good luck.
Keep post.

---

### Post by aCanadian on 2007-06-20
when I try to run  dpkg-reconfigure -a this is what i get:

```
gorak@gorak-desktop:~$ dpkg-reconfigure -a
/usr/sbin/dpkg-reconfigure must be run as root
```

---

### Post by Rui Pais on 2007-06-20
administrative tasks always require sudo:
```
sudo dpkg-reconfigure -a
```

---

### Post by aCanadian on 2007-06-20
okay so I just did that, and, now it says this:

```
gorak@gorak-desktop:~$ sudo dpkg -reconfigure -a
Password:
dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

---

### Post by forestpixie on 2007-06-20
no gap between dpkg-reconfigure I believe

---

### Post by aCanadian on 2007-06-20
ok I've tried everything. I give up. I'm starting my reformat now. This time im not going to install the new pidgin quite yet (i think i deleted something i shouldnt have when i uninstalled gaim). But once I'm done I'll give ya'll an update :) thanks for all the help everyone.

---

### Post by Rui Pais on 2007-06-20
sorry to know that :(

good luck with your next install then.


Where do you get those debs? maybe they have been the all cause. Take care installing deb files get it from the net. If they are not specific for Ubuntu they can broke something vital. 
Check here first for extra deb packages:
[http://www.getdeb.net](http://www.getdeb.net)
At least they ar compiled for Ubuntu.

Best of luck to your next Ubuntu :)

---

### Post by aCanadian on 2007-06-20
I reinstalled and am on a fresh slate :) I'll check out that getdeb site, but I think I'm gonna go for a swim with the girlfriend now and take a break from this ubunting lol

---

