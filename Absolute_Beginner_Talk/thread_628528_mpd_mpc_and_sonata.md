---
title: "mpd mpc and sonata?"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by semperfiguy on 2007-12-01
I am trying to use mpd and mpc.  I edited the .mpdconf file to include my music directory and everything, I ran mpd --create-db.  and I see all my files being added.  Then I try and run mpc update, mpc add /, and then mpc playlist, but nothing ever gets added to the playlist?  When I run sonata, I have it set to my music directory but it never adds any files to it?  How do you get the mpd players to work?

---

### Post by Dries_Lee on 2008-01-06
You should check your firewall settings. I had the same problem as you, and adding a rule in Firestarter solved it.

---

### Post by mcduck on 2008-01-06
You shouldn't need to change any firewall settings as long as MPD and the client are running on the same machine.

But one thing you should check is that your files (and directories containing the files) have permissions that allow other users to read them (as MPD runs as it's own user). So, 'others' must have reading rights for files, and read&execute rights for directories.

And then, 'mpc add /' might not be the correct command..  Try "mpc ls | mpc add".

Anyway, the way I got MPD to work was to install it as a daemon (so it gets started automatically, and runs as it's own user). Then I just created a symbolic link from my music directory into /var/lib/mpd/music (MPD's default music directory, "sudo ln -s /home/mcduck/Music /var/lib/mpd/music" creates the link). 

I do all my configuration in /etc/mpd.conf, although there really isn't much that would need changing when using MPD this way. Only thing I had to change was the character set for filesystem & id tags (had to change it to UTF-8 ). Actually the ~/.mpdconf would be useless as I'm not the one starting MPD so it would never even read that file..

---

