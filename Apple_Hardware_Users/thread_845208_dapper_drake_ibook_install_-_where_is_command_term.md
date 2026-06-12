---
title: "dapper drake ibook install - where is command terminal?"
date: 2008-06-30
forum: Apple Hardware Users
---

### Post by dannyo on 2008-06-30
hi

i am a newbie to linux and trying to boot from a live cd on an ibook g3. it all goes well, ubuntu logo, all the checks say ok, until it says it is configuring X, then the screen goes black, with a flashing cursor.

have read lots online about this, and seems i need to make alterations through the command terminal, reached through pressing ctrl-alt-f1. but this just darkens the screen (F2 lightens it again)

how can I get to the terminal?

- when i get to the first boot and can actually type things in, if i type rescue i just get an error message.

typing live-powerpc at this point eventually gets to a point where there is a cursor, and i can type, but nothing is recognised.

anyone know what i should do? I was so pleased when ubuntu came up on the screen, but that was ages ago now.

thanks
jonathan

---

### Post by damis648 on 2008-06-30
If I were you, I would download Hardy Heron. Dapper Drake is an outdated release. Maybe you will get more luck.

---

### Post by stream303 on 2008-06-30
I'd review this faq and see if some of the techniques for booting live-desktops with Gutsy will work with your Dapper live-cd:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

In many instances, the splash screen or other video variable prevents the use of virtual terminals.  In my case, I use "nosplash" or "quiet nosplash" as kernel parameters during boot.

You may want to try the "alternate" installer rather than the live-desktop if you have decided you definitely want to install - although it is text/ncurses based, it will install yet provide a full gui afterwards and may not have the problem configuring X like the live version has.

Unless you absolutely need Dapper, you may want to try some of the later community-supported versions:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Feisty 7.04 makes for a good starting point if you are just starting out, although any release is good - each has some small quirks that can usually be ironed out.

---

