---
title: "I broke it with one command. BROKE, I tell ye"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by cogenthack on 2007-06-10
I was installing a perl extension pacpl ( audio encoding ), and the directory structure *looked* like it belonged in the root folder so I executed the command
```
sudo tar -xzvf pacpl /
```
which I thought would - oh, I dunno I'm a noob, but it *seemed* like a good idea at the time.
Anyway it broke everything instantly, and the cdr drive is throwing a wobbly, so I can't even do a fresh install. The load screen works but it changes to a terminal for user/pass. The only message I get when the thing boots is:
```
can not cd to /home/[USERNAME]/
```
I don't understand either what I did wrong, or what keywords I need to use to look the solution up. Could someone give me some pointers?

---

### Post by Rocket2DMn on 2007-06-10
Those seem to have nothing in common, is there anything else AT ALL that you did like run updates at any point or install/reconfigure anything?

---

### Post by cogenthack on 2007-06-10
When I said it broke instantly, it really did, the moment I executed that command, the icons on the desktop screwed up, some replaced with red crosses, no commands worked - I panicked and reset the computer, thinking that might help. Previous to that I had installed the script (pacpl-install) on top of perl ( including the libogg-dev for headers and suchlike ) and was trying to figure out the easiest way to get pacpl (perl script) into PATH, which is what lead me to the above.

---

### Post by Rocket2DMn on 2007-06-10
That is strange, I've never heard of a problem quite like that.  Have you tried booting with Recovery mode (the second option in GRUB) or with an older kernel?

It is possible that by extracting to the root of the filesystem you overwrote something or other which has resulted in the problems you are experiencing.

---

### Post by cogenthack on 2007-06-10
Recovery mode appears to work, I went in and deleted every thing that I determined had been written by the command. I've just looked over the directory structure and there doesn't appear to be anything that would cause conflicts. The response you just gave was my initial response, but there doesn't seem to be any overlap. [here]("https://sourceforge.net/project/showfiles.php?group_id=139264") is the page for the package (i686). Perhaps you could cast your eye over it?

---

### Post by HotShotDJ on 2007-06-10
So... let me get this straight... you ran a command using "sudo" without having any clue what it was you were doing because "it seemed like a good idea at the time" ????   Did you read any HowTo's or README files to find out what actually WOULD be a good idea?  And what does "the cdr drive is throwing a wobbly" mean?  How, exactly could what you did have anything to do with a malfunctioning cdr drive?

As Rocket2DMn said, it is likely that you over-wrote some critical files -- you're best bet is to do a complete reinstall.  If your cdr drive is broken, you'll have to buy a new one.  And in the future, DON'T run commands using "sudo" unless you know what you're doing.

---

### Post by Rocket2DMn on 2007-06-10
ok ok, let's calm down a little bit, he did say he was a noob.  Heck, I'm still somewhat of a noob, esp. with Ubuntu.  Besides, we are all new at some point and have been there, done that.

Back on topic, a reinstall might be necessary, but I don't think we should rush to that quite yet.  Have you googled the problem, perhaps you can find somebody else who has had issues with this package.  And yeah, what do you mean exactly by your cdr is "wobbly"?

---

### Post by cogenthack on 2007-06-10
many thanks for your complete lack of understanding, and especially for your overbearing manner

---

### Post by shamushand on 2007-06-10
I think that's what happened - it overwrote critical system files. This happened to me once, i was trying to install something that conflicted with libc6, so I was trying to install an older version of it, I typed in: 

```
sudo dpkg -r --force-depends libc6
```

Do NOT try this at home...

As soon as the command was finished, I tried to install the older package, but then nothing would open, and the terminal became non-responsive. After reinstalling the system, I learned my lesson -  sudo, it has to power to give and to take away.

And now, a few sidenotes:

Sudo, with great power comes great responsibility.
Sudo, drink responsibly. (I couldn't resist) :D

Sorry you had to learn your lesson the way I learned mine. ;)

---

### Post by cogenthack on 2007-06-10
"throwing a wobbly" is parlance for "not working", sorry if that wasn't clear. The trouble with googling it is that I don't have enough of a handle on the problem to sufficiently describe it. Can/does 'tar' change the permissions on folders that already exist?

---

### Post by Rocket2DMn on 2007-06-10
Not gonna lie, that sucks.  But how did you fix the problem, shamushand, did you have to reinstall?  There should be a repair option when loading from the Ubuntu cd, but I've never seen or used it.

---

### Post by shamushand on 2007-06-10
All the repair does in reconfigure something then dump you on a command line.
Turns out everything in Ubuntu depends on libc6, even the command line. 
So yeah, I had to reinstall. But no biggie, this was on an old test machine.

---

### Post by HotShotDJ on 2007-06-10
> **Rocket2DMn said:**
> ok ok, let's calm down a little bit, he did say he was a noob. Yes, yes... of course... a noobie.  And yes, many years ago, I was one too.  I suppose my comment could be interpreted as overly critical -- that was not the intent.  But I DO think that cogenthack should write 100 times on the blackboard "I will not run commands with sudo without reading the manual" and then let this be an important learning experience.

However, I stand by my comment about "throwing a wobbly."  That phrase is not useful to help diagnose his problem.  I'm STILL not sure what it even means... I can only surmise that it is somehow not working (??).

---

### Post by shamushand on 2007-06-10
HotShotDJ, I think he basically means the CD drive croaked. ;)

---

### Post by cogenthack on 2007-08-17
](*,)
the fix was:
```
chmod 755 /
```

---

