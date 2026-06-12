---
title: "Limit CLI output to one screen at a time"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by lespaul_rentals on 2008-01-16
I have an Ubuntu 6.06 server going.  Obviously it's command-line.  When I run a command that produces a lot of output, say "ls" or "apt-cache search", I can't read it all because it goes by too fast and I can't scroll.  I know there's some way to make it go one screen at a time, I believe by using a pipe |.  Can anyone help me out?

---

### Post by eolson on 2008-01-16
example

ls -l | less

  or

ps -ax | less

It will stop scrolling and you'll be able to scroll up and down with your arrow keys.

the pipe symbol is a shifted backslash on my machine.

---

### Post by drs305 on 2008-01-16
You can add "  | less  " to the command. Then use pgup and pgdn to view more.

---

### Post by lespaul_rentals on 2008-01-16
Thanks!

---

### Post by Sukarn on 2008-01-17
You can also scroll using Shift+PageUp and Shift+PageDown

---

### Post by Joeb454 on 2008-01-17
I never knew that...I know you can use a mouse, but I've not got round to installing Ubuntu server on my spare PC yet, so not sure about the server edition :)

I'll probably install it when Hardy (8.04) is released

---

### Post by Sukarn on 2008-01-17
> **Joeb454 said:**
> I never knew that...I know you can use a mouse, but I've not got round to installing Ubuntu server on my spare PC yet, so not sure about the server edition :)

I'll probably install it when Hardy (8.04) is released

Mouse cannot be used to scroll (at least not by default) in a virtual console (which is what we're discussing in this thread).

I suppose what you are talking about is a terminal emulator like gnome-terminal or konsole.

To switch to a virtual console (even in a desktop installation of ubuntu), press Ctrl+Alt+F1. F1 to F6 are virtual consoles by default, and F7 to F12 are reserved for X-servers by default.

For switching from graphical interface (X-server) to a virtual console or another X-server, you have to press Ctrl+Alt+the function key, but when you're in a virtual console you can skip pressing the Ctrl key.

First instance of X-server (the graphical interface) is started in F7.

---

