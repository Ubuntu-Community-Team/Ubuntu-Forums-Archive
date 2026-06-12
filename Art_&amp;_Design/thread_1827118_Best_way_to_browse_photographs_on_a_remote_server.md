---
title: "Best way to browse photographs on a remote server"
date: 2011-08-17
forum: Art &amp; Design
---

### Post by gunksta on 2011-08-17
I just got a new DSLR which inspired me to try to re-think my digital workflow. I would like to store my photographs on my server at ~/Pictures. The server is already accessible remotely (ssh) and runs Gallery3, for publishing. Because I already have a decent system for backing up the server, I'd rather put all of my photographs there, rather than tote them around on my laptop. My thinking is that this way I can access the photos remotely and it makes upgrading the laptop in a few years easier.

Eventually I want to build a set of folders under ~/Tags and link the photos to the directory as a tagging solution. My goal is to avoid applications like f-spot, etc. My only problem seems to be thumbnails. I can access the photos through nautilus, but I don't get any thumbnails. And, applications like geeqie and raw therapee can't even see that I'm connected to the remote system.

Thoughts? Suggestions? Browsing photos without thumbnails is a little hard. I'm curious to hear what others are doing or if you have a solution to my little dilemma.

---

### Post by Dragonbite on 2011-08-17
Are you sure Nautilus has the option to preview remote pictures turned on?  It's a specific setting and I don't know if it defaults to off (I think so).

---

### Post by gunksta on 2011-08-18
Excellent suggestion. Turns out that Nautilus does not automatically create thumbnails for remote files. I'm at work, so creating thumbnails of the photos would take forever, but it should work faster at home.

Excellent suggestion. Turns out that Nautilus can do most of what I want it to do. In thinking about it, another option might be to formally map the location of this external drive, so apps like RawTherapee can also access it.

--andy

---

### Post by zaipai on 2011-08-20
There are also plugins that Nautilus can use to create thumbs of formats it does not understand. So if you have images that are not creating previews, then search for a Nautilus plugin for that file type.

---

