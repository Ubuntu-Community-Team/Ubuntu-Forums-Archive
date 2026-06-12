---
title: "no menu when you use the logout button (possible bug)"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by uzi09 on 2006-05-26
sup all?

whenever i loaded up ubuntu (this has happend with breezy and dapper), for the first little while, when I hit the logout button (the applet on the panel, not the one under the System menu), i would get the great logout menu (with all the options -- to logout, lock screen, shutdown, hybernate, etc etc).

after a while, it doesn't show up any more. no warning or anything, it just logs right out. it's handy having it right there, but annoying that you don't even get a warning. it's happend a few times where my hand would just slip a bit and it'd log me out -- all my data: *gone*!

luckily, i was saved once by gmail's great autosaving system, but i wouldn't want this to happen again. if i setup a new account, the menu will return again, but i didn't bother using it enough to see if it'll go away after a while. i thought it'd be easy enough to just right click > properties and see what it executes, but i failed to find a properties menu for it :S.

can someone gimme a hand as to figuring out how to get it up and running again?

thanks,
uzi

ps: just thought of a possible cause, i also happend to change my theme. i don't know if this is theme related or not, and i don't recall whether it worked before the theme change or not.

---

### Post by dmizer on 2006-05-26
well, it's certainly easy enough to change the theme to try it.  if changing the them to ubuntu default human fixes your problem, you should think about saying something to the person who developed your alternative theme.

---

### Post by uzi09 on 2006-05-26
thanks for the reply -- i guess i might as well give that a try...

i'm surprised that it isn't that common. :S

EDIT: well, that didn't do anything :(

---

### Post by martinbriscoe on 2006-06-06
The solution for many is:

1. Go to the "System" menu - select "Administration" - select "Login Window"
2. Check the "Show Actions Menu" item under the menu bar section.

Martin

---

### Post by anders on 2006-08-23
I too am having this problem. I do not get a log out menu when I choose System -> Shutdown, I just get automatically logged out and returned to the GDM login screen. I didn't know the log out menu existed before I installed Dapper on another machine. The machine that it does not work on uses a Dapper installation that was installed when Dapper was in beta. None of the solutions suggested here yields anything and Google doesn't seem to help me either.

---

### Post by Jaime E. Villate on 2006-10-10
I have the same problem. I've used Ubuntu for over a year and I always had the logout menu with options lock, shutdown, etc. Yesterday I decided to install a theme different from the default one, and the logout menu dissapeared both from the panel button and from the System menu.
I have reverted to the default theme and I have made sure that the "show actions" setting is active, but the problem continues. Any hints will be appreciated.

---

### Post by Jaime E. Villate on 2006-10-10
I just found the cause/solution to my problem :lol: 
In my case it has nothing to do with having changed themes; I'm sorry I said that wrong.

I just entered the menu: System > Preferences > Session
and in the "Session Options" tab I checked the "Ask on logout" field which was unchecked. That solved the problem.

I had unchecked that field yesterday because I thought I had clicked on it accidentaly and I thought that field meant that I'd be asked whether to save the current desktop state.

---

### Post by anders on 2006-10-10
That did it for me too! Thanks for sharing Jamie! It's kind of silly I didn't figure that out myself, but having searched forums with people having similar problems and nowhere any solution I just thought this was some obscure bug that only a few were affected by and I gave it up.

The reason I didn't figure it out is that I think that that checkbox or one very much like it has always had the same meaning as you describe: to ask me each time I log out whether or not to save the session before logging out to the gdm login screen. It's very confusing when something changes meaning completely like that.

---

### Post by Jaime E. Villate on 2006-10-11
Yes, there was some change in the configuration menus that in this case create confussion. I also spend a lot of time searching around the Web, until I finally ran across the documentation for a very old version of Gnome (before the config menu changed) which made it clearer how to enable/disable the logout menu.

---

