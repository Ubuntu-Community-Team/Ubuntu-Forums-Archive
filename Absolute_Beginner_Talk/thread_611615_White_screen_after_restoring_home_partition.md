---
title: "White screen after restoring home partition"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2007-11-13
I've decided to downgrade from Gutsy to Feisty after several unresolved issues.
As advised by many people, I have my /home directory on another partition.
I did a fresh install of Feisty and copied the entire contents of my former /home directory to the new.  

On reboot I'm left with a white screen with a black cursor.  Can't do anything with that.

Have I done something wrong in copying over my old home partition?  It's the first time I've tried it.

Can I recover the situation somehow?


Thanks.

---

### Post by Pumalite on 2007-11-13
I'd save data and do a clean install of Feisty.

---

### Post by Pumalite on 2007-11-13
Double post.

---

### Post by Phosphoric on 2007-11-13
Pumalite,

which data should I save?  What do you think might have corrupted my desktop?

I'd like to keep my gnucash register (very important), firefox bookmarks, letters etc.

is there a prefferred way to merge a home directory?

Thanks.

---

### Post by ByteJuggler on 2007-11-13
Probably some of the settings/config files in your home folder is causing some heartburn for Feisty/the desktop manager.  So, to temporarily disable all of them, try the following (off the top of my head):

1.) At the white desktop press "ctrl-alt-f1".  You must get back to a text mode "console" login prompt.
2.) Log in here with your normal username and password.  This should drop you at a command prompt.
3.) Enter the following commands, exactly as shown:

```

mkdir OldConfig
mv .* OldConfig/

```

After the "mv" (move) command above you'll get some warnings about not being able to move "." and ".."  You can ignore those.  Then reboot, by doing:

```

sudo shutdown -r now

```

You can probably also press ctrl-alt-del. After the reboot, you should be able to log into your desktop, after which you can selectively restore config files from the "OldConfig" folder as appropriate.

---

### Post by Pumalite on 2007-11-13
Delete.

---

### Post by Phosphoric on 2007-11-13
:)@ ByteJuggler, thanks I'll try that when I get home later.  I assume a basic desktop will appear if I've moved everything from my home directory to OldConfig?

@Pumalite, thanks for the link to psychocats, I've already been there and followed the advice on setting up a seperate home partition.  What it dosen't tell you is how to restore it, hence my pickle now.

Thanks.:)

---

### Post by jaybombalous on 2007-11-13
if u have your old /home dir and all its config files on a separate partition, leave them there and reinstall feisty. then u can mount that partition in feisty and copy and paste all your personal files over to your new home directory. But don't copy the /home/username folder just the files u need.

---

### Post by jaybombalous on 2007-11-13
> **Phosphoric said:**
> :)@ ByteJuggler, thanks I'll try that when I get home later.  I assume a basic desktop will appear if I've moved everything from my home directory to OldConfig?

Thanks.:)

yes, its taking all the files from /home/*username* and moving them to /home*/username*/oldconfig

This will move the config files out of the way so feisty won't try to load them.

hidden files always start with a '.' the reason why the command ```
mv .*
``` it moves anything that starts with a '.' and ends with '*' ( * means any type character any length). which in the /home directory is all your personal config files. :) hope that helps the understanding

---

### Post by Pumalite on 2007-11-13
Here are a couple of links for saving/restoring:

[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)

---

### Post by Phosphoric on 2007-11-13
OK, after a lot of good advice I have Feisty up and running.

The white screen problem, I couldn't get out of.  Tried ByteJuggler's tip to get back to a text terminal but that didn't work.  No response.

So I re-installed 7.04 and then compared all the files in my old home directory on the seperate partition with the new home directory and deleted all the common files so that there would be no clash.  I then copied over the remaining files to the new home directory and re-booted.  All ok.  So far so good.

I then re-installed gnucash and was devestated when it couldn't find my old files.

After a lot of ponsing about I managed to get it to recognise my latest files and I seem to have kept all my hard work  over the last few months.

I now need to re-install all my required packages and I hope that the configuration of those will be found.

So, my question is, what is the benefit of keeping a seperate home file if it's so hard to find the  configuration again. Will I be able to retrieve all of my old bookmarks etc.?

I've got a lot of work to get back to where I started.


I'll keep plugging away with Ubuntu but I have to say as a seasoned Window user this is hard graft and very frustrating.

I'm still in there and thanks for all the help so far.........I'll be back :)

---

