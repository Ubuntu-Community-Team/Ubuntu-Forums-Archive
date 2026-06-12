---
title: "Frustrated beyond belief: Ubuntu Rescue"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by mybootorg on 2006-04-22
I am new to Ubuntu and Linux in general and have had a pretty easy time installing Ubuntu 5.10 and other applications.  (With the possible exception of upgrading the default 5.08 Firefox install to the latest version --which I still havent figured out, even using Automatix) everything has gone very smoothly.

One of my first goals after installing my necessary software was to completely rid Ubuntu of the "poop brown" color that plagues it.  This proved to be a difficult task as it's strewn from the boot loader, to the login, to the splash, to the desktop etc. And has to be changed every place.

I found an article on how to alter GRUB's menu.lst to point to a different boot image.  This would have been fine and dandy except I mistyped the path to the image.

Now does Grub revert to a default image when it cant find its SPLASHIMAGE?  No.  Does Grub just skip the SPASHIMAGE and continue to boot?  No.  It refuses to boot Ubuntu and runs in a loop, trying to reboot to fix the problem. How wonderful...

I found references to Ubuntu's install rescue mode.  Just what I needed...  Loaded it up, entered rescue mode, navigated to /boot/grub.  Set myself up with root access and proceeded to try to edit my menu.lst

Here's the source of my anger: I can mv menu.list.  I can copy it. I can view it.  I can do just about anything to it except....  um... edit it.

If I type:

gedit menu.lst

I get a bunch of errors about not being able to display to device or application 1/* nonsense.

If I type:

edit menu.lst

I get a weird editor that seems to default to view-only mode and puts my keyboard into what I can only call "press a key for a random result" mode.  There doesn't appear to be a way to exit edit much less navigate the file or edit anything.

gedit ane edit --help are amazingly unhelpful.  For instance, the help for edit shows that you can apparently run it in different modes, and that "view" is the default mode.  But then forgets to suggest the other possible modes.

Sorry for the rant.  I'm really frustrated right now -- mostly because what should be VERY simple, is VERY unachievable for me.

Any suggestions beyond driving to the liquor store or reinstalling? :)

Best regards,

Craig Mitchell, St. Louis, MO

---

### Post by mostwanted on 2006-04-22
[QUOTE=mybootorg]I am new to Ubuntu and Linux in general and have had a pretty easy time installing Ubuntu 5.10 and other applications.  (With the possible exception of upgrading the default 5.08 Firefox install to the latest version --which I still havent figured out, even using Automatix) everything has gone very smoothly.

One of my first goals after installing my necessary software was to completely rid Ubuntu of the "poop brown" color that plagues it.  This proved to be a difficult task as it's strewn from the boot loader, to the login, to the splash, to the desktop etc. And has to be changed every place.

I found an article on how to alter GRUB's menu.lst to point to a different boot image.  This would have been fine and dandy except I mistyped the path to the image.

Now does Grub revert to a default image when it cant find its SPLASHIMAGE?  No.  Does Grub just skip the SPASHIMAGE and continue to boot?  No.  It refuses to boot Ubuntu and runs in a loop, trying to reboot to fix the problem. How wonderful...

I found references to Ubuntu's install rescue mode.  Just what I needed...  Loaded it up, entered rescue mode, navigated to /boot/grub.  Set myself up with root access and proceeded to try to edit my menu.lst

Here's the source of my anger: I can mv menu.list.  I can copy it. I can view it.  I can do just about anything to it except....  um... edit it.

If I type:

gedit menu.lst

I get a bunch of errors about not being able to display to device or application 1/* nonsense.

If I type:

edit menu.lst

I get a weird editor that seems to default to view-only mode and puts my keyboard into what I can only call "press a key for a random result" mode.  There doesn't appear to be a way to exit edit much less navigate the file or edit anything.

gedit ane edit --help are amazingly unhelpful.  For instance, the help for edit shows that you can apparently run it in different modes, and that "view" is the default mode.  But then forgets to suggest the other possible modes.

Sorry for the rant.  I'm really frustrated right now -- mostly because what should be VERY simple, is VERY unachievable for me.

Any suggestions beyond driving to the liquor store or reinstalling? :)

Best regards,

Craig Mitchell, St. Louis, MO[/QUOTE]

The GRUB menu is owned by root, you have to be super-user/admin/root to edit it.

Type sudo in front of a command to execute that command with super user privileges. I have a feeling you don't know what permissions are, so please read up on this first:

[http://en.wikipedia.org/wiki/Unix_permissions](http://en.wikipedia.org/wiki/Unix_permissions)

Then read this:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

It will make you understand everything a little better. On a Linux system, you only have write permissions for the files in your home directory, everything else is owned by root or other users.

---

### Post by nealklomp on 2006-04-22
I am with you on the color, however, I don't know that the negative 'poop' adjective is entirely required. I have a frriend who avoided Ubuntu for several months because of it--she eventually installed it and is in love, but we spent sometime erradicaticing the color. It is gone on my computer, except in the first intializing-before login screen. Art Manager is a great app, edit login to change the color, new splash, new desktops, new themes and its a totally slick system.
I understand the message of the color scheme, but it is really one of the ugliest colors and the theme most certainly reperesents a lack of feminine input.

---

### Post by drummer on 2006-04-22
gedit doesn't work because it needs to be run in a GUI (eg. when you are logged into Gnome). I think edit is a symlink to the program Vi, which is a very powerful editing tool, but also immensly user UN-friendly. An easier alternative is nano. You just type and navigate how you normally would in a gui based text editor, and to save, just Ctrl-O, and exit, Ctrl-X. There are instructions on the available commands in nano at the bottom of the program.

---

### Post by Gustav on 2006-04-22
For an easy to use editor in the cli, use nano.

EDIT: Too late again :)

---

### Post by mybootorg on 2006-04-22
[QUOTE=mostwanted]I have a feeling you don't know what permissions are, so please read up on this first:
[/QUOTE]

I think I understand permissions and also, roughly what sudo accomplishes: the equivalent of running a program under superuser identity.

The same can be accomplished by just switching to the root user via su, correct?  Everything from that point on will run as root, correct?

All of the things I attempted in my first post where done under the identity of root@host

---

### Post by mybootorg on 2006-04-22
[QUOTE=drummer]An easier alternative is nano. You just type and navigate how you normally would in a gui based text editor, and to save, just Ctrl-O, and exit, Ctrl-X. There are instructions on the available commands in nano at the bottom of the program.[/QUOTE]

[QUOTE=Gustav]For an easy to use editor in the cli, use nano.

EDIT: Too late again :)[/QUOTE]

nano does not work for me in the rescue mode.  I get a "bterm error". Whatever that means...

---

### Post by mybootorg on 2006-04-22
I am happy to say "**CASE CLOSED**".  By trial and error, I figured out the neccessary commands in vim to edit the menu.lst.  Then some more trial and error later, I stumbled upon the :help  And a little guesswork later, I discovered that :write would save my changes.

I kept waiting for this archaic editor to ask him to insert the next punchcard but it never did.

Oh well, it was a learning experience. Thanks everyone for your suggestions.

---

### Post by Mustard on 2006-04-22
[QUOTE=mybootorg]I am happy to say "**CASE CLOSED**".  By trial and error, I figured out the neccessary commands in vim to edit the menu.lst.  Then some more trial and error later, I stumbled upon the :help  And a little guesswork later, I discovered that :write would save my changes.

I kept waiting for this archaic editor to ask him to insert the next punchcard but it never did.

Oh well, it was a learning experience. Thanks everyone for your suggestions.[/QUOTE]

Hehehe..I hate vi/vim with a passion. I can feel your pain. :D

---

### Post by drummer on 2006-04-22
hehe... vi is great if you know how to use it, but it is a pain in the butt and not very helpful if you're just thrown into it. I used to hate it, but had to learn how to use it for uni and now it's not so bad. It's just a bit different, there is 'command' mode and 'insert' mode, basically, you press i to get into insert mode, and Esc gets you back to command mode. In insert mode you can enter text, and also delete it, and in command mode you do everything else, deleting, changing words, formatting, search/replace, etc. Shift-ZZ to save and :q! to quit without saving is all you really need to know if you're just doing a bit of quick, basic editing.

---

