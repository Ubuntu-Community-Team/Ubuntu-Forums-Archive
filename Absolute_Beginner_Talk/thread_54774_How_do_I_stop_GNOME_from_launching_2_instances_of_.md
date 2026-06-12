---
title: "How do I stop GNOME from launching 2 instances of some applications?"
date: 2005-08-06
forum: Absolute Beginner Talk
---

### Post by amrust on 2005-08-06
I have a problem I stumbled on trying to resolve a firestarter issue.

Most programs appear to launch just fine. But some are exhibiting weird behavior. For example, when I start certain applications, like:

[B]Firestarter
Users and Groups
Time and Date
Login Screen Setup[/B]

For some reason, I get two copies of these application running. I know they worked normally the other day, and only launched one app when i click on them in the application menus and launchers. As of today, they are launching 2 copes when I click them. What happened?

And when I do add them to my launcher panel, they try to launch using 'gksudo' instead of 'sudo'.  :???: 

The only thing I have done out of the ordinary lately, is when I logged out the other day, I selected "save current setup". Could that have done something to my default session? What would be causing this problem? Can anyone help keep me from pulling my hair out? This is very frustrating, I think it's a simple fix, if I could just figure out what to do. I am a new Linux user, so please be gentle. :)

---

### Post by amohanty on 2005-08-06
save current session also keeps track of which apps you have running and launches them or at least tries to when you log back in. I think whats happening is that the launchers are locked and loaded and fire up the apps once you provide the su password.

AM

---

### Post by amrust on 2005-08-06
You are correct in that stopping firestarter, and then saving current session will correct the problem I had with firestarter.

But I still don't understand why many of these apps appear to be launching by using the gksudo command. Why are some things launching twice now, when I pick them, instead of just once? It's like anything that I'd launch that requires a password, launches 2 copies when started. If I wait long enough, the "2nd copy" eventually dissapears, but why is it doing this now? And how do I correct it? I know there has to be a way, there's a way to fix ANYTHING in Linux, it seems. :?

---

### Post by amrust on 2005-08-06
I'm thinking my problem may have something to do with my account privleges, but I don't know for sure. What "group" should my normal-everyday login account be in? The group name that matches it's name, or admin, or adm, or user, or which?

---

### Post by amohanty on 2005-08-06
Theres a possibility that these programs do not launch fully until you authenticate as root. Your regular everyday account has a profile called 'Desktop' and belongs to a group with the same as your username.

AM

---

### Post by amrust on 2005-08-06
Yes, I checked in Users and Groups, and my everyday account is in a group name same as the account name. When I start **Time and Date**, or **Users and Groups**, or **Login Screen Setup** and let them run for long enough, the duplicate version in my bottom bar seems to go away on its own. I don't recall it behaving like the until just recently, but maybe it always did. is this normal when you launch these programs as a regular user? Do any others see this behavior?

---

### Post by amohanty on 2005-08-06
Dont save your session when you exit. Delete .dmrc in your home, reboot. If you would like some apps to startup when you login, you can try to put them in .login or .profile. I have not tested that so I cannot guarantee but I will and let you know of the result.

AM

---

### Post by amrust on 2005-08-06
OK I deleted .dmrc, and it built a new clean one. The firewall seems to be working OK now, its not giving me the error dialog, and its up in the panel. Only thing that is still strange is the 2 copies of those programs I listed being launched when I chose them from menu. But one goes away if I wait long enough.

If I change the launcher for them to sudo instead of gksudo, they seem to work normally. Why do they now have gksudo on them instead of sudo? Why dpoes everything that should be sudo start with gksudo in the menus now?

---

### Post by amohanty on 2005-08-06
Why do you use gksudo rather than sudo?

AM

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=amohanty]Why do you use gksudo rather than sudo?

AM[/QUOTE]

You must use gksudo for all graphical apps. If you don't it might mess up your ICEauthority file and you will not be able to log back into Gnome on your next boot.

The only exception (for some weird reason) is gedit.

---

### Post by amrust on 2005-08-06
[QUOTE=amohanty]Why do you use gksudo rather than sudo?[/QUOTE]
I didnt choose anything, the menus have gksudo launching some of those apps, themselves. Ubuntu came that way, I guess.

[QUOTE=poofyhairguy]You must use gksudo for all graphical apps.[/QUOTE]
So when I see them look like 2 are started at first, then one goes away after a few seconds, this is normal? It seems to be the way Ubuntu wants it, i know I didnt accidentally change them to gksudo, i dont even know how to modify the application menu launchers. LOL

---

### Post by amohanty on 2005-08-08
> You must use gksudo for all graphical apps. If you don't it might mess up your ICEauthority file and you will not be able to log back into Gnome on your next boot. 

Is this only for starting apps at login?

Thanks.

AM

---

### Post by TravisNewman on 2005-08-08
if you have a launcher that uses sudo, you'll never see the password dialog. This is why gksudo is used. You must use gksudo for any apps you're launching from a launcher, otherwise there's no way to authenticate.

You didn't accidentaly change them to gksudo, they were always like that.

---

### Post by amrust on 2005-08-08
[QUOTE=panickedthumb]if you have a launcher that uses sudo, you'll never see the password dialog. This is why gksudo is used. You must use gksudo for any apps you're launching from a launcher, otherwise there's no way to authenticate.[/QUOTE]

Understood. But the ones that launch with gksudo in the launcher only ask me for my password for the 1st one I launch. Subsequent launches after the 1st gksudo launcher program, pull up one window for the program launched, but briefly there are 2 applications in my lower status bar where running windows reside (don't know the technical name). Is this normal authentication taking place, while there are 2 of them briefly, then one goes away after it authenticates itself?

---

### Post by garba on 2005-11-25
i'm having the same problem i found out only those apps with come with the "StartupNotify" set to true in their .desktop file are affected by this odd behaviour, for example synaptic works just fine and won't bring up another instance of itself upon startup, but "time and date" will... check their .desktop and see for yourself this might be the problem

---

