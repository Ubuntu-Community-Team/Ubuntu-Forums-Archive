---
title: "ndiswrapper"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by darkreaction on 2007-03-12
How do I run the ndiswrapper once i have installed it.

---

### Post by siciliancasanova on 2007-03-12
**ndisgtk** is a GUI for ndiswrapper

---

### Post by darkreaction on 2007-03-12
ok so how do i run [FONT="Arial Black"]ndisgtk[/FONT]

---

### Post by soul814 on 2007-03-12
This link should help you out.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by darkreaction on 2007-03-12
I have been there but i am a noob at this. all i want to do is get on the internet i have a Belkin Wireless G USB Network Adapter but i cant get it to work i installed all the packages it tells me to but i don't know what to do with them?

---

### Post by siciliancasanova on 2007-03-12
[Ndisgtk]("http://www.slax.org/modules.php?category=network&id=682&name=ndisgtk+%28ndiswrapper+GUI%29")

That's one link, I had a good experience with it.  Some people it works for them some people it doesn't.  If you follow the post above me you can do it all from the terminal without the GUI.  Your chances of it working are better that way too.

**EDIT:** You can also find it in the synaptic package manager if you search **ndisgtk**.  Once it is installed it will be **System > Administration > Windows Wireless Driver**s

---

### Post by darkreaction on 2007-03-12
ok so how do i get to my programs once i have installed them?

---

### Post by siciliancasanova on 2007-03-12
Like my post above, ndisgtk is in System > Administration > Windows Wireless Drivers

It will ask you for the .inf file.  You will need to extract your driver on the desktop or somewhere so you can get into it and point ndisgtk to the .inf file.  You can use wine to extract the driver if it's a .exe

---

### Post by Ek0nomik on 2007-03-12
You can also just type "sudo ndisgtk".

---

