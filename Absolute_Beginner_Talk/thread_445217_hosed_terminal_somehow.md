---
title: "hosed terminal somehow"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by maniac_X on 2007-05-15
my turn...I hosed my Terminal

i was setting up a Terminal Profile changing colors and what not

and then in the General tab(i think) I think I checked a box about 2/3 way down and typed something, closed the profile and Terminal window...and now when i try to open a Terminal window, it just opens and closes real fast.

so right now i can't  open and keep open a Terminal window.
the only way i can enter anything via terminal is use the alt-F2 method

anyway i can scrub what i did to get the Terminal window working like before i messed with creating a new profile? :confused:

---

### Post by Hobo Joe on 2007-05-15
Your avatar is very fitting. ;)

anyways, can you re-install the terminal through synaptic or something?

---

### Post by maniac_X on 2007-05-15
> **Hobo Joe said:**
> Your avatar is very fitting. ;)

anyways, can you re-install the terminal through synaptic or something?

that's a thought but i am not sure what to reinstall??...  i just reinstalled xterm and that didn't change/fix it. ??:confused:

---

### Post by Metacarpal on 2007-05-15
If you're using Ubuntu (gnome-flavored): Go to Places > Home.  hit ctrl+h to show hidden files.  Look for a folder entitled .gnome-terminal or something similar.  (I'm not on my Ubuntu PC right now, so I can't check for sure.  It might be inside of .gnome2)

Delete that folder.  That will clear your personal settings for terminal.

If you're using Kubuntu or Xubuntu, I'm not sure what to do.

---

### Post by maniac_X on 2007-05-15
> **Metacarpal said:**
> If you're using Ubuntu (gnome-flavored): Go to Places > Home.  hit ctrl+h to show hidden files.  Look for a folder entitled .gnome-terminal or something similar.  (I'm not on my Ubuntu PC right now, so I can't check for sure.  It might be inside of .gnome2)

Delete that folder.  That will clear your personal settings for terminal.

If you're using Kubuntu or Xubuntu, I'm not sure what to do.

btw, thanks to both of you for the quick response :) 

did as you said and i see 3 folders with "gnome" in the name

.gnome
.gnome2
.gnome2_private

no folders suggesting "terminal"

---

### Post by Hobo Joe on 2007-05-15
I looked under synaptic, and the package called ncurses-base and ncurses-bin look like they might do something...
> Terminal-related programs and man pages 
This package contains the programs used for manipulating the terminfo
database and individual terminfo entries, as well as some programs for
resetting terminals and such.

You might as well try re-installing, just to see if it works.

EDIT:

Wait, I found it!

gnome-terminal, and gnome-terminal-data. I'd try re-installing those.

---

### Post by Metacarpal on 2007-05-15
Open up .gnome2 and see if there is a gnome-terminal folder in there.

---

### Post by maniac_X on 2007-05-15
i started digging around in the Home folder.... and i found a folder named gnome-terminal inthe

.gconf/.aps folder

if that helps

edit: thx Hobo joe.... am trying your suggestion as i type this

will post back shortly..... i'm on dialup so might be a few minutes

---

### Post by maniac_X on 2007-05-15
Thank you one and all!!

Hobo Joe is the winner.....  but we are all winners (especially me) because we are using *buntu and there's this great community of users out here :guitar: 

now i can go and mess something else up :)

btw Hobo joe,  I chose that avatar on purpose because i knew, being newb with linux, it would be a humorous reminder of how i feel sometimes in this brave new world :)
as time goes along and my skill increases, I may change the Calvin avatar to something less anxious

---

### Post by maniac_X on 2007-05-15
well, i spoke too soon....

my original problem has morphed a little bit.

Hobo joe's suggestion partially fixed the problem. Here is what happens currently:

i click the Terminal icon in my panel and sometimes it opens/closes real fast and sometimes it opens two windows like in this screenshot:
[http://img237.imageshack.us/my.php?image=screenshotbi8.png](http://img237.imageshack.us/my.php?image=screenshotbi8.png)

i have gone in and deleted and profiles present except the Default. 
going into Terminal > Reset or Reset and Clear doesn't do anything.

---

### Post by maniac_X on 2007-05-15
well,  i played around with it some more.... seems when i launch a terminal window from 
Applications > Accesories > Tereminal  it opens like it's supposed to

so i deleted the link on my panel and  made a new link to the panel and it seems to be working now...opening only a single window like it originally did.

Thanks for listening, we now return you to your regualr programing... :)

---

