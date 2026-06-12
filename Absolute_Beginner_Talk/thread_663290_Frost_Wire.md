---
title: "Frost Wire"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by killermad34 on 2008-01-10
Alright, I have read all around the forums and can't seem to find a fix for this.  I am completely new to Ubuntu or Linux at all for that matter.  I am taking a class on it right now so I figured what better way to get acquainted than just jumping right in, heck, that's how I've learned everything else computers and so far it has worked out well.

I am trying to install Frost Wire.  I downloaded the file and it actually opened up into an installer and said it installed.  Well now I can't find it anywhere.  I even went to the usr/lib/Frost Wire folder and everything is in there but no way to "execute it" so to speak.  Now I went through all the commands on the instructions from the website with no problems, but I still can't find a way to run it.  I have all the latest java installed and up to date, and frankly I am getting a little frustrated with the whole "root" stuff.

So I am looking for a way to get Frost Wire to work, and secondly, a way to become a Root user so I don't have to deal with all these 'you don't have permission to do this and that' problems.

---

### Post by santiagoward2000 on 2008-01-10
> **killermad34 said:**
> Alright, I have read all around the forums and can't seem to find a fix for this.  I am completely new to Ubuntu or Linux at all for that matter.  I am taking a class on it right now so I figured what better way to get acquainted than just jumping right in, heck, that's how I've learned everything else computers and so far it has worked out well.

I am trying to install Frost Wire.  I downloaded the file and it actually opened up into an installer and said it installed.  Well now I can't find it anywhere.  I even went to the usr/lib/Frost Wire folder and everything is in there but no way to "execute it" so to speak.  Now I went through all the commands on the instructions from the website with no problems, but I still can't find a way to run it.  I have all the latest java installed and up to date, and frankly I am getting a little frustrated with the whole "root" stuff.

So I am looking for a way to get Frost Wire to work, and secondly, a way to become a Root user so I don't have to deal with all these 'you don't have permission to do this and that' problems.

Hi!
Frostwire should be under Applications/Network. If it isn't, try opening a terminal and type:
```
frostwire
```
That should open it.

---

### Post by mdpalow on 2008-01-10
Did you install/load Java?

Can't run Frostwire without it... :)

See my link below (any of them will take you to the same page). My script will install Java for you. It's not hard, but for the life of me, I can't remember what the file names are off hand.

Script will do it for you though...

---

### Post by killermad34 on 2008-01-10
Well I typed Frost Wire in the terminal and it loads.  It comes to the screen where you pick your country and where you save your files at all that works fine.  Then it comes to a screen where it wants me to enter a nickname.  And then it stops.  It's still working but it wont let me type in the box at all.  No matter what key I hit nothing enters into the field.

Now me keyboard is obviously working but it wont let me input anything.  Also is there a way I can get an icon for Frost Wire and put it on my desktop?

---

### Post by killermad34 on 2008-01-10
Well I got it to work.  I guess I can't use any folder to save files into but the default one it provides.  When I change the folder, then it doesn't allow me to type anything into the nickname box.  This is really becoming more of a hassle for me than I thought it would.  Isn't there a way just to make yourself a 'root' user and a program that will automatically install these programs instead of having to enter lines of code into a terminal everytime?  

I know it's free so it's not going to be as 'convienient' as Windows, but come on.  I don't want to have to bust out my command prompt skills everytime I need to move a file to a differen't directory because linux wont let me drag and drop.

---

### Post by santiagoward2000 on 2008-01-10
> **killermad34 said:**
> Well I typed Frost Wire in the terminal and it loads.  It comes to the screen where you pick your country and where you save your files at all that works fine.  Then it comes to a screen where it wants me to enter a nickname.  And then it stops.  It's still working but it wont let me type in the box at all.  No matter what key I hit nothing enters into the field.

Now me keyboard is obviously working but it wont let me input anything.  Also is there a way I can get an icon for Frost Wire and put it on my desktop?

The typing problem is quite common. Normally maximizing the window fixes it.
About creating a shortcut, just left-click on the desktop, **Create launcher...** and enter **frostwire** as command.

---

