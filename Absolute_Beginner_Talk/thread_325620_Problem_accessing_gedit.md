---
title: "Problem accessing gedit"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Tzumli_D on 2006-12-26
I am trying to include the multiverse and universe (?) into my resources list ,so in the terminal wrote:
sudo gedit /etc/apt/sources.list

After I put in my password it just sits there, nothing happens, no prompt, no gui.

After closing the terminal and reopening it I wrote
gedit
and the Gedit window opened, but I could not change anything because I don't know how to tell it what my password is etc.

So I've done a search here for gedit and had a look at some of the threads:
[http://www.ubuntuforums.org/showthread.php?t=325271&highlight=gedit](http://www.ubuntuforums.org/showthread.php?t=325271&highlight=gedit)
seemed to have what it wanted so I tried:

~$ gksudo gedit /etc/apt/sources.list
(gedit:8724): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
~$ 
The Gedit window popped up but did not display anything.

Is it possible that there is somethingwrong with my version of terminal?
I'm trying to delete something, but cannot get to do it because I can't change the directory. When I write:
man cd
the response is: No manual entry for cd
I have used the synaptic manager and reloaded terminal and gedit using the package manager, but I still can't get access to gedit.

Oh, I've got ubuntu edgy

---

### Post by spockrock on 2006-12-26
it seems strange that there is nothing in your source.list, what does

```
cat /etc/apt/sources.list
```

do?


Also if you want to enable universe and multiverse open synaptic, then settings>repositories then pick the Ubuntu 6.10 tab, and check the universe and multiverse tabs.

---

### Post by Sef on 2006-12-26
> sudo gedit /etc/apt/sources.list

Since gedit is a graphical installer, the code should be done this way:

```
gksudo gedit /etc/apt/sources.list
```

Otherwise you could damage your system.

---

### Post by bapoumba on 2006-12-26
You can set aside the gedit problem for now.

You can edit your sources.list with another editor, nano for ex which does not run in graphics mode :

```
sudo nano -B /etc/apt/sources.list
```
the -B will backup your original sources.list file with the ~ extension. CTRL + O to save it (samen name), CTRL + X to exit.
But first, as recommended, post your current sources.list with ```
cat /etc/apt/sources.list
```

Can you access other root applications in graphics mode ? What does return ```
gksudo -S  -d  gedit 
```
The warning is a [bug]("https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917") and should not prevent gedit from running.

---

### Post by 3rdalbum on 2006-12-26
Until we can figure out exactly what is going on, you can do "gksudo gedit" and then do File > Open... and open the file that way. Alternatively, since you say you can get into Synaptic, go System > Administration > Software Sources and change the repositories that way.

---

### Post by Tzumli_D on 2006-12-26
> **3rdalbum said:**
> Until we can figure out exactly what is going on, you can do "gksudo gedit" and then do File > Open... and open the file that way. Alternatively, since you say you can get into Synaptic, go System > Administration > Software Sources and change the repositories that way.
Interesting results. I tried the second way first, and it kept freezing on me.

I then tried gksudo edit, and the window opened with a prompt for password, so I made the uncomments and saved. And then closed the window.
When I looked at the terminal window, although I did have an opened window etc which worked successfully (it seems) I still ended up with an error message:
denise@alexandria:~$ gksudo gedit
(gedit:12321): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Is this a genuine bug then? and should I report it? If so how?
Denise

---

### Post by Tzumli_D on 2006-12-26
[Can you access other root applications in graphics mode ? What does return ```
gksudo -S  -d  gedit 
```
The warning is a [bug]("https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917") and should not prevent gedit from running.[/QUOTE]

These are the results I got for this last thing:
denise@ale:~$ gksudo -S  -d  gedit
No ask_pass set, using default!
xauth: /tmp/libgksu-ebHbdb/.Xauthority
STARTUP_ID: (null)
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gedit
buffer: -
(gedit:12728): -
No password prompt found; we'll assume we don't need a password.

(gedit:12728): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by bapoumba on 2006-12-26
> **Tzumli_D said:**
> 
denise@alexandria:~$ gksudo gedit
(gedit:12321): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Is this a genuine bug then? and should I report it? If so how?
Denise

Yes it's a bug (I linked it just above). And it's a warning, graphics applications will work just fine ;)

edit : and your root access to gedit is fine (as for other graphic applications, for sure). All set.

---

### Post by Tzumli_D on 2006-12-26
I must admit, I don't understand parts of your reply.
"I linked it just above"  does that mean I don't have to do anything?

"Graphics applications will work just fine"  - am I using graphics applications?

---

### Post by bapoumba on 2006-12-26
> **bapoumba said:**
> 
The warning is a [bug]("https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917") and should not prevent gedit from running.

Sorry, yes the bug is already filed . You can add comment to it if you wish. Everyone has it, this is a known issue, not critical.

And yes, gedit is a graphical application (it uses X-server. Nano can run in text mode).

I am looking for links for you to read.

edit :
[http://en.wikipedia.org/wiki/Graphical_User_Interface]("http://en.wikipedia.org/wiki/Graphical_User_Interface")
[http://en.wikipedia.org/wiki/Text_User_Interface]("http://en.wikipedia.org/wiki/Text_User_Interface")

---

### Post by Tzumli_D on 2006-12-26
Thanks for those links, I'll follow them up. :D

---

