---
title: "I can't Login to my V5.04 Ubuntu system. :("
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by Rykhaard Damian on 2005-11-21
I was hoping that I'd be able to find a similar situation here at the site, related to my troubles, but I haven't been able to, in my searched through the search function, thus farly. :(
I haven't booted my Ubuntu 5.04 system on my other computer (which originally had XP SP2 only - now, it's dual bootable) for about 10 days.  When I tried to login to it yesterday, I was told that (improperly phrased, from poor memory) "wrong username or password".  :(
I've tried all of the possible names that I login/logon to places with, as well as all of the passwords that I've used within the last couple of years - I.E. each different name, with each of the different passwords.
The only thing that I can think of now - is that I created EITHER a new name, or a new password for the system when I first set it up on the XP machine, but I have no memory of writing it down. :confused:
One possibility - in the lower right corner of the screen, is the name: DAMIAN after 2 /'s.
Could the system be telling me that, THAT is the login name that it's looking for?  (It's the actual acronym for a musical instrument that I'm building, in the same room as that machine.)  If that IS the name - I can try all of the passwords that I remember, from my last 10+ years of logging on / in, over the Net.

Outside of THAT - not being able to log back in - is there any way that I can reset the Administrator password and / or name, without reinstalling Ubuntu from scratch, on the machine?

Thanks grandlee for any help! :) I'm only about 21 days old in Linux (on my Mandrake 8.1 install on this old clanker, and Ubuntu installed, about 10 days ago, on my main non-networked machine.)

Ryk

---

### Post by ecobuntu on 2005-11-21
i have a thought.  log into the safe mode.  It will bring you into a command mode where you will be root.  type the root password (which will be your user password, hopefully you remembered this and forgot the username?).  then type adduser, then <username> passwd (username will be the username you create).
Hopefully this works.  Otherwise you might need to reinstall.  BTW, I think that DAMIAN is your  hostname.

---

### Post by ecobuntu on 2005-11-21
alternatively, log in to safe mode.  
type root password 
type: startx 
this will start GNOME.
then use the GUIs to add a new user, under systems -> administration -> users and groups

---

### Post by codejunkie on 2005-11-21
[quote=Rykhaard Damian]I was hoping that I'd be able to find a similar situation here at the site, related to my troubles, but I haven't been able to, in my searched through the search function, thus farly. :(
I haven't booted my Ubuntu 5.04 system on my other computer (which originally had XP SP2 only - now, it's dual bootable) for about 10 days.  When I tried to login to it yesterday, I was told that (improperly phrased, from poor memory) "wrong username or password".  :(
I've tried all of the possible names that I login/logon to places with, as well as all of the passwords that I've used within the last couple of years - I.E. each different name, with each of the different passwords.
The only thing that I can think of now - is that I created EITHER a new name, or a new password for the system when I first set it up on the XP machine, but I have no memory of writing it down. :confused:
One possibility - in the lower right corner of the screen, is the name: DAMIAN after 2 /'s.
Could the system be telling me that, THAT is the login name that it's looking for?  (It's the actual acronym for a musical instrument that I'm building, in the same room as that machine.)  If that IS the name - I can try all of the passwords that I remember, from my last 10+ years of logging on / in, over the Net.

Outside of THAT - not being able to log back in - is there any way that I can reset the Administrator password and / or name, without reinstalling Ubuntu from scratch, on the machine?

Thanks grandlee for any help! :) I'm only about 21 days old in Linux (on my Mandrake 8.1 install on this old clanker, and Ubuntu installed, about 10 days ago, on my main non-networked machine.)

Ryk[/quote] you could try the recovery option at the grub menu when you boot up your computer if you don't see the grub menu press the esc key when your computer is booting up and you see that 4sec countdown menu  from choose recovery mode and when you get to the command line you can enable the root user with the```
passwd root
```command from here you can also use the ```
add user
```command to add another user account so you can bootup ubuntu, you can then copy over your user settings and files to the new user account.

---

### Post by Rykhaard Damian on 2005-11-21
[quote=ecobuntu]i have a thought. log into the safe mode. It will bring you into a command mode where you will be root. type the root password (which will be your user password, hopefully you remembered this and forgot the username?). then type adduser, then <username> passwd (username will be the username you create).
Hopefully this works.  Otherwise you might need to reinstall.  BTW, I think that DAMIAN is your  hostname.[/quote]

(;) This makes me wish I had both machines side-by-side, rather than on different floors, but. :D LOL )

Into Safe mode:  right then.  I'll go and give that a whack, and try all of my passwords that I'm able to remember, as I have used different passwords for my Roots as well as Usernames.  With success on that end, I'll then follow your adduser advice and create a new one - writing both the username and it's password down, where I wont loose them. :)

I'm hoping that I don't have to reinstall, as I gave the original set of Ubuntu 5.04 back to my boss at work, and my order of 5.10 hasn't come in the mail yet. :(

DAMIAN could be my hostname?  Now THAT's a possibility!  When I'd gotten home with the 5.04 install discs, from work, my main machine was down here on our home network, and I'd installed it down here, switching the locations of both computers the next day.

K.  Off to try it and see how it goes. :)  Thankee grandly for the suggestions! :)
Ryk

---

### Post by Rykhaard Damian on 2005-11-21
Thank you greatlee ecobuntu!  :D  It worked beautifully. :)  DAMIAN WAS the hostname of my the machine.  Rebooting into safe mode (entitled ...... something Recovery - read quickly as I didn't wish the machine to choose the OS before i did) allowed me to setup a new user without troubles, and I notated the login info, so that I wont loose it, again. :)

As well, thank you for helping codejunkie! :)  I'd take a quick gander once the Desktop came up to find a command for listing the users (to move info over from the other original user).  I'll follow your suggestion, for that.

Thank you both. :)  (Wish I could learn faster but ....... it all takes times. (happy sigh) ;) )

Ryk

---

