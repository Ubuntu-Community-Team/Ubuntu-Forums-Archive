---
title: "Stuck in Dapper Install/Reboot"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Kurt_Alan on 2006-05-22
****[FONT="Arial Black"][/FONT]

Hi,

I have installed Dapper 6.06 beta install

In the reboot I am stuck at this cursor:

login@unbuntulocalname $ ___

What goes here? I can't proceed!  I only know of 3 choices: password, local name, and log-in. . .

---

### Post by Sef on 2006-05-22
So from what I understand, it installed from the disc without any problems, then you removed the disc and pressed enter to reboot.  Upon reboot you encountered the problem of the login. Correct?

---

### Post by Kurt_Alan on 2006-05-22
**[SIZE="5"][/SIZE]**


Yes, I have installed successfully and removed cd.  I have created a user name, host name, and password.

Not a malfunction, just don't know what to type next. . . 

kurt@unbuntuDorothyJ $ ____ ?

Gotta go to work . . . get back to you later. Thanks for your help.

---

### Post by Sef on 2006-05-22
What's your graphics card?

Sounds like a problem with your graphics card.  It should boot up to a login screen.

---

### Post by Kurt_Alan on 2006-05-22
There's nothing wrong with my graphics card; I had just used it for WinXP, Red Hat WS.

I don't think there's a malfunction.  I'm being asked for information and I don't know what I'm being asked for.

The prompt is:

UserLogin@ubuntuLocalHost $ ____?

The OS has ALREADY identified my user name and password, so I think that shows a good install.

So what is this prompt asking for and what do I type in??

Come on, Sef, you can figure it out! You have a lot more beans than I do!

---

### Post by user1397 on 2006-05-22
what happens if you type ```
startx
```?

---

### Post by user1397 on 2006-05-22
if that does nothing, maybe you accidentally installed the server edition of dapper beta.
you just have to type in:
```
sudo apt-get update
```and then ```
sudo apt-get install ubuntu-desktop
```
then ```
sudo reboot
```
and it should work.  if it still doesn't, then its definitely a graphics card/driver problem (it doesn't matter if windows or redhat recognized your graphics card, some distros just have a hard time with recognizing hardware)
If this is the case, i don't know what to do, ask for someone else's help (i'm no graphics card/driver expert!!:???:)

---

### Post by Sef on 2006-05-22
or you could do this instead:

From the Terminal:

sudo apt-get update

sudo apt-get install ubuntu-base ubuntu-desktop

sudo apt-get dist-upgrade

---

### Post by Kurt_Alan on 2006-05-22
[SIZE="5"]****[/SIZE]

More than one hour's worth of files are being installed from the cd rom (with above commands)!

I DID install the server version, not accidentally, but without knowing what that meant!  I just wanted Dapper 6.06 NOT live and this was all I could find.  (Could not find install on the live version of the 6.06 beta).

Does this mean I installed without the GUI????     :confused:

---

### Post by user1397 on 2006-05-22
[quote=Kurt_Alan]

More than one hour's worth of files are being installed from the cd rom (with above commands)!

I DID install the server version, not accidentally, but without knowing what that meant!  I just wanted Dapper 6.06 NOT live and this was all I could find.  (Could not find install on the live version of the 6.06 beta).

Does this mean I installed without the GUI????     :confused:[/quote]
thats exactly what it means

---

