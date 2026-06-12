---
title: "experiment."
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by richieboy on 2006-04-17
if i understand correctly, i can just run the xserver and call up programs using the command line.  is this right?  if so, how do i get my computer to boot up just into x?  then how do i start the command line?  then how do i change it back if i don't like it?  and where can i get a list of commands to call programs up, eg:  :$ synaptic;  :$ mozilla-firefox?  that kind of thing.

please help.  i think this might be fun.

thanks,
rich

---

### Post by jazzmuzik on 2006-04-17
The X server runs by default. Just open a terminal (Applications, Accessories, Terminal) and type a command like 'sudo synaptic' . You can also press Alt-F2 and enter a program name.

A list of commands? There are hundreds, maybe thousands of commands. As for programs look in the menus or in Synaptic for programs that are installed or could be installed. I'm constantly learning about new programs. Somebody may mention a program and I go to Synaptic to see if it's available, etc.

This will show all the program files in bin directories:

slocate -ir bin/ | more

BTW, running 'slocate -ir bin/ | wc -l' reveals 3434 programs in bin/ directories. Not all of those are real programs though.

---

### Post by dickohead on 2006-04-17
A default install will always start you in X, running the command gnome-terminal from the run dialog (alt+f2) or Applications-Accessories-Terminal will give you the console, so too would Ctrl+Alt+F1 through to F6 but that drops you out of X.

To run a program like firefox just type: firefox or firefox &

Try them both to see the difference.

You could always just select firefox or similar from the menu too...

---

### Post by richieboy on 2006-04-17
hmmmm.  i guess i'm confused.  i thought i could make the machine boot up into just the terminal, no gui.  and then i could use the terminal to call up programs.  does that make sense?  i'm still pretty new to this.
thanks,
rich

---

### Post by richieboy on 2006-04-18
i tried ctrl-alt-f1 and that's what i want but i still want to be in x.  does that make sense?  i want no guis when i boot up, just the terminal.  doing ctrl-alt-f1 got me just the terminal.  it wouldn't allow firefox.  i think the message was "can't start display".
rich

---

### Post by jazzmuzik on 2006-04-18
I'm sure it's possible. I used to know how to do it in RedHat, but that won't help you. (hehe) It's a simple thing though. Hmm. Look at /etc/inittab. At least in Redhat when you change the default runlevel that would determine the mode it would boot into.

Mine shows:
id:2:initdefault:

If you change the 2 to a 3 the default runlevel will be 3. I think 3 is the text mode. 2 is definitely gui in Breezy. Search around for the runlevels before listening to me though. :)

Try this:

[http://ubuntuforums.org/showthread.php?t=10736&highlight=init+runlevels+startx](http://ubuntuforums.org/showthread.php?t=10736&highlight=init+runlevels+startx)

---

### Post by John.Michael.Kane on 2006-04-18
Server install=ubuntu base from there you can edit your sources.list with vi or nano then # apt-get update. from there # apt-get install the files you want ie: xubuntu-desktop

---

### Post by jazzmuzik on 2006-04-18
[QUOTE=richieboy]i tried ctrl-alt-f1 and that's what i want but i still want to be in x.  does that make sense?  i want no guis when i boot up, just the terminal.  doing ctrl-alt-f1 got me just the terminal.  it wouldn't allow firefox.  i think the message was "can't start display".
rich[/QUOTE]

Whoa! Firefox won't run from a ctrl-alt-f1 text mode screen. Firefox is a gui only program.

Perhaps what you want is to be in the gui but open a terminal. Try Applications, Accessories, Terminal. You can run any gui program from there.

---

### Post by richieboy on 2006-04-18
will xubuntu boot up into command line and allow me to call up gui programs from there?

---

### Post by jazzmuzik on 2006-04-18
[QUOTE=richieboy]will xubuntu boot up into command line and allow me to call up gui programs from there?[/QUOTE]

Already explained.

---

### Post by John.Michael.Kane on 2006-04-18
richieboy it would seem you asking to be tought how to use the comandline in which case it would take someone here a while to walk you through every comand. so here are some links that may help you on your quest. 

[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
[http://www.comptechdoc.org/os/linux/howlinuxworks/linux_hlxwindows.html](http://www.comptechdoc.org/os/linux/howlinuxworks/linux_hlxwindows.html)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.tuxfiles.org/linuxhelp/shortcuts.html](http://www.tuxfiles.org/linuxhelp/shortcuts.html)
[http://www.faqs.org/docs/Linux-HOWTO/XDMCP-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/XDMCP-HOWTO.html)
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/2531-keyboard-shortcuts-x-windows-command-line.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/2531-keyboard-shortcuts-x-windows-command-line.html)
[http://www.die.net/doc/linux/man/man1/xserver.1.html](http://www.die.net/doc/linux/man/man1/xserver.1.html)
[http://www.linux.com/howtos/XWindow-User-HOWTO/cli.shtml](http://www.linux.com/howtos/XWindow-User-HOWTO/cli.shtml)
[http://lug.boulder.co.us/docs/vi_vim_howto.html](http://lug.boulder.co.us/docs/vi_vim_howto.html)
[http://www.vmunix.com/~gabor/vi.html](http://www.vmunix.com/~gabor/vi.html)
[http://www.eng.hawaii.edu/Tutor/vi.html](http://www.eng.hawaii.edu/Tutor/vi.html)

---

### Post by dickohead on 2006-04-19
I think what you're after is to know if you can type 'firefox' or similar at the command line and have firefox startup - the answer is no.

Firefox requires an X-Server to run on, without the X-Server present where will firefox open the gui? The answer is nowhere, as it says when telling you there is no display.

Something you might enjoy doing however is looking into SSH -X with this you can load up programs from one machine (command line interface) and have them appear in the other machines gui  very handy stuff, kind of like primitive terminal  services.

---

### Post by steve.horsley on 2006-04-19
[QUOTE=richieboy]i tried ctrl-alt-f1 and that's what i want but i still want to be in x.  does that make sense?  i want no guis when i boot up, just the terminal.  doing ctrl-alt-f1 got me just the terminal.  it wouldn't allow firefox.  i think the message was "can't start display".
rich[/QUOTE]

What you ask for is not possible. There are two very different types of "terminal". One is a text-only console, and you always have six of those, on Alt-F1 to F6. These are fundamentally incapable of displaying GUI type stuff. The other type is a bit-mapped terminal, called an X terminal. This appears on Alt-F7 when you start the X server. The X server is fundamentally incapable of displaying "character" data. It only does bit-mapped graphics. To get you a command line type capability in X, there is gnome-terminal of xterm, both of which convert the text data into a bit-mapped font for display. 

It is the type of display that is the important thing. You can launch firefix from a text console but it bombs out because it can't find an X server to paint its graphics on. However, you can launch firefox from inside a command-line window in an X server, because the X server already exists (you are already INSIDE the X server), so firefox is then happy.

Why can't you launch firefox from a text login on F1 and have its window appear in F7? Well you can, but you have to do some tiikering. I'm not sure on the details, but I think you have to issue the command **xhost +** to the X server, and set a DISPLAY attribute in the text console. In theory, this can even make the firefox window appear on another PC. Years ago, I thought it was funny to make assorted pictures appear on other peoples PCs while they were using them.

---

