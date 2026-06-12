---
title: "Programs not Running!"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-29
Hello!

I upgraded to Edgy not too long ago, and I recently found that Frostwire was not running in it.

Well, I searched the forums a bit, and I found this one [http://www.ubuntuforums.org/showthread.php?t=278688&highlight=frostwire+-working+edgy]("http://www.ubuntuforums.org/showthread.php?t=278688&highlight=frostwire+-working+edgy"),
which one member suggested using this code:

```
sudo ln -sf /bin/bash /bin/sh
```

which has in turn, caused a ton of my programs to not run!

Anyone have any advice, I'm really needing it!

Thank you!

---

### Post by blendmaster on 2006-10-29
In case it helps, here's the error I get when running pretty much any program:

```
Could not launch menu item

Failed to execute child process "<program>" (Too many levels of symbolic links)
```

Yeah, this is looking pretty bad at the moment.

---

### Post by blendmaster on 2006-10-29
Basically, does anyone know how to reverse the ln command?

I think that would solve this...

---

### Post by moshuptrail on 2006-10-29
The command you used creates a symbolic link file called bash in /bin.  The link will cause it to run /bin/sh instead of bash.  On my system, /bin/sh is a link pointing to /bin/bash!  hmmm.  (That's why it's saying too many links - it's looping)  On my system bash is an executable in /bin about 860k.  I'm guessing that unless you renamed bash first you over-wrote yours with the link file, so you need to replace bash.  That will at least get you back to where you started.

---

### Post by blendmaster on 2006-10-29
Any idea on where I can get a new one?

I didn't make a backup (I didn't think I needed one) so I guess I'll have to download it, right?

Thanks for your advice!

---

### Post by blendmaster on 2006-10-29
The bash files properties say it's of type link (broken), with a link target of /bin/sh, if this will help further.

Attempts to open the file result in a dialog saying that the file should be moved to the trash.

---

### Post by moshuptrail on 2006-10-29
bash is your command line shell.  I have a hunch you are going to have a lot of things that don't run.  Ideally just grab a copy from someone else.  I don't know if you can get it with apt-get.  Simply copying the file to your /bin folder might be a problem since the cp command requires... you guessed it, bash.

---

### Post by blendmaster on 2006-10-29
Yeah, I downloaded the tar.gz from the official site, but I cannot unpack it as the same error as above comes up. Anyone have any idea on how I should fix this!

By the way, thank you moshuptrail, you've been of great help to me!

---

### Post by blendmaster on 2006-10-29
This isn't good!

I just realized I can't launch firefox, the only way I'm typing this is because it was open before this ever started! Am I gonna have to do a clean install, because I don't think I can do anything?

---

### Post by moshuptrail on 2006-10-29
Anything that requires terminal, or command line will not work.  Can you use your browser and get to your email?  Could you do a save-as on an attachment?
If so, check your personal email on this site.  I left you a message.

---

### Post by blendmaster on 2006-10-29
Okay, yeah my browser still works (luckily, I didn't accidentally close it, as I can't open any new windows).

Message sent!

---

### Post by bsussman on 2006-10-29
deleted

---

### Post by blendmaster on 2006-10-29
How would I change /bin permissions without opening the terminal?

The terminal won't open now.

Any Graphical way to destroy root temporarily?

---

### Post by moshuptrail on 2006-10-30
I never had this problem before, and I sure as heck am not going to simulate it.  Frankly I think you may end up re-installing Ubuntu.
But, before you go there, can you open a file browser?  Can you open ANY windows?  How about System / Administration / Users and Groups?

I looked around for an alternate shell and I don't think there is one - at least not installed.  But if anyone else is following this thread - do you know of a way to replace bash?  I went to Users and Groups and looked at the setup for a user to see what shells would show in the drop-down.  The shells shown are /bin/bash, /bin/rbash, and /bin/sh.  All are just links pointing to bash.  Crap!

Unless you can do it from a window and the window doesn't invoke a script behind the scenes you are SOL.

---

### Post by moshuptrail on 2006-10-30
Okay, I just had a brain storm.  How about inserting the Live CD and then copy bash from the Live CD to your /bin folder?  The live CD will have a running copy of bash and you'll be able to start a terminal, etc.
I don't remember if the Live CD mounts existing file systems.  That would help.

---

### Post by blendmaster on 2006-10-30
Hello!

Yesterday, I was thinking about all of this, and I couldn't really think of a way to fix this problem. I was thinking about going with a live CD, but I didn't have one at hand, and had to download it anyway. I figured that if I could restart the system, I would try some more to fix this problem, but restarting it brought it to the same loop, and as such, was a no go. Well, after downloading it, I decided to reinstall Ubuntu completely, as I had the CD, and thought my system wouldn't be able to recover, even if I did fix this mess.

Well, I got it reinstalled, and am quite happy with it! However, there is no way I can thank you enough moshuptrail, for all of the help that you have given me. I can't think of **anyone** that would have even attempted to get me through that mess!

Also, while I'm still on it, I think the next release should include some sort of backup terminal, or force sudo (don't know how that would work) to get people like me out of these messes. I think that it's something that's desperately needed for users who like to explore their system.

Oh well. Again I thank you very much, and I hope no one else ever uses that command, or gets into any mess like this!

---

