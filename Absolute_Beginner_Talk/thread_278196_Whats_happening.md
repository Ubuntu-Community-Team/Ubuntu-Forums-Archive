---
title: "Whats happening"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Alvar on 2006-10-15
I don't know what is going on. All of a sunnden after i log on ubuntu I don't have the option for the synaptic device thingy(for packages forgot proper name). Then i guessed that i can use the terminal to pull it up, so logically i type in synaptic and boom, it says i'm not running as root. Whats going on i didn't change anything. Plz help me!

---

### Post by capn_hector on 2006-10-15
you need super user privilages, do a sudo <command>  that will fix it.  thats Super User DO.  it gives root privilages for the command but after the command is excuted you go back to normal privigles.

---

### Post by Alvar on 2006-10-15
I did that and this is what it said:
bash: syntax error near unexpected token `newline'

---

### Post by capn_hector on 2006-10-15
whats the command you typed in, mainly switches.

---

### Post by Alvar on 2006-10-15
I typed "sudo <command>" I think i'm being stupid, this is my first time using linux

---

### Post by capn_hector on 2006-10-15
oh, its sudo <command>  the <command> is the insert whatever command here monkier.  type in what ever command your trying to use instead of <command>

---

### Post by Alvar on 2006-10-15
Ok when I type in "sudo synaptic" then my terminal doens't do anything!

---

### Post by capn_hector on 2006-10-15
what are you trying to do??  dont worry about fancy stuff just explain it in plain english

---

### Post by Alvar on 2006-10-15
I'm trying to access my synaptic package manager. Its has dissapered from System-->Admin-->(Now its gone), there are a couple of other things that dissapered. Only printing, device manager... is there. But my system is telling me that i'm not in "root" whatever that means. So i can only run it in read-only from terminal.

---

### Post by Alvar on 2006-10-15
And that i can't change any packages (that sucks)

---

### Post by capn_hector on 2006-10-15
its a gui for apt-get.  do sudo apt-get --update  that will up date the package lists then do a sudo apt-get --list to see a list of all the packaget.  you might only need 1 - though  if 2 gives you an error try 1.

---

### Post by NeoGreen on 2006-10-15
You said synaptic manager disappeared?  Try this and see:  Press Atl + F2, then type gconf-editor /apps/nautilus/preferences.  check to see if synaptic manager is checked, if it isn't check it and save.   I don't know if this will work, but I tried it when all my icons in my desktop disappeared.

---

### Post by capn_hector on 2006-10-15
> **NeoGreen said:**
> You said synaptic manager disappeared?  Try this and see:  Press Atl + F2, then type gconf-editor /apps/nautilus/preferences.  check to see if synaptic manager is checked, if it isn't check it and save.   I don't know if this will work, but I tried it when all my icons in my desktop disappeared.

thats another way, i personaly prefer the command line.  you learn the command line you are much better off as linux is still very command line intensive and most of the command line transfers between every distro.

---

### Post by NeoGreen on 2006-10-15
yeah, I like working from the command line too.  When I switch from one distro to another, it is much easier to manage.  :)

---

### Post by jordanmthomas on 2006-10-16
Alvar, try running 
```
sudo ls
```
from a command prompt.  I think you may have taken yourself out of the admin group, so you can't do any administrative stuff.  If nothing is output, you are not allowed to use sudo.

If you still have the original user you created for the system, great:  log in as them and go to System --> Administration --> Users and Groups
Check on the problematic user to make sure he is able to 'administer the system'

If you don't have the original user, you will have to reboot and in the GRUB menu select recovery mode.
Let it boot up and then hit enter.
```
adduser *your_username* admin
```
```
reboot
```
Your user should now be allowed to run synaptic and do all that good stuff.  Hope this helps!

---

