---
title: "Mouse and keyboard random lockups?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Sinergy on 2007-05-17
Hi, ive had ubuntu for a few days now im very happy with it so far except for one thing.

My mouse and keyboard seem to randomly lock up and stop working, the mouse is able to move the cursor around the screen but i cannot click anything, i cannot type anything, i cannot ctrl + alt + f1 or anything. Anyone have any ideas as to whats happening?The only way i can fix it so far is a reboot. 

I am using a standard logitech usb mouse and keyboard.

---

### Post by Hobo Joe on 2007-05-17
I think this is a Fiesty issue, it happens to me to.

At first I thought it was Beryl, but then it happened when Beryl was off, then I thought it might be WINE, but I found out it's neither...

Pretty annoying.

---

### Post by Sinergy on 2007-05-17
Yeh it really sucks, i hope someone has a solution to this i would really like it to be solved.

---

### Post by k33bz on 2007-05-17
wow, sorry to say i dont have that problem, nor have i ever had that problem. you both might want to check your configurations. other than that i dont know what else to offer

---

### Post by Sinergy on 2007-05-17
the mouse configuration in the preferences tab?

---

### Post by aryah on 2007-05-24
Ive been having this problem too, and it has been getting progressivly worse with time. Im in console in Elinks now, and cannot do anything if I Alt-F7 into my GUI, not even get back here. Ive been using the keyboard mouse for a while, my mouse died a while ago, and used this just for the first fix, till I go get a new one, but got used to it enough that I was simply lazy to do this.. 
Anyways, first, it would be that my num lock would sometimes get just stuck, interfiering with my (kb) mouse,  and later, that and  I couldnt click, and/or menues, starting a new application, or killing/minimizing/maximising windows wouldnt work. Id go wild over my keyboard, punching letters randomly and it would eventually work again. sometimes killing some application, like nautilus or gdm helped if nothing else would. But now, few reboots in a row it was pretty much a complete lockdown, and numlock/capslock/scrollock indicators couldnt be toggled either. Nor could I use up/down keyes to navigate menues. If I persist hitting numpad keys enough, sometimes Ill be able to click. In my graphical login window, the keyboard works, and I can toggle the *locks, but the mouse keyboard doesnt, though it usually works no problem.
I do have beryl installed, but Im not using it. Killing mouse keyboard from the console doesnt help, the keyboard still gets locked. Killing nautilus after logging in and quickly Alt-F1 -ing back to console doesnt help either.
I have no idea what to even start doing.
My computer has been on for a few days without restarts (killed gdm few times though), and in the meantime Ive installed a lot of things, experimenting, mostly networking and security related, like i2p, tor, privoxy (two of them), yacy, seahorse, freenet, moblock, some firefox stuff,  and the necessary java components for some of them, but the problem doesnt appear to have either started or to happen in relation to them running or not..
I dont notice anything relevant in my system logs or dmesg, and I havent changed or know to have done anything to affect a change in my X settings since Ive installed beryl, after which it did work, certainly better than now.
The last thing that I ran before the reboot that now left me withought a gui is synaptic. It didnt respond, my comp was rather slowed down due to excessive number of tabs open in firefox I presume (Im rather low on memory), and I lost patiece and simply rebooted.
Ive upgraded from edgy to feisty, about a week ago. never had similar issues there. 
As you can understand given the situation Im currently in, Ill appreciate any feedback alot, since I dont even know where to start (apart from restarting X over and over again, which Ill do the moment I send this message, since I risk having to reboot)

---

### Post by aryah on 2007-05-24
managed to get back into GUI, restarting gdm did make it work, but the keyboard mouse didnt work. 
Turning it on again without a mouse to work with was not as easy as it could have been :)

perhaps there are two unrelated problems here (occasional keyboard/mouse locks and perhaps a buggy keyboard mouse? i suppose its not an often used feature), that wierdly interact - ive read someones bugreport describing much similar situation, but with messages in his syslog I didnt see. Logically, since they were mouse-related :)

---

### Post by AmpDivorax on 2007-05-25
edited due to a mixup.

---

### Post by LazyBoy on 2007-05-25
(Kubuntu 7.04)  I have a non responsive keyboard within X sessions.  I am posting now from a failsafe X session, where it works. 

I upgraded today, but hadn't rebooted when the problem started (for the first time).  Now I have rebooted and still have the problem.

The keyboard works for the kdm password entry and within a  failsafe X session.  I can ctrl-alt-f1 from the kdm screen or the failsafe and use a getty terminal, but if I log into non-failsafe X session, the keyboard won't work, even for ctrl-alt-f1.  The mouse works fine everywhere.

Any ideas?
LB

---

