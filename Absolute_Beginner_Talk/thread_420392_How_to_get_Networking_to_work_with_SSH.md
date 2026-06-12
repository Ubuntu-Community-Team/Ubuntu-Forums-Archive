---
title: "How to get Networking to work with SSH?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Angellis_ater on 2007-04-23
Hi!

I have a small problem that I need to get working.

I have two computers attached via a normal switch, which means that they have different IPs and all that and aren't really apart of my "internal" network, although they're both in the same house.

Now, I've installed sshfs, open-ssh, (both client and server) on both and I can access the secondary computer from the main computer through Nautilus using "ssh:IP.NU.MB.ER/Shared Folder" and saving the username and password on my keyring. That's fine and dandy - now, I can't do the same thing from the secondary computer to this one, that's problem number 1.

Problem 2 is that I can play some files from the secondary computer (ogg-files), but not others (mp3, avi) on the primary computer. If I send a file or files to the secondary from the primary computer, they're all locked from using since the rights attached to them are specific for the primary computer user.

How do I get all of this to work? Please help!

---

### Post by aktiwers on 2007-04-24
I have the same setup. and it works fine this way:
Places => Connect to server... 

1) Pick SSH from drop down menu.
2)  In Server field type in the IP of the
3) Leave port (atleast for me.. or pick an open port) blank together with folder.
4) Type in the remove computers username
5) Pick a name to recognize your connection

Thats all I have to do!

---

