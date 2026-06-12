---
title: "[SOLVED] user &amp;quot;root&amp;quot;"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by indiana_crook on 2008-03-02
When I try to run automatix, I can't.  It won't let me use my password as the administrator.  It says that it fails to recognize me as user root.  I used this thing just last night and it worked fine with my account.  All of the sudden today, I'm not the administrator???  I found this out when I tried to set up users and groups and found out that I can't do that on either of the accounts I've created, mine being the first one.  PLEASE HELP!!

---

### Post by Crooksey on 2008-03-02
```

$ sudo <command>
```

---

### Post by indiana_crook on 2008-03-02
okay how was that supposed to help??

---

### Post by Crooksey on 2008-03-02
To launch automatrix as root..

```

$ sudo automatrix
```

---

### Post by indiana_crook on 2008-03-02
that's not doing anything.

---

### Post by Oldsoldier2003 on 2008-03-02
> **Crooksey said:**
> To launch automatrix as root..

```

$ sudo automatrix
```

NOOOO..... Automatix is highly discouraged for use. it can severly trash your system

---

### Post by indiana_crook on 2008-03-02
Really???...  what do I do about not being able to edit users and such?

---

### Post by Crooksey on 2008-03-02
I didnt say it was good, but I told you how to run it with root priverlages, which was the question asked.

---

### Post by indiana_crook on 2008-03-02
well, I'm lost.  Starting to hate ubuntu.

---

### Post by Crooksey on 2008-03-02
If you arent preperaed to learn how things work, then give up now.

---

### Post by Oldsoldier2003 on 2008-03-02
> **indiana_crook said:**
> well, I'm lost.  Starting to hate ubuntu.

Automatix is a poorly written application that has a history of wrecking Ubuntu installations. Using automatix to install things often leads to you having to completely reinstall your system because of the mess it makes. What are you trying to do? if you tell us what you are trying to achieve we can point you in the right direction.

---

### Post by justinmiller87 on 2008-03-02
> **Crooksey said:**
> If you arent preperaed to learn how things work, then give up now.
Now now Crooksey, be nice. We're not going to win any users over by being rude.

---

### Post by Crooksey on 2008-03-02
Support forums are to help users, if people arent going to be grateful, then the time could be spent fixing another issue.

People either want linux or they dont, can tell them how to solve problems, not sell them an OS.

---

### Post by indiana_crook on 2008-03-02
Okay, so I'm not familiar with this OS at all.  You must understand that I'm completely new to this.  When you (Crooksey) said "sudo <command>"  I had no clue what you meant.  If you're no more patient with me than that, please leave, and yes I am grateful for the help.  At this point I'm simply trying to edit the users on my ubuntu.  I created one last night for my brother.  Everything was working fine until today, the users and groups menu under the system > administration menu is gone.  I try to use automatix, (which apparently is a bad idea) and it tells me that my user account is not root???  If someone wants my number I'll give it to you.  I'm desprate!!??

---

### Post by Crooksey on 2008-03-02
Applications >> Accessories >> Terminal

This loads the command propmpt window.

And anything prefixed with "$", is a command.

In ubuntu you cannot login as root user, you can only temporarily gain root privlages, with the use of the sudo command.

---

### Post by louieb on 2008-03-02
i wonder if you removed yourself from the admin group? You have to be a member of that group to run sudo or automatix or any system update task.
to check see if you can bring up System>Administration>Users and Groups.

to fix you have to boot into recovery mode and run the usermod command. :)Just can't remember how.

---

### Post by Oldsoldier2003 on 2008-03-02
> **louieb said:**
> i wonder if you removed yourself from the admin group? You have to be a member of that group to run sudo.
to check see if you can bring up** System>Administration>Users and Groups**.

to fix you have to boot into recovery mode and run the usermod command. :)Just can't remember how.

or terminal:
```
id
```

---

### Post by indiana_crook on 2008-03-02
okay i put the "id" thing in the terminal, now what am I trying to do?

---

### Post by jpeddicord on 2008-03-02
Let's keep the yelling to a dull roar.

> okay i put the "id" thing in the terminal, now what am I trying to do?
Paste the results here so we can see if you are in the admin group.

---

### Post by Oldsoldier2003 on 2008-03-02
> **indiana_crook said:**
> okay i put the "id" thing in the terminal, now what am I trying to do?

id will tell you all the groups you are in for example
```

uid=1000(chuck) gid=1000(chuck) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),**117(admin)**,1000(chuck)

```
you are looking to see if you are in the admin group
 edit: a lot of times you will be asked to run a terminal command because its easier to paste the result her than to upload a screenshot. makes it a lot easier for folks to help you if the can see the actual output of the commands :)

---

### Post by indiana_crook on 2008-03-02
uid=1000(caleb) gid=1000(caleb) groups=4(adm),20(dialout),24(cdrom),25(floppy),2

I believe so...

---

### Post by Oldsoldier2003 on 2008-03-02
> **indiana_crook said:**
> uid=1000(caleb) gid=1000(caleb) groups=4(adm),20(dialout),24(cdrom),25(floppy),2

I believe so...
it looks like you weren't able to paste the whole return from the command could you do it again?

---

### Post by indiana_crook on 2008-03-02
uid=1000(caleb) gid=1000(caleb) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),115(netdev),117(powerdev),1000(caleb)

---

### Post by Oldsoldier2003 on 2008-03-02
> **indiana_crook said:**
> uid=1000(caleb) gid=1000(caleb) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),115(netdev),117(powerdev),1000(caleb)

if thats the full output of the command you are not in the admin group. I'm afraid at the moment I'm not quite able to explain how to recover that so, I'll let another person take a stab at it for you.

---

### Post by amingv on 2008-03-02
> **Oldsoldier2003 said:**
> if thats the full output of the command you are not in the admin group. I'm afraid at the moment I'm not quite able to explain how to recover that so, I'll let another person take a stab at it for you.

I'll take the stab then, proceed as follows:

Restart your system, before Ubuntu starts loading press the ESC key for the grub menu. From the menu choose the option that includes "recovery mode" on it's name (If you have more than one, choose the first one). Wait for it to load, you will find a console-only session. Type in this command:

```
usermod -a -G admin <your_username>
```
afther that, issue this command to reboot:
```
shutdown now -r
```

Login as normal, you should be in the admin group.

---

### Post by Oldsoldier2003 on 2008-03-02
Thanks amingv, I was having one of what i call my "gray moments". Not enough sleep and a big case of CRS (Can't Remember errrrm "Stuff")

---

### Post by Athelstan101 on 2008-03-02
If your account has lost its admin rights then you could get them back again by logging in as root. You might need to press CTRL+ALT+F1 to get to the tty1 terminal (pressing CTRL+ALT+F7 will get you back to your X session again) and then login as root.

Once you've logged in as root, type:
```
$ vi /etc/group
```

Whilst in 'vi', edit the /etc/group file so that the admin line has your account name at the end of it i.e.
```
admin:x:114:my_account_name
```

Save the file and then try what you wanted to do originally - you may need to logout and login first.

Hope that helps.

---

### Post by indiana_crook on 2008-03-02
GOOD JOB AMINGV!!!!  You are the lifesaver.  Couldn't have done it without you Oldsoldier.  I'm good for now.  Keep your eyes open for more of my threads!!! LOL!

---

### Post by amingv on 2008-03-02
> **Oldsoldier2003 said:**
> Thanks amingv, I was having one of what i call my "gray moments". Not enough sleep and a big case of CRS (Can't Remember errrrm "Stuff")

No problem. I had a similar problem once and boy I suffered! It's nice to see how simple things are when you look from outside.

> **Athelstan101 said:**
> If your account has lost its admin rights then you could get them back again by logging in as root. You might need to press CTRL+ALT+F1 to get to the tty1 terminal (pressing CTRL+ALT+F7 will get you back to your X session again) and then login as root.

Once you've logged in as root, type:
```
$ vi /etc/group
```

Whilst in 'vi', edit the /etc/group file so that the admin line has your account name at the end of it i.e.
```
admin:x:114:my_account_name
```

Save the file and then try what you wanted to do originally - you may need to logout and login first.

Hope that helps.

Though this may work, Ubuntu won't let you login as root by default. (Unless OP changed his settings).

---

### Post by louieb on 2008-03-02
> **Oldsoldier2003 said:**
> ...and a big case of CRS (Can't Remember errrrm "Stuff")
lol: me and my buddies  call it something else.

---

