---
title: "So, I messed up my session... help..."
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by WakkiTabakki on 2006-04-26
I think I managed to mess something up in my Session (via Preferences/Session).
I'm fiddling about with Xgl and Compiz, and have had a few round with scripts starting up via Session. Now, I found this neat trick of selecting the session on the GDM-screen (involved creating a .Xsession and so on)... Although, this is not the problem, thats where it started...

I figured I'll just clean up a bit my Sessions-config. I removed all the stuff that had anything to do with compiz...
I guess I must have managed to screw something up, because the result is this: 
When I log in I get the normal Ubuntu splash with only one icon on it, the Window Manager, and then it freezes for about a minute... It doesn't hang or anything, I can switch over to any tty via ctrl-Fn at any time. It's just like it's waiting for a timeout or something...
Note, this has nothing to do with Xgl/compiz. Same thing happens if I log in with a normal Gnome-session.
When I do a Gnome-failsafe, it starts up just as normal...

I'm posting here 'cus I figure it really has nothing to do with Xgl... Just a nooby messup with the session. 
Another problem is, I don't even know which config or log files are relevant...

Any suggestions?

Thanx
/N

---

### Post by aysiu on 2006-04-26
What happens if you create and log in as a new user?

---

### Post by WakkiTabakki on 2006-05-11
Thanks for the suggestion, but it's not quite what I'm after.
But, yes, a new user does not have the problem. Well, 'cus its this particular users session thats screwed...

The thing is, I may have done a save-session (or something from the CLI) which maybe have done something... (bah, I wish I didn't have to be so vague, but I really don't even know where to start looking...)

I have a wireless network, and I'm using NetworkManager and nm-applet, so a wild guess might be; I log into my session and during, or directly after the init-process starts window-manager it tries (due to my screwed session) connect to the net which isn't up yet (I have to type in my master-password for the wallet before it can connect to my router). 
So, the guess is that the mid-air-freeze during init is due to a timeout of some program executing in synch during startup (thus freezing the init-process until it's timed out).

Well, the problem is essentially this: I don't even know where to start looking. What init-files could be the culprit? Which ones are controlling the login process? Especially directly after or during the time that the icon for 'Window manager' is shown on the splash...

Still stabbing in the dark...
Cheers
/N

---

### Post by 5-HT on 2006-05-11
[quote=WakkiTabakki]
Well, the problem is essentially this: I don't even know where to start looking. What init-files could be the culprit? Which ones are controlling the login process? 
[/quote]
If it's a session-related issue for your user, what about removing ~/.gnome2  ?
It'll be created with the default settings upon the next login.

HTH

---

### Post by WakkiTabakki on 2006-05-11
Sweeeeet! That did it!
Although... It did spark a whole range of other oddities... :-k 

I'll sit down, watch'em and come back later...

/N

---

### Post by 5-HT on 2006-05-11
Glad you could login.
If there are still some other issues about the session, removing the following may help:[LIST]
[*]~/.gconf
[*]~/.gconfd
[*]~/.gnome
[*]~/.gnome_private
[*]~/.gnome2
[*]~/.gnome2_private[/LIST]And possibly even:[LIST]
[*]~/.metacity
[*]~/.nautilus[/LIST]If specific apps are causing problems and they have their own settings folder hidden in your home directory (~/.<name of app>), removing those directories may help as well (good idea to make sure they are just settings though).

They should all get recreated at the next login or the next time the application is run.

HTH

---

### Post by Cirrocco on 2006-05-11
this raises a question...

why aren't all of your prefs kept in a folder called ~/.preferences/ ?

---

### Post by WakkiTabakki on 2006-05-14
Hi again and thanks for all the input...
Ok, since the last time, this has happened:
I removed the .gnome2 folder which had the effect that there are a few more icons lightning up before the init freezes. I've got a feeling that it freezes for a shorter period than before, but thats just a guess...

But on the good side, almost all of the GUI gets loaded now (except nm-applet) so I can, while we're in the hanging garden, start the session-property-tool from the preferences menu...
I've seen that while the init freezes the session is running ```
vino-session --smclient-id default5
``` which I find a bit weird, because there doesn't seem to be an application called vino-session anywhere in my system... Even weirder, I can't seem to find a reference to vino-session in any of the startup scripts anywhere in my system...
Aaaaand, I figured, since vino is a remote-desktop-app-sort-of-thingy, chances are that it needs a valid network-connection... So I go into System/Preferences/Session and set nm-applet to start up earlier than the default 50... But it doesn't stick, damn it... Next time I login, it's back at priority 50 (I've also tried by sudo:ing to no avail)...

I am going to reinstall eventually, this is a test-install on the laptop, but I really want  to figure out whats wrong and how you can customize the startup procedure... 

Cheers
/N

---

