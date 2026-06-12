---
title: "Upgrading Firefox/Thunderbird + Other general questions."
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by Just4 on 2006-04-24
I have Xubuntu installed, (Installed Xfce after doing a minimal install of Ubuntu), I'm wondering how to upgrade the version of Firefox to 1.5.x and Thunderbird to 1.5.x? As the repositories only have the older versions available. Also when using Synaptic I can find 7-zip and install it but it appears as if it hasn't been installed after that (I've browsed around, couldn't find it anywhere on the HD) anyone know to to install 7-zip? I'm also looking for a few other basic utilities for Linux, like an Mp3 player and CD burning apps, anyone suggestions on some good ones would be appreciated. Thanks beforehand for any help.

---

### Post by aysiu on 2006-04-24
[This thread should help you](http://www.ubuntuforums.org/showthread.php?t=151179). Note, the Thunderbird script was revised for 1.5.0.2 (the revision is at the end of the thread).

---

### Post by Just4 on 2006-04-25
Odd, Thunderbird doesn't work at all for some reason, not even after installing the old version, no run commands for it work, nothing, any help on this?

---

### Post by dsmithnc on 2006-04-25
I just tried the new script to install the new Thunderbird with the following result:

root@ubuntu:~/Desktop# mv installnewthunderbird.sh.txt installnewthunderbird.sh chmod +x installnewthunderbird.sh ./installnewthunderbird.sh
mv: when moving multiple files, last argument must be a directory
Try `mv --help' for more information

I know I'm missing something.

Dick

---

### Post by aysiu on 2006-04-25
[QUOTE=dsmithnc]```

root@ubuntu:~/Desktop# mv installnewthunderbird.sh.txt installnewthunderbird.sh chmod +x installnewthunderbird.sh ./installnewthunderbird.sh
mv: when moving multiple files, last argument must be a directory
Try `mv --help' for more information
```

I know I'm missing something.[/QUOTE] Those commands all need to be on separate lines. ```
mv installnewthunderbird.sh.txt installnewthunderbird.sh
``` Then press the Enter key. ```
chmod +x installnewthunderbird.sh
``` Then press the Enter key. ```
./installnewthunderbird.sh
``` Press the Enter key. When prompted for a password, enter your password--you will not get any visual feedback that it's accepting your password. Your password is still being accepted, nonetheless. Press Enter again, after entering your password.

---

### Post by dsmithnc on 2006-04-25
Oh, well.  That's a Homer Simpson moment if there ever was.  ](*,) 

Thanks so much for that explanation.  Worked like a charm!

Dick

---

### Post by aysiu on 2006-04-25
The important thing is that it worked.
We're all allowed Homer moments... especially in Absolute Beginner section.

---

### Post by Just4 on 2006-04-25
Any idea why I can't run thunderbird at all? I uninstalled and reinstalled a few times, nothing, I can't run from command line ( "mozilla-thunderbird" ) nor any of the menus, when I run it from command line I get no error, it just doesn't load, same with using any of the menus, whats the problem?

---

### Post by aysiu on 2006-04-25
[QUOTE=Just4]Any idea why I can't run thunderbird at all? I uninstalled and reinstalled a few times, nothing, I can't run from command line ( "mozilla-thunderbird" ) nor any of the menus, when I run it from command line I get no error, it just doesn't load, same with using any of the menus, whats the problem?[/QUOTE] Are you talking about installing mozilla-thunderbird 1.0.7 through apt-get or installing Thunderbird 1.5.0.2 from Mozilla?

---

### Post by Just4 on 2006-04-25
I installed 1.5.x using the script, but it didn't work. I removed the directories and tried to install via synaptic 1.0.7 figuring maybe it'd work if I had 1.0.7 installed first, nothing, I can't figure out whats wrong, I guess I may have f'd something up. heh. ](*,)

---

### Post by aysiu on 2006-04-25
Can you go to a terminal and type ```
mozilla-thunderbird
``` and post the output here?

---

### Post by Just4 on 2006-04-25
No output when I do it. :confused:

---

### Post by aysiu on 2006-04-25
[QUOTE=Just4]No output when I do it. :confused:[/QUOTE] No output? So this is what happens? ```
just4@ubuntu:~$mozilla-thunderbird
just4@ubuntu:~$
```

---

### Post by Just4 on 2006-04-25
Yes. No output at all.

---

### Post by aysiu on 2006-04-25
[QUOTE=Just4]Yes. No output at all.[/QUOTE] That's weird. I'm not sure what that means. See, if Thunderbird weren't installed, you'd get something like ```
bash: command not found
``` and if Thunderbird were working properly, it would just start up.

I'm not sure what that jump to the next line means.

---

### Post by Just4 on 2006-04-25
Yeah, I don't understand it either. But it does it with both 1.0.7 and 1.5 I fuess maybe I'll find a different email client then for now until I can figure out whats wrong.

---

### Post by aysiu on 2006-04-25
If no one responds to this thread after 24 hours, bump it. Someone on this forum has to know what's going on.

---

### Post by Just4 on 2006-04-25
One thing I've noticed from reading Mozilla's site, there is no ~/.thunderbird folder with profile info? If that means anything one way or the other.

---

### Post by aysiu on 2006-04-25
[QUOTE=Just4]One thing I've noticed from reading Mozilla's site, there is no ~/.thunderbird folder with profile info? If that means anything one way or the other.[/QUOTE] .thunderbird is a hidden folder.

If you're using Gnome, press Control-H in your home directory, and you'll see all the . folders. If you're in KDE, press Alt-V, then H to see the hidden directories.

Ubuntu's Thunderbird puts its profile in ~/.mozilla-thunderbird. Mozilla's Thunderbird puts its profile in ~/.thunderbird.

~/ is just another way of saying /home/just4

---

### Post by Just4 on 2006-04-25
Yeah, I know its hidden and I am using Xfce + Nautilus but I still do not see it even when I have it set to show hidden files?

---

### Post by aysiu on 2006-04-25
The folder doesn't get created until the first time you launch Thunderbird.

---

### Post by Just4 on 2006-04-26
Ah, ok - that makes sense. Sorry for all the questions. Still cannot get Thunderbird to run.

---

### Post by Just4 on 2006-04-26
Bump - Anyone know of any fix/and or the cause of this?

---

### Post by Caligula on 2006-04-26
The same happened to me with frostwire...
I didn't solve it, but i'm not using java now anyway...

---

### Post by sumgai on 2006-04-27
I am having the same problem with thunderbird.  No matter what I've tried (all the same as mentioned above), nothing happens when I try to run it from a terminal or from the system menu.  No errors, no program, nothing!

I did finally get my firefox running properly though... I found clues on the firefox message board:

  -- Firefox directories need write access for software update to work, so I did this
  -- Go to about:config and set xpinstall.enabled to true

That did it for me.  Extensions and plug-ins are working just fine along with everything else so far.

Not too bad for a noob.  Now if I can just get thunderbird working!

---

