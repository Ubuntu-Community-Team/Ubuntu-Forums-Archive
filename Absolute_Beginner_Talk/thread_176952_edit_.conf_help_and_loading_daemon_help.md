---
title: "edit .conf help and loading daemon help"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by CloudyHaze on 2006-05-15
alright, well decided to give that 3ddesktop a go last night.

went great, except for a couple minor noobie type problems :)

ok. when i first activated the 3ddesk from the terminal, i had three of my four desktops in grey.

alright, so i:

3ddesk --acquire=100

great, now its all good.

after this, i assigned 3ddesk start to the windows key on the keyboard.

then shut down the machine.......come back later, start it up.....hit the windows key to activate 3ddesk, but now the grey screens are back! 

must i load the daemon everytime i restart?

next question:

ok, i wanted to get rid of the numbers on the 3ddesktop......so i go to the .conf file through the terminal via

sudo vim /etc/3ddesktop/3ddesktop.conf

now how do i edit this? it wont let me type or change anything that is brought up? must i set the permission to root? i think it did ask for root pw after the sudo command.

any help appreciated

---

### Post by userundefine on 2006-05-15
[QUOTE=CloudyHaze]next question:

ok, i wanted to get rid of the numbers on the 3ddesktop......so i go to the .conf file through the terminal via

sudo vim /etc/3ddesktop/3ddesktop.conf

now how do i edit this? it wont let me type or change anything that is brought up? must i set the permission to root? i think it did ask for root pw after the sudo command.

any help appreciated[/QUOTE]
I suggest not using vim as a newbie.  It's quite powerful, but unintuitive when first using it.  Why don't you try:

sudo nano /etc/3ddesktop/3ddesktop.conf

Nano is simple and straight-forward.

---

### Post by CloudyHaze on 2006-05-16
anyone else got some input?

---

### Post by CloudyHaze on 2006-05-18
alrighty.

editing with vim was alot easier for me :) thanks


but still, 3ddesk --acquire=100  is not sticking.

can i put than into the conf file so that when 3ddesk is loaded that acquire happens?

---

