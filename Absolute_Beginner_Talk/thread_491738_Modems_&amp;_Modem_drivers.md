---
title: "Modems &amp; Modem drivers"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Georgeiger on 2007-07-04
Does Ubuntu support Swann external dial-up Speed Demon modems and if so, what driver should I use and where can I get one? If not, what is the best buy Modem I can get? My computer itself is a 2.4 Gig Celeron, about 3 years old, with half a Gig of RAM. I'm a real newbie, first day in fact, with ubuntu. Thank you.
   Georgeiger

---

### Post by antmenj on 2007-07-04
If its a full modem yes.  If its a winmodem, and it probebly is, maybe with a bit of stuffing around.

See [http://www.linmodems.org/](http://www.linmodems.org/)

Edit----------------------------------------------
I should read better.

External modems **YES**

---

### Post by antmenj on 2007-07-04
Bring up the terminal: Applications> Accesories>Terminal> 
type:
sudo pppconfig 
enter your password
fill in the details and do NOT change the conection name from "provider"
save and exit

To dial open the terminal and type pon to dial and poff to hang up.  Better still create 2 desktop icons to do this at the click off the mouse.

No need to worry about drivers for external modems.  Just plug in to an empty com port.

---

### Post by Georgeiger on 2007-07-04
To show you what an absolute dummy I am, I don't even know how to make a shortcut using Ubuntu. Also, when I logon to this thread, I am told that I have an unread provate message. How can I pick it up?
   Thank you, and best regards, Georgeiger

---

### Post by Bartender on 2007-07-06
When you bring your mouse over the text saying "Private Messages" you'll see that it's a link.  Click on it.

---

### Post by Georgeiger on 2007-07-06
Thank you. That worked just dandily. I still can't figure out how to make a pon or a poff shortcut. Or any shortcut for that matter. I can see this is going to be a steep learning curve for me.
   Best regards, Georgeiger

---

### Post by Bartender on 2007-07-07
Find the application you want to put on the desktop (such as Thunderbird, found in Applications>Internet I believe) and just drag the icon to the desktop or right-click on it and you'll get a context menu.

I'm not sure how to make a shortcut for pon and poff.  It's probly really easy ;)

---

### Post by antmenj on 2007-07-07
> **Bartender said:**
> Find the application you want to put on the desktop (such as Thunderbird, found in Applications>Internet I believe) and just drag the icon to the desktop or right-click on it and you'll get a context menu.

I'm not sure how to make a shortcut for pon and poff.  It's probly really easy ;)

Its been a wile since I did this as I now use a seperate smoothwall machine but if I remember right......

*Right click desk top in a blank area

*Create Launcher

*Put dial or what ever you want to see on the screen in the name box

*Put pon in the command box

I think you get the idea for poff

---

### Post by Georgeiger on 2007-07-09
> **antmenj said:**
> Its been a wile since I did this as I now use a seperate smoothwall machine but if I remember right......

*Right click desk top in a blank area

*Create Launcher

*Put dial or what ever you want to see on the screen in the name box

*Put pon in the command box

I think you get the idea for poff
Thank you. It works perfectly if you click on the icon by right clicking and clicking on "Open". You are rapidly becoming my newest best friend. Thank you again.
   Regards, Georgeiger

---

