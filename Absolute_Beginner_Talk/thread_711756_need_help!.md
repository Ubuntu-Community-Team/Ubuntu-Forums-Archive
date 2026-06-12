---
title: "need help!"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by RJ Hythloday on 2008-03-01
I've been using edubuntu on a hdd to try out for a friends install. I have been trying how to figure out how to run fluxbox. 

I created a file ~/.xsessions.conf and in it was the command exec startfluxbox.
 
ctrl+alt+bkspc fluxbox starts

No right click menu, no way to start a terminal

ctrl+alt+del rescue mode

startx - tells me dangerous to run in root continue/cancel

continue nothing in documents folder (they have one in edu) no internet access w/ browser.

I'm on a livecd of kubuntu right now and really want to get one file off of this hdd.
> hal-storage-fixed-mount refused uid 999

is there any way I can get into the hdd w/ the username/pw I set up on that os?

I really don't care about saving that install, fixing fluxbox, or anything else if I can get to the one file I'll reinstall edubuntu on that hdd in the system it's going to be in. I also have a couple hdds w/ kubuntu installed in differing stages of customization.
[B][SIZE="4"]
Can anyone help me get access to the current hdd?[/SIZE][/B]

---

### Post by Iandefor on 2008-03-01
I can't really offer much help with the rescuing-file thing at the moment (I'd need to have time/energy to reboot into a LiveCD and work it out from there), but here's a tidbit in case it should come in handy:

The proper way to start a Fluxbox session after it's been installed, by the way, is to go to the Options menu at the login screen, select "Select Session", and choose "Fluxbox"

It'll ask you if you want to make it the default session. Select the answer that's appropriate.

---

### Post by RJ Hythloday on 2008-03-01
> **Iandefor said:**
> I can't really offer much help with the rescuing-file thing at the moment (I'd need to have time/energy to reboot into a LiveCD and work it out from there), but here's a tidbit in case it should come in handy:

The proper way to start a Fluxbox session after it's been installed, by the way, is to go to the Options menu at the login screen, select "Select Session", and choose "Fluxbox"

It'll ask you if you want to make it the default session. Select the answer that's appropriate.
yeah, I've been through that, I installed xdm as default and it doesn't offer a choice of desktops at login.

Thanks though.

It really seems there should be a way to access sda1 from the livecd or reboot into the hdd and something besides startx to get the edudesktop up.

---

