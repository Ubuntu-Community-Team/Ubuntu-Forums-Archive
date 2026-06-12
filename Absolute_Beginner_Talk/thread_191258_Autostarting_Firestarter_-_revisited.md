---
title: "Autostarting Firestarter - revisited"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Farthing-or-less on 2006-06-07
Trying to get firestarter to start up on login without having to type in the password.  I've tried the method outlined on the fs site, and listed on variou areas of this forum over and over again: adding to the sudoers file <username> ALL= NOPASSWD: /usr/sbin/firestarter. When I do that, however, Firestarter won't start at all. I've played arouund with the spaces and places, but no go. Firestarter will not start until i remove that line from the sudoers file and then restart the system. 

Of course, because I can't get the first part to work, adding firestarter to the session startup list doesn't produce results.

Also, i repeatedly come across one poster claiming that Firestarter can be made to autostart from its preferences. Well, that option certainly doesn't seem to appear in the GUI preferences, so how can I get to the preferences referred to?

Using Dapper, if that is of any relation.](*,)

---

### Post by Robgould on 2006-06-07
The only way I know to do it is with what you are trying...edit the sudoers file and add to session start-up.  I have never gotten this to wokr long term reliably for me though.   I have given up on firestrater just for that reason.  
 
You actual firewall - iptables- does start up when ubuntu starts.  Its just a pain in the butt to configure.  I'm sure someone thinks its a piece of cake, but it sucks to me.  
 
I wish Ubuntu had a simple firewall gui like Red Hat.   I know this did not help you even a little bit.  Sorry.

---

### Post by cyangecko on 2006-06-07
I was also having problems with firestarter.  When I typed'sudo firestarter' in my terminal i got an error like this:

> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

(firestarter:5530): Gtk-WARNING **: cannot open display:

After searching through these forums I found my solution not only to that but making an autostart script.  

First off, check out this thread:  [http://www.ubuntuforums.org/showthread.php?t=136934]("http://www.ubuntuforums.org/showthread.php?t=136934")

on page 6 of this thread, scroll down to #56.  You will find that jurgen.lists created a script to start firestarter at login.

I used that script except in my sessions I had to modify a few things. 

Where jurgen wrote:

> Added to /etc/sudoers:
jurgen ALL=(root) NOPASSWD: /usr/sbin/firestarter

i had to delete the part that says (root). so mine says 
> cyangecko ALL=NOPASSWD: /usr/sbin/firestarter

Secondly, I had to add it to my startup list in sessions as:
/home/cyangecko/firestarter.sh 

as opposed to:
~/firestarter.sh

That worked for me.  Hope this helps.

---

### Post by kaamos on 2006-06-07
[QUOTE=Farthing-or-less]Also, i repeatedly come across one poster claiming that Firestarter can be made to autostart from its preferences. Well, that option certainly doesn't seem to appear in the GUI preferences, so how can I get to the preferences referred to?[/QUOTE]

Not in dapper. It starts automatically. :)

There is a script /etc/init.d/firestarter that starts the firewall when the machine boots up. If you are feeling unsure whether the firewall is running, use
```
sudo /etc/init.d/firestarter status
``` to check. Please note that the firestarter gui is completely separated from the firewall, so you won't get the trayicon by default and the gui is **not** needed for the firewall to be active. The gui is a frontend for the firestarter daemon and that again uses iptables that is a part of the linux kernel.

---

### Post by terminatorkobold on 2006-06-07
It is a small problem with sudo.

The first post of the following thread explains how to get it to work without a special script:
[http://www.ubuntuforums.org/showthread.php?t=187899]("http://www.ubuntuforums.org/showthread.php?t=187899")

---

### Post by graigsmith on 2006-06-07
> I wish Ubuntu had a simple firewall gui like Red Hat

thats what firestarter is.  it is just a gui to iptables.

---

### Post by Farthing-or-less on 2006-06-07
Wow. Lot's of options. The command for checking that Firestarter is running is probably enough though. I know it's there, and can just bring up the GUI, if I need to stop or start it. 

Thanks all very much!!!

---

### Post by Robgould on 2006-06-08
[quote=graigsmith]thats what firestarter is. it is just a gui to iptables.[/quote]
 
I know what firestarter is.  Red Hat has a menu item in the gnome menu that is there all the time.  You turn the firewall on or off there, open ports, whatever.  It jsut starts.  No need to do any configuring for it to autostart.  No need to install it seperately.  It's just part of the base.  That is what I mean I wish Ubuntu had.

---

### Post by timetunnel on 2006-06-08
Why are you trying to put Firestarter into an autostart or session startup? From the docs of Firestarter:
"A frequently asked question is, what is the state of the firewall when you are not running the Firestarter program? The answer is that it depends. If you installed the Firestarter from a binary package such RPM or Deb, the firewall will be running all the time (dial-up users excluded) and independent of the graphical interface, even after a reboot."

So, I always thought that installing the Firestarter deb is all you need (except for creating some policies) and it will be up all the time.

---

### Post by timetunnel on 2006-06-08
Never mind. You're talking about autostarting the GUI. Sorry for my former posting.

---

### Post by 23meg on 2006-06-08
[QUOTE=Farthing-or-less]... and can just bring up the GUI, if I need to stop or start it. 
[/QUOTE]
You don't need the GUI even to stop or start it. 
```
sudo /etc/firestarter/firestarter.sh stop
```  or ```
sudo firestarter --stop
``` stops it.
```
sudo /etc/firestarter/firestarter.sh start
``` or ```
sudo firestarter --start
``` starts it.

The best general practice from a physical security standpoint is not to have the Firestarter GUI run at startup.

---

