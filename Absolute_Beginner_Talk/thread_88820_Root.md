---
title: "Root"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by DivineComedy on 2005-11-11
Once again ubuntu pisses me off, but this time im coming to ask you people rather then doing it myself.

Alright, I done set up my root password and everything however when I try to log into root I get "Administrater is not allowed to log in from here" and this is pissing me off. I've read other forums and they all give the same answer, root commands are only accessable through terminal. This is NOT acceptable with me.

I'm still pretty sloppy with terminal and I don't know how to delete files and such from there and I have a few files that are under root permission that I want to clear for hd space. Why the **** can't I access my own computer as root? Is there anyway to set it to allow me in? If not could someone please just tell me how to delete from the terminal before I go mad?!

---

### Post by michael_salcher on 2005-11-11
just use "gnome-terminal" to get a terminal up and then if you have a root password, you should be able to log in as root by typing "su". if that does not work, you can get a root shell by typing "sudo -s" and and then entering your user password.
"sudo -s" also works on the 6 text terminals available via "ctrl+alt+f1" to "ctr+alt+f6" if you first log on as a normal user.

---

### Post by cedjo on 2005-11-11
I think it will be useful for you to consider why it's done like this, it's because some new users just don't know that they can destroy some system files. If you know this you'll certainly be able to log in as a normal user, open a terminal window, and then delete the files....
PS: if the files have root permissions, it's normally to avoid them to be deleted, and it has been installed by the system ('cause you haven't done it as a root user did you?)

---

### Post by codejunkie on 2005-11-11
[quote=DivineComedy]Once again ubuntu pisses me off, but this time im coming to ask you people rather then doing it myself.

Alright, I done set up my root password and everything however when I try to log into root I get "Administrater is not allowed to log in from here" and this is pissing me off. I've read other forums and they all give the same answer, root commands are only accessable through terminal. This is NOT acceptable with me.

I'm still pretty sloppy with terminal and I don't know how to delete files and such from there and I have a few files that are under root permission that I want to clear for hd space. Why the **** can't I access my own computer as root? Is there anyway to set it to allow me in? If not could someone please just tell me how to delete from the terminal before I go mad?![/quote] if you just wan't a gui to copy, paste, edit, delete files etc in root mode you can add a launcher on your desktop name it something like root file browser or what ever and for the command use ```
gksudo nautilus
``` it will ask for a password, it will be the password of the first user you created when installing ubuntu. to gain full root access first enable the root account with ```
sudo passwd root
``` click on System/Administration/Login Screen Setup then click security tab and check the box that says allow root to login with gdm, now you will be able to login as root. hope this is what you were looking for.

---

### Post by vruum on 2005-11-11
I think some things (even some administrative) are easier to do graphically, like mass handling of files, I have problems remembering the chmodding terminology, and feel safer actually doing it graphically. But root login through gdm is VERY unsafe, you don't wanna run firefox gaim or openoffice as root, (or, if you do, you should be able to  mess with gdm configurations).
Any way, open up a terminal and
```

sudo nautilus

```
should give you a root filebrowser.
[edit] I type slow[/edit]

---

### Post by apjone on 2005-11-11
[QUOTE=DivineComedy]Once again ubuntu pisses me off, but this time im coming to ask you people rather then doing it myself.

Alright, I done set up my root password and everything however when I try to log into root I get "Administrater is not allowed to log in from here" and this is pissing me off. I've read other forums and they all give the same answer, root commands are only accessable through terminal. This is NOT acceptable with me.

I'm still pretty sloppy with terminal and I don't know how to delete files and such from there and I have a few files that are under root permission that I want to clear for hd space. Why the **** can't I access my own computer as root? Is there anyway to set it to allow me in? If not could someone please just tell me how to delete from the terminal before I go mad?![/QUOTE]
I started linux after 8yrs of windows !!!! Get to knowing the command line, it is your friend!!!!

---

### Post by LinuxWiz83 on 2005-11-15
I started linux after 3 years on windows and been using both in tell the last 3 or 4 months. Not just that you can run as a user and still have all the permissions as root does with easy to use scripts made for nautilus. If you want to run nautilus as root then use this script [http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Misc/root-nautilus-here](http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Misc/root-nautilus-here)
and to add it just run:
gedit ~/.gnome2/nautilus-scripts/root-nautilus-here (paste what is in the link above in this blank file)
chmod +x ~/.gnome2/nautilus-scripts/root-nautilus-here

Here is thread on an how-to for root access by right click on a file with Nautilus/Gedit: [http://ubuntuforums.org/showthread.php?t=75610](http://ubuntuforums.org/showthread.php?t=75610)

---

### Post by ssam on 2005-11-15
if you really want to log in as root then you have to change an option in the login control panel. GDMs default is to not allow root logins.

what is it that you want to delete? if it is a program you dont use then you can just uninstall it in synaptic.

please be very care when you are logged in as root. some of us stay awake at night worrying about people who log in as root.

i think it would be good if nautilus had an understanding of sudo. for example if you tried to do something you did not have permission to do it would pop up a password box (and a big warning).

---

