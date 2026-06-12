---
title: "Custom icons for specific filetypes"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-11
I just installed the linux version of my favourite text editor, it makes me feel at home.

It has it's own icon, which I managed to apply to a desktop launcher okay.

Now, is there a way I could make all files of type 'plain text document' use that icon too, system wide?

Or am I trying too hard to turn linux into windows here :???: :oops:

---

### Post by Inxsible on 2007-06-11
You can change it. Right click any file that you want to change the type of. Select Properties. Click on Open With (or just Open) tab. Select your favorite app to open it with. I think it will change the icon automatically. If not, you can then browse into the directory of your app and select your icon there.
 
Note: I think it will work. I havent tried it, as I am on an XP right now.

---

### Post by ecs_pf5 on 2007-06-11
Yes it works - but it doesn't change all files. Only that one file. All the other files across the system of the same filetype seem to keep their original icons. I must admit, I *am* trying to bend it to act like Windows here, when I guess really I should be more concerned with just getting used to the way it works 'natively'!

Perhaps I have to find a way to add the program I just installed, to the 'open with' dialog as a 'default program' rather than a 'custom command'?

(The editor I installed is called 'edit pad lite' and I installed it into /home/user/editpad where it likes to run from a shell script that the installer put there. The icon appears to be the file 'editpad.xpm' in that directory)

---

### Post by Inxsible on 2007-06-11
Try restarting your X, to see if the changes take effect. I am just trying out on a limb here. Press Ctrl+Alt+BackSpace.

---

### Post by ecs_pf5 on 2007-06-11
No joy.. I think it's trying to hang on to using gedit as the default for opening 'plain text documents'.

---

### Post by Inxsible on 2007-06-11
> **ecs_pf5 said:**
> No joy.. I think it's trying to hang on to using gedit as the default for opening 'plain text documents'.
 
I know there is a way to do it. I just am not on a Ubuntu machine. Maybe I will give it a shot later tonight.

---

### Post by ecs_pf5 on 2007-06-11
Thanks - if I happen to stumble across it I'll post back straightaway.. I had a look in the menus to see if there was some kind of 'default programs' thing; there is something called 'Preferred Applications' but it only seems to cover a very few major programs like Internet browser, email and terminal.




[edit]

ehup, this looks interesting:

[http://www.cs.cornell.edu/~djm/ubuntu/#change-default-app](http://www.cs.cornell.edu/~djm/ubuntu/#change-default-app)

Hmm. Done that; every text/plain document now opens with edit pad lite by default but the icons are still the same.

again this looks informative:

[http://ubuntuforums.org/showthread.php?t=271448](http://ubuntuforums.org/showthread.php?t=271448)

I think in the Theme I currently have set,

 /usr/share/icons/gnome/scalable/mimetypes/text-x-preview.icon

is possibly the one (or one of the ones) I need to change.. can't access it easily due permissions though. Short of logging in as Root. Sudo doesn't seem to be helping me much right now & gimp won't open it.

[edit] okay, I rushed in where angels fear and tried sudo su, which let me overwrite /usr/share/icons/gnome/scalable/mimetypes/text-x-preview.icon with a renamed copy of the program's icon. No joy, all text/plain filetype icons just the same as they were before, right across the filesystem :(

---

### Post by ecs_pf5 on 2007-06-12
Afraid I'm floundering with this, beginning to feel I'm starting to wander around in dangerous parts of the OS, blindfold with an axe :lol:

Seem to have reached the limits of my googling abilities on the problem.

---

### Post by Inxsible on 2007-06-12
Wow, the first link you posted is extensive. Be good to bookmark it for meself !!
 
I couldn't get the icon thing working either :(

---

