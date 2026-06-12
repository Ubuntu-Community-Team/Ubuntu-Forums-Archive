---
title: "mac menu"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by chips24 on 2008-03-13
im looking for mac menu and mac icons, con you help me find those?

---

### Post by divague on 2008-03-13
mac icons i suggest you to download the ver 0.3 icons
[http://sourceforge.net/project/showfiles.php?group_id=204373](http://sourceforge.net/project/showfiles.php?group_id=204373)

mac menu
[https://wiki.ubuntu.com/global_menu](https://wiki.ubuntu.com/global_menu)

---

### Post by chips24 on 2008-03-13
well, its useless.

---

### Post by chips24 on 2008-03-14
what about a mac login screen?

---

### Post by Fred_E _krugar on 2008-03-14
How about just going here :
[http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/](http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/)

---

### Post by chips24 on 2008-03-14
im stumped, how do you use the global menu bar?

---

### Post by Duck2006 on 2008-03-14
These may help in getting icons and stuff to make your system look like a mac

[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)

[http://www.linuxquestions.org/questions/ubuntu-63/make-ubuntu-look-like-osxmac-608307/](http://www.linuxquestions.org/questions/ubuntu-63/make-ubuntu-look-like-osxmac-608307/)

---

### Post by ramjet_1953 on 2008-03-15
For a Mac-like launch bar try Avant Window Navigator

[COLOR="Red"]sudo apt-get install avant-window-navigator[/COLOR]

[COLOR="Red"]sudo apt-get install awn-manager
[/COLOR]
Note that Avant only works when you have visual effects enabled.

Check out my desktop, to see if this is what you want.

Regards,
Roger :cool:

---

### Post by chips24 on 2008-03-15
the awn manager does not work, I have been searching for 6 hours to install my mac menu and desklet  thing. can you help me find a DEB download?

---

### Post by chips24 on 2008-03-15
well ive decided that im going to create the menus manually , one question, how do you make a link to a folder on  the "edit menus" option?

---

### Post by chips24 on 2008-03-16
i didnt know how to do this manual thing, the mac menu bar is more complex than it looks, i tried for a couple more hours and i couldn't find the mac menu bar. can you help me?

however this is my progress. i already have a mac usplash  and login!

---

### Post by ramjet_1953 on 2008-03-16
When you said that AWN Manager doesn't work, exactly what is happening when you try to run  it?

The manager appears as an item in [COLOR="Blue"]System>Preferences>AWN Manager[/COLOR]

Did you install Avant Window Manager and AWN Manager using Synaptic, from the repositories?

Don't forget, Avant Window Manager only works with Desktop Effects enabled.

Regards,
Roger :cool:

---

### Post by chips24 on 2008-03-16
im not talking about the awn manager, im talking about the menu bar, the the ubuntu menu bar, except a mac theme. i already have AWN, i dont like it.

---

### Post by chips24 on 2008-03-16
heres a real mac screen shot, the menu at the top of the screen- thats what i want.

---

### Post by chips24 on 2008-03-16
sorry, heres the screen shot...:oops:

well, looks like the file format is invalid, you get what i mean though?

---

### Post by joshrobinson on 2008-03-16
> **chips24 said:**
> sorry, heres the screen shot...:oops:

well, looks like the file format is invalid, you get what i mean though?

yeah, i never got the whole, i want my linux install to look like a mac or look like vista, linux has its own unique look that i think is better then both of them

the only thing i can think of is the mac global menu, which is pretty neat looking, but looks like it requires more work then its worth to actually have it

---

### Post by chips24 on 2008-03-16
i personally don't know how to use th global menu bar, can you tell me how? im willing to do anything to get the theme i want.

---

### Post by joshrobinson on 2008-03-16
let me look into it, i will let you know how it goes

---

### Post by joshrobinson on 2008-03-16
ok, well i installed it and got it working, but its got alot of downfalls, for one, it doesnt work with firefox, and a good deal of other applications, if you open those applications, the mac menu just goes blank and you have to resort to your normal file edit view menu's on the application itself

this will force you to use applications that work with the mac menu, just to get the desired look, not cool.. heres a screenshot of how it turned out on my computer, note i didnt theme it to look like a mac, but thats the mac menu

if you are still interested i can post how to do it, but i wouldnt recommend it

---

### Post by chips24 on 2008-03-16
ok! show me! im ready! i already have my most used programs on the bottom menus anyway.

---

### Post by joshrobinson on 2008-03-16
run these commands one at a time

```

mkdir temp
cd temp
 wget http://gnome2-globalmenu.googlecode.com/files/gnome-globalmenu-0.4.2_ubuntu-gusty-svn679.tar.gz
tar zxvf gnome-globalmenu-0.4.2_ubuntu-gusty-svn679.tar.gz
sudo dpkg -i *.deb

```

now do this
```
gedit ~/.gnomerc
```
and paste the following
```
export GTK_MODULES=libgnomenu
```
save and close it

on your top panel, right click it and add the global menubar
logout and log back in, you should see the file edit menu at the top panel now

---

### Post by chips24 on 2008-03-16
Ubuntu wouldn't start! i tried for an hour to get in to the login screen. i had to say bye bye to Ubuntu. all my work and information are gone!!!! grrrrr!:x:x:x:x:x

the usplash would appear than a black screen with a useless curser would appear blinking. i waited and waited and nothing happened.

---

### Post by Ptero-4 on 2008-04-10
For those who wish to test the mac menubar. The apps that work are the ones made in gtk2 and wxgtk2, everything else won't work (kde apps are qt, limewire/frostwire are java, oo.org is a custom toolkit, firefox is xul based, aMSN is tcl/tk and gnome 1 apps run gtk1).

---

