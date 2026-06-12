---
title: "A few noob questions..."
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by Aurdal on 2006-06-05
1. How important is it to have a Firewall? (I don't like having to type my password twice when I log in. :))

2. How do I change the splashscreen, and background color which comes when you log in?

3. Whenever I do something else in addition to playing music, the sound flickers, is there a way to get around this? (the music is on a FAT drive, is it better to place it on a EXT3 maybe?)


Thanks.
-Aurdal

---

### Post by bluenova on 2006-06-05
[QUOTE=Aurdal]1. How important is it to have a Firewall? (I don't like having to type my password twice when I log in. :))[/quote]

Very, it's your only defence against intruders, you wouldn't leave your front door open when you go out would you? A hardware firewall is best, but other than that use firestarter as a GUI frontend to iptables. You would only need to type in the password if you needed to adminster the firewall, it will be running (in the background) when you boot your computer.


> 2. How do I change the splashscreen, and background color which comes when you log in?

Take a look in Administration > Logon manager


> 3. Whenever I do something else in addition to playing music, the sound flickers, is there a way to get around this? (the music is on a FAT drive, is it better to place it on a EXT3 maybe?)


Thanks.
-Aurdal

I'm not sure if FAT would be a problem, I wouldn't have thought so, try playing a file from your ext3 partition and see what happens.

---

### Post by frodon on 2006-06-05
I would give you a different answer about the need of a firewall. A firewall with ubuntu is really not needed, an up to date ubuntu box is secure enough.
The only interest of a firewall (if you don't run any services) is the peace of mind, because if a good hacker want to attack you he will succeed even with a firewall but such persons don't target simple users, therefore no need of a firewall except for peace of mind.
By the way, i run a software firewall (i like peace of mind ;) )

---

### Post by Aurdal on 2006-06-05
1. Whenever I boot it promts me for my password.

2. Only thing in there is Login Screen Setup, and if it's in there somewhere I can't find it.

3I think I might have fixed this problem by installing a sound fix for gnome with automatix.

---

### Post by seshomaru samma on 2006-06-05
[QUOTE=Aurdal]1. Whenever I boot it promts me for my password.

2. Only thing in there is Login Screen Setup, and if it's in there somewhere I can't find it.

3I think I might have fixed this problem by installing a sound fix for gnome with automatix.[/QUOTE]

this might answer your questions:
[http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide](http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide)
part 17.7 will tell you how to log into GNOME without a password
part 25.29 will tell you how to manipulate the GRUB splash screen

---

### Post by Aurdal on 2006-06-05
Thanks, but neither of them were what I asked for. I want to change the Gnome Splash screen, and I don't want to log in to gnome without password, but I wan't my firewall to not promt me for my password when I have logged in.

---

### Post by u.b.u.n.t.u on 2006-06-05
Hi Aurdal,

seshomaru samma gave you the answer to your question "firewall to not promt me for my password when I have logged in."

The answer is here:

[http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_have_Firestarter_start_without_the_root_password](http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_have_Firestarter_start_without_the_root_password)

Scroll up and down a little to get a fuller idea.

---

### Post by bluenova on 2006-06-05
Double post

---

### Post by bluenova on 2006-06-05
Firestarter should only ask for a password when loading the GUI app, which as I said before you don't need to run at startup it will run in the background without it, so check your startup apps (sessions > Startup) and remove firestarter from there if it's listed.

For the gnome splash screen install 'gnome-splashscreen-manager'

---

