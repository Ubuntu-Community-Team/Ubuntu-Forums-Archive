---
title: "Superkaramba - problem"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Oki on 2007-01-24
Hi

I just installed "Superkaramba" with Adept on Kubuntu(KDE is installed on Ubuntu). First time running I started the program from Utilities > Superkaramba and thereafter I installed some themes. After restarting the system these themes are gone. I can open Superkaramba again, but the themes I installed are gone. If I look in the "New Stuff..." I can see they are installed(they have a green check on them) - but I can't get them to run. Installing other themes works, and they show up in the Superkaramaba dialog, with an Uninstall button(witch the missing themes dont). Look at the screens to better understand. 

I have uninstalled Superkaramba with Adept, and installed it again - but with no help.

Any tips ?

---

### Post by ComplexNumber on 2007-01-24
> **Oki said:**
> Hi

I just installed "Superkaramba" with Adept on Kubuntu(KDE is installed on Ubuntu). First time running I started the program from Utilities > Superkaramba and thereafter I installed some themes. After restarting the system these themes are gone. I can open Superkaramba again, but the themes I installed are gone. If I look in the "New Stuff..." I can see they are installed(they have a green check on them) - but I can't get them to run. Installing other themes works, and they show up in the Superkaramaba dialog, with an Uninstall button(witch the missing themes dont). Look at the screens to better understand. 

I have uninstalled Superkaramba with Adept, and installed it again - but with no help.

Any tips ?
i guess its like that each time you log in, right? i suspect that you are starting each session(ie each time you login is a new ssession) with a fresh session, so its not remembering the previous superkarambas that you started running. go to the kde control centre (for some reason, this is not in the menu. instead, go to the terminal and type in 'kcontrol') and go to 'session management'(or something like that. type in "session" into the search box to find it) and change it so that it remembers the previous session each time you log in.

---

### Post by Oki on 2007-01-24
"i guess its like that each time you log in, right?"
Yes. I have not used the session management yet, and take a look at the screen print below. Isn't that strange - like it should be?

---

### Post by ComplexNumber on 2007-01-24
i assume that it was like that already. what you could try doing is clicking on the skz file to run a superkaramba rather than installing it via the dialogue in your first screenshot. then logout and log back in again to see if it 'sticks.
i remember that i had the exact same problem, but i seem to remember that it was behaving funny whever i tried to install them via the superkaramba dialogue, but it would be fine after i installed by double clicking on a skz file.

---

### Post by Oki on 2007-01-25
You mean download a skz file and double click it? I tried but nothing happend.

---

### Post by ComplexNumber on 2007-01-25
> **Oki said:**
> You mean download a skz file and double click it? I tried but nothing happend.
no. the skz file is merely a superkaramba theme. try another one. if none work, then maybe you have a missing python dependency.

---

### Post by healthpellets on 2007-01-25
Sorry, don't mean to be rude here, but i also have a Superkaramba question....

When i d/l a system recourse tool, it never registers my network connections, cpu heat, or memory used.  Tips?

And I can't get liquid weather to work either...like, it doesn't work at all!

---

### Post by ComplexNumber on 2007-01-25
>  When i d/l a system recourse tool, it never registers my network connections, cpu heat, or memory used.  Tips?
install lm_sensors

---

### Post by Crakie on 2007-01-25
> **Oki said:**
> I have uninstalled Superkaramba with Adept, and installed it again - but with no help. Any tips ?

I had a similiar experience. The problem is that uninstalling does not completely remove the settings files. I even uninstalled using the --purge option and, after reinstalling, widgets would still show up as being installed whereas in fact they were not. Without a reinstall option, that really sucks!

Here is how I fixed this: after uninstalling, I ran a filesearch on the whole drive for superkaram* or karam* (can't remember which searchphrase exactly). It gave a few hits and I deleted them all. After installing Superkaramba again, I could install whatever I wanted. Note: you need to have root priviliges to search and delete those files.

---

### Post by ComplexNumber on 2007-01-26
> Here is how I fixed this: after uninstalling, I ran a filesearch on the whole drive for superkaram* or karam* (can't remember which searchphrase exactly).its not necessary to do a search of your whole drive. the settings are all in the .superkaramba and .kde directories in your home directory. the setting in superkaramba file in your .kde directory is the one that needs deleting (from what i remember).

---

### Post by Oki on 2007-01-26
Cant find them in the Home folder at all?

---

### Post by Oki on 2007-01-26
I did remove superkaramba (sudo aptitude remove superkaramba), then I searched for superkaramba and deleted the files I found. Then I installed superkaraba again but the themes/widget was still marked as installed? Strange...

---

### Post by Crakie on 2007-01-26
Deleting only the stuff in /home won't do. Well, I didn't do it for me, that is. I had to run Konqueror (probably Nautilus for Gnome) as root and do a thorough search of the ENTIRE drive. I remember having to try quite a bit of search strings before a number (about 10) files started showing up, but it was something like superka* or karam*. Sorry, cannot remember which one exactly.

---

### Post by fearlex on 2007-02-06
I have exactly the same problem and i don't know what to do. It is really wierd but i see there is no solution still

---

### Post by Darell on 2007-03-21
I have the same problem too!
no solution yet?

---

### Post by Thadir on 2008-01-01
On the Superkaramba website they sugest you switch on the session support. I tried that. Dont know if it will work bc I dont ofthen reboot.

---

