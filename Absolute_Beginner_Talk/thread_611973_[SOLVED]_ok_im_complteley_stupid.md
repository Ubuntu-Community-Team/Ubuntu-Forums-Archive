---
title: "[SOLVED] ok im complteley stupid"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-11-13
Ok i know i'm now officially the most gullible ubuntu user as i used the rm command as root and iv'e deleted my entire home directory :P so erm... how do i get it back so i have all the folders again?

thanx for help in advance everyone

---

### Post by overdrank on 2007-11-13
> **steveandbill said:**
> first type this in

Code:


just to make sure you wont be left with any have deleted corrupt folders


then type



make sure this works.


ps dont worry your not the first today dam spammers :(

Do not use that command!

---

### Post by philinux on 2007-11-13
DONT

it will remove all your system

---

### Post by PriceChild on 2007-11-13
It will be automatically repopulated as you log in and use programs.

Sorry for the spammer.

---

### Post by Paul820 on 2007-11-13
S/He already did, that's why s/he is posting how to get it back.

---

### Post by 900donuts on 2007-11-13
who told you to type that?

do you still have access to the gui or did it just delete the the folders contents(example: movies documents pictures?)

i have little experience in the effects of root but there should be a recovery program in add/remove or in synaptic if that doesn't work there are plenty of live cds geared towards system recovery

---

### Post by kamitsukai on 2007-11-13
no offence or anything but can i wait o see what other people say as well as your solution has rm in it to :(


the thing above was i was just about to post thnx guys

---

### Post by jdong on 2007-11-13
Unfortunately once files are deleted it's extremely difficult, if not impossibly tedious, to recover it all back. I hope you didn't lose anything important during this attack, and made backups prior.

The address block in question has been banned from the forums but that's just a workaround -- in the end nobody can solve this kind of problem except the user being cautious with freshly registered / low-post-count accounts giving odd looking advice.

---

### Post by kamitsukai on 2007-11-13
well it doesent matter most of the stuff is easily replaced and i had my important stuff on my usb flashdrive :P

---

### Post by jdong on 2007-11-13
> **kamitsukai said:**
> well it doesent matter most of the stuff is easily replaced and i had my important stuff on my usb flashdrive :P


Finally, someone who makes backups :)


You can restore the home directory to pristine state by running **rsync -av --delete /etc/skel/. ~/.; sudo chown your_user:your_user -R ~/**, but **DO NOT RUN THIS COMMAND ON EXISTING HOME DIRECTORIES -- IT IS DESTRUCTIVE (deletes existing files)**

---

### Post by kamitsukai on 2007-11-13
thanx everyone and next time i will wait for second oppinions on things before executing a command from a new account! 

Lesson well learnt!:lolflag:

---

### Post by sailor2001 on 2007-11-13
they made a sticky about that spammer.....also after you load up all the programs you want..(I can never get enough of them) you might want to burn them on a disk..  "aptoncd" located in synaptics

---

