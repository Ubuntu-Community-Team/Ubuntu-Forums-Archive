---
title: "need help with updates and installing: feisty"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by svjenni on 2007-04-09
Hi all 

I am a new Ubuntu convert, I upgraded my laptop pretty seamlessly and was so convinced that I am now typing this from my main pc now on feisty

The change to Ubuntu was a completely clean install from an edgy live dvd and then i upgraded straight to feisty after the updates came down - the reason for my decision to go with feisty was the amarok mtp support.

So the problem is now whenever i try to update or install anything i get an error message.

This is the latest error if i try to install updates

E: /var/cache/apt/archives/openoffice.org-style-andromeda_2.2.0-1ubuntu2_all.deb: files list file for package `gdebi' is missing final newline

And if I try to install amarok

E: /var/cache/apt/archives/libartsc0_1.5.6-0ubuntu1_i386.deb: files list file for package `gdebi' is missing final newline

I'm new at this, but i'd really like to try and sort this out, please help!

---

### Post by svjenni on 2007-04-09
bump,

p.s 
i have tried reinstalling gdebi but get the same error

---

### Post by jhenager on 2007-04-09
It sounds like a file needs to be edited and insert a hard return at the end of the file and then save it.
I'm running edgy, so I don't know if I have that file.

---

### Post by svjenni on 2007-04-10
Thanks, I worked out that that was what I needed to do but couldn't work out how to do it,

this seems to be a pretty big stumbling block for newbies.

I gave up and started again with edgy and I am getting on with it better than fiesty, will wait for official release date before I upgrade again

---

