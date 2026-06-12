---
title: "Shell Scripting?"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by twirp on 2006-04-14
I tried to make a shell script (I think that's what it's called)
and tried to make it start fbpanel, nautilus, and openbox

So I put:
```

exec fbpanel && exec nautilus && exec openbox

```

But it gave an error...
I made sure it was chmod +x, then I tried it at 0777

Thankyou for your time.

---

### Post by unbuntu on 2006-04-14
what was the error message?

---

### Post by twirp on 2006-04-14
[QUOTE=unbuntu]what was the error message?[/QUOTE]
All it said was Error starting up, starting 'Fail Safe Gnome' instead.

---

### Post by IYY on 2006-04-14
If you just want to run the 3 programs:

```
fbpanel &
nautilus &
exec openbox
```

> All it said was Error starting up, starting 'Fail Safe Gnome' instead.

What is this script for, exactly? When do you want it executed? Is it an Xsession script?

---

### Post by twirp on 2006-04-14
[QUOTE=IYY]If you just want to run the 3 programs:

```
fbpanel &
nautilus &
exec openbox
```



What is this script for, exactly? When do you want it executed? Is it an Xsession script?[/QUOTE]
I guess it would be for xsession.
I save it as /opt/startcustomx
and made it so the .desktop file runs it.
It now works, but it will only start whichever comes first. so it only started fbpanel, then I put openbox, and that only started.
But all 3 won't start...

How would I logout if the menu doesn't provide the option?
Is there a thing I can enter into the Terminal?

---

### Post by IYY on 2006-04-15
If the OpenBox menu is similar to the Fluxbox menu, you just add

```
[exit] (Exit) 
```

to it.

About all the programs not starting... Are you sure you included the &'s at the end of the first two lines?

Also, why did you choose OpenBox over Fluxbox? Flux is pretty much the same thing, and is easier to configure...

---

### Post by twirp on 2006-04-16
[QUOTE=IYY]If the OpenBox menu is similar to the Fluxbox menu, you just add

```
[exit] (Exit) 
```

to it.

About all the programs not starting... Are you sure you included the &'s at the end of the first two lines?

Also, why did you choose OpenBox over Fluxbox? Flux is pretty much the same thing, and is easier to configure...[/QUOTE]
I picked OpenBox because I don't like FluxBox's panel bar, and I like this lime green theme that I found for OpenBox.
It works now, I noticed that I had 2 &'s and that only had 1 (I should be more observant).

*More Questions...*
What parameters do I pass to make it load Nautilus as the background, and not open the file-manager?
And I found a post the other day about the different plug-n-play script things (where you put it in the USB and it shows on the desktop), what are the commands to start them because it doesn't do it unless I am using GNOME?

Thanks.

---

### Post by IYY on 2006-04-16
The command to launch Nautilus without a default window:

```
nautilus --no-default-window
```

To use Gnome themes and the automounter, the command is:

```
gnome-settings-daemon
```

---

