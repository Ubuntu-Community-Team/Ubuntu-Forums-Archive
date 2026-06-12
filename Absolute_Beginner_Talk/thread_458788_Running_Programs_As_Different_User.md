---
title: "Running Programs As Different User"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by majorbabu on 2007-05-30
Hi
Fairly newbie-ish user here.
I basically want to run a program under a different (and more privileged) user inside some other user's logged in session.

The program in question is mainly Ktorrent. Any other program would do too, but ktorrent is the main one that I'm interested in running through a different account.

Any ideas on how I can go about doing this?

---

### Post by sankarv on 2007-05-30
you can switch to different user inside another user's logged in session using the 'su' command.


in commandline just give



su <username>


give the password if it asks and then run the program u want from there.


this is the simplest idea i know for general linux....



im not sure as i have nt tried this in ubuntu .check if it works





if u want to become root and run the program just give


sudo <programname>



it will run the program as root.

---

### Post by aysiu on 2007-05-30
Alt-F2 ```
kdesu ktorrent
``` Isn't it a bit dangerous running an internet program as root, though?

---

### Post by majorbabu on 2007-05-30
Thanks for the reply.

Hmmm, that doesn't seem to work out with ktorrent or even gaim for that matter. 

For instance, when I do 'su <username>' and then run something like Gaim, I get the following message in terminal:

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gaim:9321): Gdk-CRITICAL **: gdk_display_get_name: assertion `GDK_IS_DISPLAY (display)' failed
Gaim 2.0.0beta6

** (gaim:9321): WARNING **: cannot open display: unset

```

I think i have to run an X server or something to get it to run. I tried downloaded this app called Xnest that is apparently right for the job, but I'm not sure how to use it.

---

### Post by zvacet on 2007-05-30
Do you have any specific reason to run that type of program as root?

---

### Post by aysiu on 2007-05-30
Oh, the X server isn't running? Are you strictly at the command-line with no graphical user interface? I assumed, since you mentioned KTorrent, that you were using Kubuntu.

---

### Post by majorbabu on 2007-05-30
[QUOTE=zvacet]
Do you have any specific reason to run that type of program as root?[/QUOTE]
No. I just want to run it as any other user. I Wouldn't want to run it as root for sure. Not a safe thing to do even with my limited knowledge as a Linux user :)


[QUOTE=aysiu]Oh, the X server isn't running? Are you strictly at the command-line with no graphical user interface? I assumed, since you mentioned KTorrent, that you were using Kubuntu.[/QUOTE]
I'm on Feisty Fawn.

This is what I get when I type 'su <username>", followed by 'kdesu ktorrent' 

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdesu: cannot connect to X server :0.0

```
This is after installing 'kdebase-bin'

---

### Post by userundefine on 2007-05-30
If you have su'd to another user, you do not need 'kdesu' as preface.  But still, you'll get a different error probably that's somewhat similar.  I think it relates to what groups your user belongs to.  If you can run ktorrent fine as your normal user, you should figure out which group allows you to run it.

---

### Post by majorbabu on 2007-05-30
^hmm. That might be the case, but I'm not sure how to resolve it. For instance, I can't even use 'ls' once i've done the 'su <username>" command

Here's how I have the accounts.
User1 (as part of group "admin")
User2 (as part of group "users")

Once logged in as User1, and going to terminal to enter "su User2" followed by 'ls' reveales
"Permission Denied"
Moreover, trying to run ktorrent reveals a string of errors... or more specifically the following:
```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Qt: Warning: ktorrent: cannot connect to X server :0.0
ERROR: KUniqueApplication: Registering failed!
ERROR: Communication problem with ktorrent, it probably crashed.

```

Also, I'm not sure if this helps but when I first login through the main login screen (with the User1 account) I get this small message that says the following:
> 
User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by other users.

It goes away when I hit 'OK'. I'm not sure if that helps, but here it is anyway. :)

---

