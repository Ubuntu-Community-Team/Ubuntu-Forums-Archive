---
title: "Starting A Program before log-in"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Mr T 87 on 2008-03-04
I have downloaded a game, frets on fire (fretsonfire.sourceforge.net). I want it to load before anything else. Such as the log-in screen and the desktop. Of course it'll have to load after all the drivers. I read somewhere that I have to edit the rc.local file but i'm not sure what to put in there. The same thing i'd type in the terminal to run the game?

Is it actually possible to run a game at this stage anyway? Or is their a better way to do all this?

---

### Post by hyper_ch on 2008-03-04
it is by starting it in the according run levels...

but why on earth would you want to do that?

---

### Post by igknighted on 2008-03-04
Ubuntu doesn't use several of the init runlevels by default, so I would pick one (4 or 5) and stop the things you don't need (like gdm) and set a lightweight WM like fluxbox to run, and then the game on top of that.  From there I would copy/paste the top grub entry in /boot/grub/menu.lst right below itself and add the number 4 or 5 (whichever you used above) to the end of the kernel line.  This will tell Ubuntu what runlevel to use as default.  Now change the title to "frets on fire" or anything that will distinguish it for you, and when you want to boot to the game first simply choose that option.  Also, the command 'sudo init 4' (assuming you configured init level 4) would take you to the game and drop you out of gdm/gnome.  You could leave the game and start gdm again by using the command 'sudo /etc/init.d/gdm start', or (in theory) 'sudo init 2'

EDIT: I agree with hyper_ch though, I cannot imagine why you would want to do this.

---

### Post by marufaberlin on 2008-03-04
Well... Why don't you use an automatic login for an account and have FoF run when that user logs in? You can always log out and log in to a different account.

But why the hell would you want to run a game every time a computer starts?

---

### Post by Mr T 87 on 2008-03-04
> **igknighted said:**
> Ubuntu doesn't use several of the init runlevels by default, so I would pick one (4 or 5) and stop the things you don't need (like gdm) and set a lightweight WM like fluxbox to run, and then the game on top of that.  From there I would copy/paste the top grub entry in /boot/grub/menu.lst right below itself and add the number 4 or 5 (whichever you used above) to the end of the kernel line.  This will tell Ubuntu what runlevel to use as default.  Now change the title to "frets on fire" or anything that will distinguish it for you, and when you want to boot to the game first simply choose that option.  Also, the command 'sudo init 4' (assuming you configured init level 4) would take you to the game and drop you out of gdm/gnome.  You could leave the game and start gdm again by using the command 'sudo /etc/init.d/gdm start', or (in theory) 'sudo init 2'


Sorry, I am quite new to ubuntu and linux. If that would work could someone translate it and maybe make it bold and about size 20? lol. I need idiot proof information, ill try my best with what I get though.

The reason i am wanting to do this is because i want to set the game up in my house as an arcade machine, so people can just switch it on and play. I'm editing the game to make it more arcade-like. I was hoping that Linux would give me more flexability with this sort of thing then windows since I can remove all unneccisary packages.

Thanks you for the replies =)

---

### Post by igknighted on 2008-03-04
> **Mr T 87 said:**
> Sorry, I am quite new to ubuntu and linux. If that would work could someone translate it and maybe make it bold and about size 20? lol. I need idiot proof information, ill try my best with what I get though.

The reason i am wanting to do this is because i want to set the game up in my house as an arcade machine, so people can just switch it on and play. I'm editing the game to make it more arcade-like. I was hoping that Linux would give me more flexability with this sort of thing then windows since I can remove all unneccisary packages.

Thanks you for the replies =)

Ok, that actually makes a lot of sense.  I apologize for judging right away like that.

To answer your question:  there are a few way you could go with this.  The method I outlined above is feasible, but (as you can see) complicated.  If you are not super concerned about the loss of a small bit of performance, then I would recommend doing a standard gnome install from the live CD.  Then install frets on fire.  Then go to system->preferences->sessions and click the add button.  Now you need to enter a name of your choosing (frets on fire works fine, it doesn't actually matter) as well as the command to run the program (this you need to find somewhere... the easiest way would be to the launcher in the menu, right click and add to desktop.  Then right click the icon on the desktop and click properties, the last tab (launcher) should show the command.  Click ok, then go to system->administration->login window.  Here go to the security tab and select your user for automatic login.  Now reboot, and it should log in automatically and start the game.  You can even autohide the panels (or delete one) if you want.

---

### Post by hyper_ch on 2008-03-05
just do auto-login with a user and then load it in the current session... no need to load the game before the user login...

---

