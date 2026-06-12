---
title: "Root password to adminster system."
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Dominaduro on 2007-10-28
Hi guys, I just transferred from opensuse 10.3 to Gutsy (and synaptic made it worth it by far).

There's one thing that I am not used to, however. When installing, I enabled the root account. I then opened up users-admin and went to the user privileges section. I noticed that my main account had the "Administer the System" option checked. Now, from what I see, this enables it so that I am able to see all the launchers in the System->Administer menu to change things. And then when I click on them, it asks me to enter my OWN password, not the root.

I don't see the difference between this and running as root (in fact, sometimes it doesn't even ask me to type in my password when opening synaptic or something like that). So what I did was, I unchecked "Administer the System" for my main user account and gave the root account all privileges. The problem is, when I logged back into the main account,  I couldn't see any of the launchers in that System->Admin menu. (As a beginner, it took me quite a bit of time to figure out the name of the program to run was users-admin). 

It's not that big of a deal, because I can still just type "gksudo users-admin" or something like that (and use the root password); however, it's just more convenient if I can see all the options in the main menu.

Any ideas?
Thanks.

---

### Post by taurus on 2007-10-28
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by plr4ever on 2007-10-28
I also have run into Gutsy not asking me for my password if i type it in about a dozen times. However, i don't think this means your are running under full root priviliges. Is there some reason you want to type in your password at every administrative option? (ie, someone in the house/office you dont trust?)

---

### Post by lpevey on 2007-10-28
If you right-click on the menu and choose "edit Menus," you can add and remove things from teh menu.  In the Administration section, are those options there and just unchecked, or are they completely gone?  If they are just unchecked, it may be as simple as checking them.  If they're gone, I know you could manually add items, but I think there must be an easier way.

---

### Post by daimaru on 2007-10-28
> **plr4ever said:**
> I also have run into Gutsy not asking me for my password if i type it in about a dozen times. However, i don't think this means your are running under full root priviliges. Is there some reason you want to type in your password at every administrative option? (ie, someone in the house/office you dont trust?)

ubuntu remembers your admin login for 5 to 10 minutes or so not sure which . so if in terminal or in the system menu you just used that command and then do a sudo again it wont ask for password.

---

### Post by Dominaduro on 2007-10-28
I read this prior to posting ([https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo))..I'll look into it more.

This is interesting...so I turned off "Administer the System" for my main account. And then when I ran in it...I typed in the terminal "gksudo users-admin" and when I typed in the root account password, it said wrong password. I then typed in mine...and it said something like "failed to open users-admin because you don't have the privileges."  It's obviously not asking for the root password in the first place.

I then just went to the terminal and typed su...logged in...and of course users-admin works just fine.

As for the menus, when the "Administer the System" option is off, (the menu items are still there), when you check them, it automatically UN-checks them in about 2 seconds...probably has to do with the same issue of asking me for my password instead of the root.

It's not that I don't trust someone else in the house...I just don't trust myself. I feel safer when I'm using the root account to change things, not my own. That, and I wish there was a way to actually make a "root" user (as in, can use the desktop). In other words, I want to make a user that can have all privileges (easy), AND, make it such that that user is the superuser too. (But this first issue I'm describing above has more priority).


Amazingly quick replies, thanks guys.

---

### Post by daimaru on 2007-10-28
you can enable root login go to system-->administration-->login window on security tab check enable admin login
EDIT then on login screen you can login as root

---

### Post by Dominaduro on 2007-10-28
Thank you.

That's actually pretty nifty, because with the easy user switching, it makes things pretty convenient.

However, it would be even more convenient if sudo just asked me for my root password, rather than mine. Any ideas?

I figure that maybe solving that issue would be easier since the items in the administration menu are "gkduo blah blah" anyway.

---

### Post by daimaru on 2007-10-28
> **Dominaduro said:**
> Thank you.

That's actually pretty nifty, because with the easy user switching, it makes things pretty convenient.

However, it would be even more convenient if sudo just asked me for my root password, rather than mine. Any ideas?

I figure that maybe solving that issue would be easier since the items in the administration menu are "gkduo blah blah" anyway.

besides changing your password to the root one :lolflag: i'm at a loss sorry not experienced enough for that, but with this little bump maybe someone else can help

---

### Post by Leonivek on 2007-10-28
I'm curious, though.  Why do you need to login as Root when you can sudo or gksudo your way through everything?  If you run something that needs root-level privileges, it'll ask you for your password (not root's).  I'm fairly new to using Linux, but I've been using it for over 2 years now and have never had to log in as root.

Having the "Administer the System" option checked does not reveal additional menu items; that is done by editing the menu as lpevey mentioned.  That option allows you to administer your system with root priviliges (sudo or gksudo) with YOUR password, not the Root account's password.

Anyhow, just curious...  :)

---

### Post by Dominaduro on 2007-10-28
See now, that's exactly what's bugging me. When you turn off "administer the system" the menu options disappear..and when I try to add them in (re-check them), it automatically disables them. And even with "Administer the System" off, it still asks me for MY password. The only difference is, when I type in my password, it says I don't have privileges. 

I just want it to use the root password for sudo rather than my own. I think I just kind of want it that way cus I got used to it in SUSE. If not done this way, I don't see the difference between a normal user and a system administrator (logged in, and then type your own password to gain root privileges? a little weird).

---

### Post by Dominaduro on 2007-10-28
Yeah, I can't seem to find a way to get sudo to use the root password.

I guess I'll just get used to being the administrator again.

---

### Post by Leonivek on 2007-10-28
> **Dominaduro said:**
> See now, that's exactly what's bugging me. When you turn off "administer the system" the menu options disappear..and when I try to add them in (re-check them), it automatically disables them. And even with "Administer the System" off, it still asks me for MY password. The only difference is, when I type in my password, it says I don't have privileges. 

I just want it to use the root password for sudo rather than my own. I think I just kind of want it that way cus I got used to it in SUSE. If not done this way, I don't see the difference between a normal user and a system administrator (logged in, and then type your own password to gain root privileges? a little weird).

The sudo or gksudo commands "raise" you to Superuser status temporarily as long as you can provide your password and as long as your account is set to administer the system.  Same as any other programs or settings that ask you for your password; they are raising you to superuser temporarily.

EDIT: A normal user wouldn't be able to change anything because they are not set to administer the system.

---

