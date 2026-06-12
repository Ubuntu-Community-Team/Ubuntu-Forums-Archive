---
title: "reboot hangs"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by unseenbeing on 2007-01-03
every time i try to reboot it acts like it is

goes through the little shutdown sequence then the screen goes dark but i can still see the ubuntu loading bar thing

the only way i can get it to reset is to hold the power button


this is on my laptop

---

### Post by bapoumba on 2007-01-03
Hi,
are you trying to reboot from the logout menu ?
Is there any error message if you go to a terminal and **sudo shutdown -r now** ?

---

### Post by xyz on 2007-01-03
Also you may want to try this:
[Reboot when everything fails]("http://ubuntuforums.org/showthread.php?t=315404&highlight=reboot")

---

### Post by unseenbeing on 2007-01-03
xyz you're way off from my problem sorry
same with you bapoumba

when i reboot
it will do the shutdown sequence
it will show the little ubuntu logo and status bar and it will do what it does to shut down
but it will not completely shutdown and reboot
it shows a faint picture of the ubuntu logo and status bar but the status bar is empty
there is no text showing an error
it just freezes right before it shutsdown to reboot

---

### Post by oilchangeguy on 2007-01-03
i've got a toshiba laptop that does the same thing. the suggestion i got was to go into the bios and edit the power settings to where it will auto shutdown. i didn't do that, just let it go, cause when i yank out the ubuntu harddrive and drop in the xp pro hardrive re-start works fine. must be a quirk with some computers.

---

### Post by grim4593 on 2007-01-25
Hmm I have this same problem...
I have a MPC Transport T3000 laptop. It does the exactly thing as the op. 

Now, windows XP reboots fine. When I had Dapper it rebooted fine. When I upgraded Dapper to Edgy, reboot started hanging after the bar filled all the way up just like the op. Recently I got annoyed with a few problems and assumed that upgrading Dapper to Edgy messed things up. I reinstalled Edgy from scratch with the install cd's. Reboot does not work still...

---

### Post by Mithrilhall on 2007-01-31
I'm having the same problem.

I have a dual-boot system (XP Pro & Kubuntu 6.10 - Edgy).

Reboot works fine in Windows and hangs in Kubuntu.

I'm going to give this a try tonight when I get home and will post back on the outcome.

[http://www.ubuntuforums.org/showthread.php?t=346182&highlight=reboot+hangs](http://www.ubuntuforums.org/showthread.php?t=346182&highlight=reboot+hangs)

---

### Post by Mithrilhall on 2007-02-05
My last post in this thread is what did it for me.

[http://www.ubuntuforums.org/showthread.php?t=349993](http://www.ubuntuforums.org/showthread.php?t=349993)

---

### Post by grim4593 on 2007-02-07
Hmm, I don't think your solution would help me. Everything worked fine in dapper, and it broke after installing edgy (even after a complete reinstall). My hardware configuration has not changed. I tried turning off powernowd like the posts above yours too: however that just turned off my ability to control my processor speed and it still hung on reboot.

---

### Post by kallek on 2007-02-10
My situation is similar. Shutdown works, but restart hangs. Restart worked fine with Breezy, Dapper, and previous to that, with gentoo, debian, & suse, but it started hanging after upgrade to Edgy. I too, both upgraded and reinstalled, but with the same result. I got a sony vaio, pcg-grt815e laptop.

---

### Post by kallek on 2007-04-21
I upgraded to Feisty Fawn, and the problem is no more.

---

