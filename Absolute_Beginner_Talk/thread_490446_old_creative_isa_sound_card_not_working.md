---
title: "old creative isa sound card not working"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by simon303 on 2007-07-02
i have a very old creative sound card in an isa slot in my computer
can anyone help get it working?

---

### Post by Benbow on 2007-07-02
Does it work at all? I have an old creative audigy card (expensive in its day!) which was recognised by Ubuntu, the only problem was that it didn't produce any sound!! I removed it some time ago and now rely on the onboard sound on the motherboard.
I can only give you sympathy but I researched the problem thoroughly but failed to find a solution.
I hope someone comes up with the answer..........for both of us.

---

### Post by TrueJk7 on 2007-07-02
I'd hate to say it but Createive does not like linux at all. You may want to check out Ubuntu's old mailing lists on this. Find out what kind you have 
# lshw 
or
# lspci -v

then google against ubuntu for it "site:ubuntu.com (sound card's name)"

And see what you come up with. A little more searching never hurts. ;)

---

### Post by Raineer on 2007-07-02
I stopped being a creative customer like 4 days after I went Linux for Life, the company has their head up something dark.

That being said, if your soundcard is listed in [this]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix") list you should have a shot at it. Look for the exact model and see if there are instructions to follow.

---

### Post by simon303 on 2007-07-02
following the above advice i found
[https://help.ubuntu.com/community/forum/hardware/OldSoundCard]("https://help.ubuntu.com/community/forum/hardware/OldSoundCard")
which helped as it has a list of kernel modules for different soundcards
i then used modconf to enable:
```
snd-sb-common <common soundblaster modules>
snd-sbawe <i belive my card is in the awe series, snd-sb16 didnt work so it must be>
```
and now i have sound
(when in modconf the modules are found in kernel/sound/isa/sb)
thanks for all the help

---

### Post by hetihe on 2007-07-02
I found this: [https://help.ubuntu.com/community/DebuggingSoundProblems?highlight=%28sound%29](https://help.ubuntu.com/community/DebuggingSoundProblems?highlight=%28sound%29) very useful when cofiguring ISA sound card.

---

