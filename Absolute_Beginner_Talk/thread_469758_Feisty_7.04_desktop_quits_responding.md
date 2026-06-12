---
title: "Feisty 7.04 desktop quits responding"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-10
Seems to happen when copying or downloading a file - all of a sudden, nothing on the Desktop will respond to a click.

The mouse still is moveable, and operations currently in progress seem to continue and complete normally, but nothing can be clicked on. The keyboard seems to go dead also.

I end up having to hit the power switch to do a rough-reboot :(

Wondering how to start debugging this..?

Is there a trick I can use, some kind of keyboard shortcut, to restart the Desktop without a forced complete power down?

---

### Post by KIAaze on 2007-06-10
> **ecs_pf5 said:**
> Seems to happen when copying or downloading a file - all of a sudden, nothing on the Desktop will respond to a click.

The mouse still is moveable, and operations currently in progress seem to continue and complete normally, but nothing can be clicked on. The keyboard seems to go dead also.

I end up having to hit the power switch to do a rough-reboot :(

Wondering how to start debugging this..?

Do you have a SCIM icon in your taskbar by any chance? (or SCIM running in the background)
Because I currently also have such a problem except that my mouse still works. It's only the keyboard that stops working.
What I do is that I simply quit SCIM after startup (I'll probably remove it from the startup apps too sometime).

> **ecs_pf5 said:**
> 
Is there a trick I can use, some kind of keyboard shortcut, to restart the Desktop without a forced complete power down?

Try ctrl+alt+backspace.
Another solution is switching to a virtual terminal by pressing "ctrl+alt+f1".
Then you can restart gdm (gnome display manager) by typing ```
sudo /etc/init.d/gdm restart
```.
(note that "sudo /etc/init.d/gdm stop" will simply stop gdm)

Of course, if your keyboard stops working, this is useless...

---

### Post by ecs_pf5 on 2007-06-10
> Do you have a SCIM icon in your taskbar by any chance?

I don't think so, no.. how would I tell if it's running in the background?

Cheers for the keystrokes I'll write them down for when it happens. Part of the problem is that because I'm fairly new to Ubuntu, the keyboard actually might be okay on those key combinations, I just haven't known what to press..

Of course coming from Windows I've been bashing ctrl-alt-delete for all I'm worth, to no avail :lol:

[edit]

it just did it. I opened an email in thunderbird, that's all - suddenly, no response from mouseclicks; couldn't click & drag any windows.. all froze up although mouse pointer still moveable. So I guess my theory that it had something to do with file copying is out the window :(

On the bright side ctrl-alt-backspace worked a dream to get me back into a working GUI without having to yank the power plug. Thanks :)

Still mystified as to why it's crashing out tho.

---

### Post by standards on 2007-07-11
This has happened to me like 5 times today already. I completely removed SCIM via synaptic and it's still freezing left and right. Frustrating.

---

### Post by regomodo on 2007-07-11
there is another, and safer, way of doing a reset. you hold down alt+SysRq and press the following buttons in sequence, giving 1sec between letter

r e i s u b

A way to remember is "Raising Elephants Is So Utterly Boring"

You can do this when your computer appears to be dead. Something to do with a high level irq or something like that

[edit] just found this link > [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by KIAaze on 2007-07-12
WOW, now that's a pretty complex trick! :O

> **ecs_pf5 said:**
> I don't think so, no.. how would I tell if it's running in the background?

To tell if it's running in the background, there are 3 ways I know of:
1)Gnome System monitor (look in the menus, it should be there somewhere)
2)ps (command-line)
3)top (command-line)

Read this article for more info on how to use them:
[http://www.informit.com/articles/article.asp?p=770644&rl=1]("http://www.informit.com/articles/article.asp?p=770644&rl=1")

P.S:
If you ever find some info telling you to edit xorg.conf (a config file controlling the hardware), you might want to try out [xorg-edit]("http://www.deesaster.org/progxorg.php").

---

