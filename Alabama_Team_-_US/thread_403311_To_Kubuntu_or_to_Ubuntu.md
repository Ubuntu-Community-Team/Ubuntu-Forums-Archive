---
title: "To Kubuntu or to Ubuntu?"
date: 2007-04-06
forum: Alabama Team - US
---

### Post by MerlinsLair on 2007-04-06
Ok, I experimented with both and decided on Ubuntu with the Gnome desktop system. Now my question is...how does one go about uninstalling Kubuntu? No sense in it staying on if I'll not be using it, right?

Guess this really shows off my newbie status, huh? :lolflag:

---

### Post by stalker145 on 2007-04-06
[Here's a good place to start.]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by MerlinsLair on 2007-04-06
Holy cow! How the heck did I miss that? Guess I couldn't see the forest for the trees! Thanks stalker145...appreciate it.

---

### Post by stalker145 on 2007-04-06
> **MerlinsLair said:**
> Holy cow! How the heck did I miss that? Guess I couldn't see the forest for the trees! Thanks stalker145...appreciate it.

No problem. I'm happy to help.

---

### Post by MerlinsLair on 2007-04-06
Ok, I'm getting this now:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


And when I do, I get the next phrase:

> dpkg: requested operation requires superuser privilege

What's up?

---

### Post by stalker145 on 2007-04-06
> **MerlinsLair said:**
> Ok, I'm getting this now:



And when I do, I get the next phrase:



What's up?

Did you make sure to put 'sudo' before the command? It's what comes to *my* mind...

---

### Post by wesley_of_course on 2007-04-06
Wesley here ; 


      Fellow Noob here ,  Sudo  ?

---

### Post by MerlinsLair on 2007-04-06
Yes, sudo added but it doesn't run. Only goes back to my original command prompt...hmmm Btw, added yahoo messenger to my collection for IM'ing. ;)

Sudo is the root user without logging out of a normal user account and having to log back in as an administrator or "root" to perform admin tasks. This is how Ubuntu does it and it's so much easier this way.

Check this page out as it has several useful links about it: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security) :)

---

### Post by crane on 2007-04-06
So running *sudo dpkg --configure -a* you are still getting 
dpkg: requested operation requires superuser privilege?

---

### Post by MerlinsLair on 2007-04-07
Yes, odd isn't it? Sorry for the late reply but my grandson arrived last night. Will check into this further later this morning. ;)

---

### Post by crane on 2007-04-09
Did you find any resolve to this?

---

### Post by MerlinsLair on 2007-04-09
Actually, not yet Crane. Have been going through some serious re-training at work due to a transfer from one department to another. Gotta love downsizing! :^/

Have some off days coming up and will get back to researching this again. Right now, it's not all that bad. If nothing else idea-wise becomes available, I'll re-install Ubuntu. Of course, that'll be a last resort.

Also, found out that Totem doesn't play well with Firefox 2.0.0.3. It simply will not play any mpg's. I ran across something about this somewhere...probably the site here: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) when researching the Firefox upgrade. Know of any other movie players that are good for Ubuntu/Linux?

---

### Post by Steven_B on 2007-04-09
Mplayer, GXine and VNC are all good media players.  You probably want to install the "gstreamer-plugins-" packages (If you haven't already), as they allow you to play additional media formats.

Does sudo give you an error every time you use it?
You could try booting into "rescue mode", which will log you in as root.  You can then run commands without "sudo".  You'll just have a command line (no GNOME, etc.), so make sure you're confident with the command line first.

---

### Post by crane on 2007-04-09
Yea, look into installing gstreamer-plugins. Look at this as well -->[Ubuntu Guide - Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")
I believe I just installed mplayer from synaptic, gstreamer-plugins, and then I added the codecs pack from the mplayer site.(not sure if that is still needed.

---

### Post by johndavid400 on 2007-04-10
MerlinsLair's:
try installing the scripts from these links, Multimedia codecs and VLC:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28VLC.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28VLC.29)

... this should get mpg's working.

Also, do you remember whether you used apt-get or aptitude to install Kubuntu?
If I recall correctly, there is more work involved to remove Kubuntu (or any program for that matter) when you used apt-get to install it.

---

### Post by MerlinsLair on 2007-04-11
> **johndavid400 said:**
> MerlinsLair's:
try installing the scripts from these links, Multimedia codecs and VLC:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28VLC.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28VLC.29)

... this should get mpg's working.

Also, do you remember whether you used apt-get or aptitude to install Kubuntu?
If I recall correctly, there is more work involved to remove Kubuntu (or any program for that matter) when you used apt-get to install it.

Thanks for the tips guys! Really appreciate it. :)  As for the Kubuntu install...I think I had installed it via Synaptic.

---

### Post by MerlinsLair on 2007-04-11
Got the Kubuntu issue resolved albeit not the way I would have preferred. Wound up re-installing and adding everything back in that I wanted so far. Also, the videos now work just fine. Well, except for any Windows movie files. Those I get sound only. LOL

Btw, I'm on the channel in IRC atm if anyone wants to drop by and shoot the breeze! :)

#ubuntu-alabama ;)

---

### Post by crane on 2007-04-11
> **MerlinsLair said:**
> Got the Kubuntu issue resolved albeit not the way I would have preferred. Wound up re-installing and adding everything back in that I wanted so far. Also, the videos now work just fine. Well, except for any Windows movie files. Those I get sound only. LOL

Btw, I'm on the channel in IRC atm if anyone wants to drop by and shoot the breeze! :)

#ubuntu-alabama ;)

Cool man. Today has been crazy at work so I didn't get the chance to drop in. I should be on irc tonight.!

---

### Post by MerlinsLair on 2007-04-12
No problem. I'll be at work tonight though. Maybe I'll catch you before I leave...we'll see.

---

### Post by crane on 2007-04-12
I hope things calm down next week. All of our service Dept. is in Virginia working so there are 3 of us holding the fort. Normally there are 7 or 8. Man I love work, never a dull moment!

---

### Post by crimsontide on 2007-04-13
Anyone ever try xfce?  Xbuntu?

---

### Post by crane on 2007-04-13
I have tried it and it seems pretty nice. I just really like gnome. Xubuntu does run on an older laptop that Ubuntu will not run on so it does have some big advantages. Fluxbuntu is also nice... or was it flubuntu I can't remember right now.

---

