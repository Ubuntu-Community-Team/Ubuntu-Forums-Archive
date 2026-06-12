---
title: "Lost Firefox's bookmarks."
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by fidolip on 2007-03-11
Funny (ekhm..) thing happened today - I was playing music through Amarok player and I told my computer to go into 'standby' mode without either stopping or pausing the music (i.e. it was still playing). After I came back from work I turned the computer on again and found it working on the highest freqency possible (1.6GHz - it's laptop, so normally it runs on 600MHz) and the Amarok was frozen. The 'top' command showed that most of the CPU usage is taken by the Amarok. I couldn't reboot it normally (when I tried the whole system froze) so I went the 'harsh way', i.e. kept the power button pressed for some time until it turned off. After turning it on again there was some trouble with filesystem and I had to do 'fsck' and press 'y' few times (some troubles with inodes, mostly connected to Amarok as far as I can tell). After that I rebooted it normally and everything ran smoothly. Or so I thought - when I opened Firefox it came out that all my bookmarks are missing. History and other stuff (like the fact that I was already logged in to this forum when I entered the main site) seem to be inact.

Now three questions:
1. Why did it happen?
2. Is it possible to recover my bookmarks? It's nothing of a great importance, but still - would be nice to have them back..
3. In case of this happening again - is it possible to kill a single process (like 'amarokapp') from the terminal? I tried 'kill amarok' and 'kill amarokapp', but then it says that kill can take only 'process ir job's ID'. I know I can always run the system monitor and try from there, but somehow I trust command line more.;-)

Cheers!

---

### Post by astrolabio on 2007-03-11
Look this is a problem that happened to me often.

To recover your bookmark just go in 
~/.mozilla/firefox
then there must be a folder with a funny name (a bunche of random letter and numbers). Get in there too.
Inside it there's a folder named bookmarkbackups. You can guess what it does contain :)

You can import it in firefox using the bookmark manager.
Firefox/Bookmarks/Organize Bookmarks.../File/Import.../From file
and giving him the path to that file.

To kill processes in a terminal is very easy
killall name
or you can use 
ps -e
to get the list of all processes with their PID (Process ID)
and then use that number to kill it
kill PID
(i.e. kill 2345)

If it really don't want to die you can try the famous
kill -9 PID

Thers is even a song about it 
[http://www.monzy.com/intro/killdashnine_lyrics.html](http://www.monzy.com/intro/killdashnine_lyrics.html)

Another way is using top
just use top
then press k
and write the PID

---

### Post by aidanr on 2007-03-11
1. don't know, i don't have a lappy or use suspend

2. firefox backs up your bookmarks in ~/.mozilla/firefox/profile.default/bookmarkbackups

3. if you absolutely have to do a hard reboot, [this]("http://en.wikipedia.org/wiki/Magic_SysRq_key") is the correct way

edit:// i'm too slow today :)

---

### Post by fidolip on 2007-03-11
Cool! Thx, it worked.:-)

As for using PID - tried it once and it rebooted my whole system.:D And this 'killall' - the command is a little misleading, wouldn't you say?;-)

Anyways, I'm happy I have my bookmarks back and I learned sth new. Thank you again!

---

### Post by fidolip on 2007-03-11
aidanr: A'propos no. 3 - thx for the link! I didn't know such a thing existed. But that's something I got used to during my short time with Linux.;-)

---

