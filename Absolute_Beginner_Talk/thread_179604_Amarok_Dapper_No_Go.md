---
title: "Amarok Dapper No Go"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by richbarna on 2006-05-20
Hi all,
Just upgraded to dapper, all fine except for Amarok.(just skips through mp3's and wma music files)
I did all these :-
[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

I installed Amarok 1.3 and then tried Amarok 1.4a
I installed aRts and Xine engines.

I have sound because I hear the system sounds and Kaffeine plays all videos.

I did see this thread by the way :-
[http://www.ubuntuforums.org/showthread.php?t=26308&highlight=Dapper]("http://www.ubuntuforums.org/showthread.php?t=26308&highlight=Dapper")

Has anyone else had a problem with Amarok?
And if so, could you tell me if I have overlooked something?

Thanks in advance.

---

### Post by mostwanted on 2006-05-20
The restricted codecs in xine have been moved to the package libxine-extracodecs in Dapper. You need to install that.

---

### Post by richbarna on 2006-05-20
[QUOTE=mostwanted]The restricted codecs in xine have been moved to the package libxine-extracodecs in Dapper. You need to install that.[/QUOTE]

I tied it and got this message :-
> ********@dhcppc0:~$ sudo apt-get install libxine-extracodecs
Reading package lists... Done
Building dependency tree... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate


I've got all repositories allowed including backports

---

### Post by mostwanted on 2006-05-20
[QUOTE=richbarna]I tied it and got this message :-


I've got all repositories allowed including backports[/QUOTE]

it's in multiverse. Try changing your repository locale if that's the problem.

---

### Post by richbarna on 2006-05-20
Just installed xmms and it works !!
So it's definitely an Amarok problem.

---

### Post by mostwanted on 2006-05-20
[QUOTE=richbarna]Just installed xmms and it works !!
So it's definitely an Amarok problem.[/QUOTE]

No, it's *not* "definitely an Amarok problem". It's a libxine-extracodecs problem. You need to install libxine-extracodecs; XMMS doesn't use xine for playback, so it's not affected by libxine-extracodecs not being there...

**Steps to make it work:**

1) Check if you actually do have multiverse enabled

2) Reload your sources

3) Remove all locale traces from the URLs in your sources list (for Americans it's the "us." part in every URL, for Spaniards it's probably called "es.") and reload.

libxine-extracodecs is what gives you playback of restricted formats in Amarok on Dapper. I'm not giving you completely useless advice you know, so don't discard it the second something doesn't go right.

---

### Post by henriquemaia on 2006-05-20
Running Dapper amd64.

I installed the new version after adding the repository line to my sources.list. It didn't work, and I get the message:

```
henriquemaia@pc2:~$ amarok
amarok: error while loading shared libraries: libkdecore.4: cannot open shared object file: No such file or directory
```

No big problem, though. Just unistalled and reverted the the previous version (the one in ubuntu repositories). 

Just a warning for someone trying this upgrade.

---

### Post by henriquemaia on 2006-05-20
Oh, oh, wrong thread. My appologies. Sorry for this.

ps: the thread I intended to post is this one: [http://ubuntuforums.org/showthread.php?t=179532](http://ubuntuforums.org/showthread.php?t=179532)
It's already posted there.

---

