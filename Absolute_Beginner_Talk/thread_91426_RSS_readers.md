---
title: "RSS readers"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by Matt Houston on 2005-11-17
Hi

What RSS readers can I install using Synaptic? I looked into rssowl but this doesn't seem to be included, and when I downloaded the installation file it had a rpm extension which Ubuntu wouldn't recognise. 

Any recommendations?

---

### Post by rpaller on 2005-11-17
To install RPM packages you  need to convert them using a utility called Alien. How-To can be found [here]("http://www.ubuntuforums.org/showthread.php?t=90353&highlight=rpm+packages").

---

### Post by canadianwriterman on 2005-11-17
If you're using Firefox as your Internet browser, I'd recommend installing the Sage RSS reader. It's a Firefox extension and works very well, and it's integrated into Firefox.

---

### Post by Matt Houston on 2005-11-17
[QUOTE=rpaller]To install RPM packages you  need to convert them using a utility called Alien. How-To can be found [here]("http://www.ubuntuforums.org/showthread.php?t=90353&highlight=rpm+packages").[/QUOTE]

The dude in the last post says "chances are that u will have lots of dependency issues when trying to do that... hence converting a rpm to a deb with alien and then trying to install it is not always a good idea.", what are you feelings about that? How do I find out out about dependancy issues?

[QUOTE=canadianwriterman]If you're using Firefox as your Internet browser, I'd recommend installing the Sage RSS reader. It's a Firefox extension and works very well, and it's integrated into Firefox.[/QUOTE]

Yes I know thanks, prefer a separate RSS reader.

---

### Post by purdy hate machine on 2005-11-17
I always use the Integrated RSS reader in Opera but if you are looking for a separate application you could try a desklet.
There is some nice RSS eyecandy here [http://gdesklets.gnomedesktop.org/]("http://gdesklets.gnomedesktop.org/")

---

### Post by rpaller on 2005-11-17
RSSOwl is Java based. If you download the gzip'ed version and unpack it. I unpacked it into my home folder.

Launch a terminal:
```
$ cd ~/rssowl_1_2_linux_bin
$ ./run.sh
```

I am still fighting with creating a launcher for this application, but it does work when run from a terminal window.

---

### Post by doclivingston on 2005-11-17
Liferea is nice, and fairly powerful.

---

### Post by Matt Houston on 2005-11-17
is Liferea included in the depositories?

---

### Post by Darrin on 2005-11-17
Ive been using Blam. Its listed in the add applications. Now if I can only find a good rss creator app.

---

### Post by LorenzoD on 2005-11-17
Apart from Liferea, you may want to look at Blam and Straw. Personally I use Liferea, but I there are some things I really like about Straw. Too bad development seems to have stalled somewhat. If your using KDE, akregator seems to be a good choice.

Liferea is a funny application. I always feel like I need to find a better alternative, but end up going back to it simply because it's the best. I have the same issue with Gaim for instant messaging.

---

### Post by Matt Houston on 2005-11-17
Liferea looking good for the moment, thanks for help everyone.

---

### Post by Matt Houston on 2005-11-17
You know what I don't like about Liferea, when you delete an item using the delete key it doesn't automatically select the next item, but then neither do Straw or Blam.

---

### Post by Darrin on 2005-11-17
Just tried Liferea. I like it better than Blam. Im going to start using that one. Thanks.

I created feeds using [Feedforall]("http://www.feedforall.com/index.htm") in windows. (also works for macs). Is there anything like this out there for Linux? I cant find one.

---

### Post by laltopi on 2005-11-20
I like liferea too. However, the version available in the universe repo is old and buggy. Are there any repos containing the newer 1.0 RC4 version?

---

### Post by goodmanbrown on 2005-11-20
[QUOTE=laltopi]I like liferea too. However, the version available in the universe repo is old and buggy. Are there any repos containing the newer 1.0 RC4 version?[/QUOTE]

Dapper currently has 1.0RC3.  You could request a backport to Breezy in the backports forum.

---

### Post by Zerocool10482 on 2006-01-24
I don't know about all of you but Blam is cool. I've been I these forums and everyone hates Blam or doesn't know about it. What up with that.

---

