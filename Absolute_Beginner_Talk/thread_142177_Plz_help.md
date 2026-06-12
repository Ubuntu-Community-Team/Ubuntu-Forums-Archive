---
title: "Plz help"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by SillyAce on 2006-03-09
Ok im running uBuntu right now, and i have one problem, there is only one resolution, 640 x 480... how do i make it bigger?

---

### Post by anirban.sam on 2006-03-09
type from a console; sudo dpkg-reconfigure xserver-xorg and follow the on-screen instructions

---

### Post by SillyAce on 2006-03-09
Console?:confused:  where is that? This is the first time running ubuntu :)

---

### Post by NeghVar on 2006-03-09
Applications>Acessories>Terminal

---

### Post by anirban.sam on 2006-03-09
nevigate in yr menu, application>system tools> terminal, a black & white text box will open, type that thing in that

---

### Post by aysiu on 2006-03-09
If you're in Ubuntu, go to Applications > Accessories > Terminal
If you're in Kubuntu, go to KMenu > System > Konsole

A little window will appear with mostly nothing and this "prompt": ```
sillyace@ubuntu:~$
``` That's where you type the commands.

After you type ```
sudo dpkg-reconfigure xserver-xorg
``` you'll be asked for your password. Enter it. Then, you'll be asked a series of questions. If you know the answers to them, answer them appropriately. If you don't know, just go with the default answer (press **Enter**).

---

### Post by SillyAce on 2006-03-09
ok there is a problem when it asks me for my password when i try to type it dosnt work nothing shows up

---

### Post by bluevoodoo1 on 2006-03-09
[QUOTE=SillyAce]ok there is a problem when it asks me for my password when i try to type it dosnt work nothing shows up[/QUOTE]

It should be working. It's a security measure not to show #### or **** marks. Type your password in there hit enter and see if it works! It should!

---

### Post by SillyAce on 2006-03-09
nope it dosnt

Password:---when i try to type here it dosnt show anything at all not even spaces when i type then it says,
Sorry, try again

---

### Post by anirban.sam on 2006-03-09
type, sudo passwd root, enter and reenter a passwd, then try

---

### Post by Princey on 2006-03-09
When it asks for password, it is asking for the password that you type to log in to your desktop or used when you first installed Ubuntu. When you type, you won't see anything showing. Make sure that you're typing into the window and press enter when done. It should run from there unless you did not set up a password when installing Ubuntu or setting up your user account.

---

### Post by aysiu on 2006-03-09
Make sure you're logged in as the first user you created during the installation.

Then, use that user's password.

The first user you create has "sudo" privileges. With the word *sudo* in front of commands (*sudo dpkg-reconfigure xserver-xorg*, for example), you can temporarily assume administrator (root) privileges.

Other users you create afterwards may not have these privileges.

---

### Post by SillyAce on 2006-03-09
ok once i did all that i finally got it but somhow i f*ed it up and now my rez is 400x300

---

### Post by Xaviar on 2006-03-09
On the top bar click on System then select Preferences and then select Screen Resolution from the submenu.  Minimal use of confusing text strings, correct me if I'm wrong but selecting the resolution you want from there is easy and it allows you to switch between them until you find the one you want.  I guess you're new to programming code (as am I) and are looking for a graphic user interface solution.  I think that's what you're looking for.  Good luck SillyAce.

---

### Post by aysiu on 2006-03-09
[QUOTE=SillyAce]ok once i did all that i finally got it but somhow i f*ed it up and now my rez is 400x300[/QUOTE] What's your monitor model?

---

### Post by SillyAce on 2006-03-10
visual sensa

---

