---
title: "Changed HOME directory, bad idea.."
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by yawnster on 2006-05-28
Howdy guys,

Im dual booting Windows XP and Ubuntu 5.10, for some unknown reason I got bored and decided to mess about with the users page..

I wanted total control of the root so I decided to change my home directory to /  .. Not the cleverest idea..

[IMG]http://www.yawnster.com/images/unbuntuproblem.JPG[/IMG]

so my home directory variable I am guessing is now / instead of /home/alex (alex is my username)

I am now receiving the error..

```
Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions.
```

After looking up this error on here I ran the commands from the failsafe terminal, failsafe gnome is also a dead end...

```
sudo chmod 644 .dmrc
sudo chown alex.alex .dmrc
sudo chmod 755 /home/alex
sudo chown alex.alex /home/alex
```

And yes I do have those permissions :p but I am still receiving the same error..

When I open up gedit and browse to my home directory using the file browser I only see 1 file.. dbootstrap.settings (I think thats the exact name, I am currently on my WinXP side so I cannot really check without rebooting).. From what I have read with the built in documentation, bootstrapping is a part of the hosts file..

So [after reading yet more]("http://ubuntuforums.org/showpost.php?p=748387&postcount=13") I have come to the conclusion that my hosts file is also correct, as the what I have got is exactly the same as the one in the other post but with my hostname there..

Anyway, any help would be greatly appreciated... Alex

PS.. The XSession.errors file output is..

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "alex"
/etc/gdm/XSession: Beginning session setup...

(gnome-session: 10065): libgnomevfs-WARNING ** Unable to create ~/.gnome2 directory: Permission Denied
Could not create per-user gnome configuration directory `/.gnome2/': Permission denied
```

---

### Post by hw-tph on 2006-05-28
Change home to / ??? For what reason? This is the sort of thing you can use qemu for - mess about without having to clean up the mess. :)

As a regular user you cannot create files and/or directories in /, so you're not going to have much success.


Håkan

---

### Post by yawnster on 2006-05-28
Hmm, well by my flawed logic, I could write files to my home directory, and thus if I changed my home directory to / I could write to anywhere on the file system..

Seems rather logical to me, as this is how Windows works, but this isnt Windows :P

Do you have any tips on how to reverse this change? Do you know where the variable is actually kept, thus allowing me to reverse the change?

Thanks again.. Alex

---

### Post by Gustav on 2006-05-28
sudo usermod -d /home/alex alex

I think that should do it.

---

### Post by yawnster on 2006-05-28
[QUOTE=Gustav]sudo usermod -d /home/alex alex

I think that should do it.[/QUOTE]

Man your a life saver, I had to clear up a few more permissions errors, but this did the job..

Again thanks for the great support guys.. Now I just have to work out how to get my wireless card to work :P Ndiswrapper here I come..

Alex

---

### Post by eentonig on 2006-05-28
Seems like your ready to totally screw up your machine.

There's a reason why you don't have access to all system files as a regular user. Maybe in windows the averga Joe can go delete system dll's. Linux is designed to not allow this. (Unless you screw around of course.)

---

### Post by get_jiggy on 2006-08-26
WOW. \\:D/  I tried to change my home directory to /home instead of /home/username because I'm the only user, and this thread saved me from throwing my laptop through the wall! Thanks guys!

Moderator: can you add '$HOME/.dmrc' to the thread title?  I think I would've found it faster if part of the error message was in there.

---

