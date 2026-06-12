---
title: "Too many files open?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Metalslave on 2007-11-02
Okay, I'm new to Ubuntu, but I've already encountered this error three times now. When I try to move some files or just do whatever, a box pops up saying I have "too many open files". Sometimes I just get an empty box, so appearantly Thunderbird, FireFox, Rhytmbox, and a torrent of the latest episode of Dexter stressed Ubuntu out so hard, that it can't even display the text anymore...

This box should be capable of a lot more, so where do I adjust the open files limit and why is it set so low to begin with?

---

### Post by damotor on 2007-11-02
Despite the message you get I don't think it's because of the files opened, try deleting them with > sudo rm FILE

---

### Post by jaybombalous on 2007-11-02
I don't think thats your problem either, there is no limit as to how many open files u can have. If there is, then check out the room left on the disk, maybe u are over populating the system with more data then it can possible save onto physical hardware.

---

### Post by Metalslave on 2007-11-02
> **jaybombalous said:**
> I don't think thats your problem either, there is no limit as to how many open files u can have. If there is, then check out the room left on the disk, maybe u are over populating the system with more data then it can possible save onto physical hardware.

I have like a 120 gb free on the disk.

> **damotor said:**
> Despite the message you get I don't think it's because of the files opened, try deleting them with

So what does that comman do, exactly? I don't want to delete just anything.

When I last got this message, I had Thunderbird, FireFox, Rhytmplayer, and a torrent open. I was trying to access my files to check out some photos, but Ubuntu refused to display the contents of the disk, saying I had too many files open. I closed down everything, but the torrent, and tried again, but then it didn't even display the text message, just an empty box.

---

### Post by jaybombalous on 2007-11-02
what torrent client are u using? does this happen when u **aren't** using a torrent client to d/l a torrent?

---

### Post by jaybombalous on 2007-11-02
```
sudo rm FILE
```

will remove any file named 'FILE' in the directory u are at w/ root permissions. Meaning even if it was a protected system file it still would be removed.

the terminal defaults to the /home dir when first opened up. FYI

---

### Post by Scratches on 2007-11-02
> **Metalslave said:**
> Okay, I'm new to Ubuntu, but I've already encountered this error three times now. When I try to move some files or just do whatever, a box pops up saying I have "too many open files". Sometimes I just get an empty box, so appearantly Thunderbird, FireFox, Rhytmbox, and a torrent of the latest episode of Dexter stressed Ubuntu out so hard, that it can't even display the text anymore...

This box should be capable of a lot more, so where do I adjust the open files limit and why is it set so low to begin with?

It's a known problem, check out...

[http://ubuntuforums.org/showthread.php?t=592626](http://ubuntuforums.org/showthread.php?t=592626)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/158248](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/158248)

we still waiting on a solution.

Tom

---

### Post by Metalslave on 2007-11-02
Mm, that sounds like what I have here. I guess I'll just be patient and wait for a solution. Thanks, guys.

---

### Post by Boondock5 on 2007-11-07
Has any one heard anything on this yet?

---

### Post by nrune on 2007-11-27
Wanted to post a work around for this problem from the bug report in case others are looking for a solution as I was. 

  Patrick Wijnings  wrote on 2007-11-24:  (permalink)

This is related to bug #125739 (mpg123 and mpg321 won't play audio preview in Nautilus (Gutsy)). Nautilus opens a FIFO when you hover over an audio (.ogg / .mp3) file, but doesn't close it because esound isn't installed on gutsy anymore.

To work around this bug you can either disable audio previews or install pulseaudio-esound-compat (and mpg321, sox and vorbis-tools if you want nautilus to actually play sound).

You can continually monitor the number of FIFOs nautilus has opened with the following command:
```
while /bin/true; do clear; lsof -c nautilus|awk '{ print $5; }'|sort|uniq -c|grep FIFO; sleep 1; done
```

---

### Post by jflaker on 2007-11-27
> **jaybombalous said:**
> ```
sudo rm FILE
```

will remove any file named 'FILE' in the directory u are at w/ root permissions. Meaning even if it was a protected system file it still would be removed.

the terminal defaults to the /home dir when first opened up. FYI

QUOTE

---

