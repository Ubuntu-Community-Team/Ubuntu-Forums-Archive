---
title: "Startup Programs:  How do I launch an app that needs Root privileges?"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2005-10-31
I'm trying to start Firestarted on startup but it fails because it needs to be started by root/sudo.   "sudo firestarter" doesn't work when entered into Startup Programs and there don't seem to be any advanced settings for the entries there via the GUI.

Thanks in advance,

-Doc

---

### Post by majed on 2005-10-31
Here's how you do it:

1- Edit the file /etc/sudoers  as root 
    (ps: this will allow sudo for firestarter without password)

      - Open a Terminal
      - Run this command:  
             gksudo gedit /etc/sudoers
      - Paste this line at the end: 
             <username> ALL= NOPASSWD: /usr/sbin/firestarter
      - Replace <username> with your username
      - Save the file and close the editor

2- Add the following line to your Gnome session startup commands or put it in a script in Autostart directory (not sure if Gnome uses this, but XFCE does):
            sudo /usr/sbin/firestarter --start-hidden

3- Da da!

---

### Post by stuart-newtoubuntu on 2005-12-12
Wow 

That really helped me, but has led to a new problem. Now everytime I enter Xfce I am greated with a dialogue box informing me that I have "Insufficent privilages to run/use firestarter" (I forget the exact wording of the message)  even though firestarter is sat there in the system tray and works when clicked on.

Any idea how to get rid of this message?

---

### Post by majed on 2005-12-13
hmmm..

make sure firestarter doesn't require password by following the directions above (but i assume u did.. so it must be something else..).. ;)

try finding out exactly whats the message .. will ya? :)

im using XFCE and doing exactly what i posted before and its woroking fine..

---

### Post by tay on 2005-12-13
thas strange,, by default you should'nt be able to run firestarter from the termianl unless you root.. but you should be able to start it from the gnome-panel without password prompting.

anyways, from the terminal,, just
$sudo -s
$sudo firestarter

if that dont' work
$sudo passwd root
and change your password

---

### Post by kaamos on 2005-12-13
Why do you need the firestarter gui at startup?

The firestarter daemon starts at boot (this can be changed from firestarter preferences), and there is no need to run the gui unless you need to change setting or look at logs.

---

### Post by stuart-newtoubuntu on 2005-12-15
I didn't, I got confused and thought that firestarter was the firewall.

I have looked into things and found out about iptables.

But thanks for the help. It's taught me how to add things to start up in xfce.

---

### Post by Slade Winstone on 2005-12-17
Just a quick comment but I think that you should be using the command **visudo **to edit the sudoers file.  

Apparently, it takes care of nice things like syntax checking and locking so that you can't screw the sudoers file up ;)

Slade.

---

