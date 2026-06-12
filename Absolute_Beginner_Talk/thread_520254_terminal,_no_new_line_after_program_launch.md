---
title: "terminal, no new line after program launch"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by japribik on 2007-08-08
When I launch a program from the command line like firefox, the launch of the program is successful.  However,  after the launch I get nothing in the terminal.  I try to type things like exit or reset and hit enter but nothing comes of it.  I will not get a new line until I exit the program or get a new terminal tab.  Is this normal?  How can i fix it?

---

### Post by skwishybug on 2007-08-08
I believe this is normal, its always done the same thing for me.

---

### Post by overdrank on 2007-08-08
> **japribik said:**
> When I launch a program from the command line like firefox, the launch of the program is successful.  However,  after the launch I get nothing in the terminal.  I try to type things like exit or reset and hit enter but nothing comes of it.  I will not get a new line until I exit the program or get a new terminal tab.  Is this normal?  How can i fix it?

HI I don't believe there is a fix, but to launch a program you can use the alt,F2 keys instead of the terminal. :KS

---

### Post by HermanAB on 2007-08-08
To get the prompt back and put the program into the background, append the command with an ampersand:
$ gedit &

If you forgot the ampersand, press 'Ctrl-Z', to stop the program temporarily, then type 'bg' to put it in the background.  Search Google for 'linux jobcontrol' for more information.

Cheers,

Herman

---

### Post by japribik on 2007-08-08
Awesome, Thanks Guys!

---

### Post by Hobo Joe on 2007-08-08
When you launch a program through the terminal, it stays like that to show status/error messages etc. Which is very helpful if you're trying to fix a problem. If you just want to run a program normally, just do what overdrank said, and use alt+f2.

---

### Post by Chaotic Thought on 2007-08-15
Also, be aware that if you launch a program from the terminal using the ampersand (as in **gedit &**), and then close the terminal window while that program is still running, that program will be terminated along with your terminal window. To prevent that from happening, issue the **disown** command in your terminal before closing it.

Example:
1. Launch a terminal window
2. type **gedit**, press return
3. press CTRL+Z inside your terminal window
. . (note that at this point, **gedit** is "frozen"--it won't respond to any mouse clicks, etc
4. type **bg**, press return
. . (that unfreezes **gedit**, allowing it to run in the background)
5. type **disown**, press return
6. close your terminal window

And then **gedit** should still be running. Note that the issuing the command **gedit &** is like steps 2, 3, and 4 occuring all at once.

---

