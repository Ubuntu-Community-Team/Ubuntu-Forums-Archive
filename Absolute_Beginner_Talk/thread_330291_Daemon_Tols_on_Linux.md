---
title: "Daemon Tols on Linux?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by coolboarderguy on 2007-01-02
Hi All,

I have some .nrg files on cd that I open using daemon tools under xp and wanted to know if something similiar exists under linux. I really would like to avoid having to boot into xp just for this. Is there something out there? I installed the daemon tool via apt-get but get the feeling that it is different to the daemon tool app under windows. Have I missed something?

---

### Post by qyot27 on 2007-01-02
I found this:
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/499696.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/499696.html)

In which it says that such images can be mounted by using
```
mount -o loop,offset=307200 image.nrg /wheretomount
```

But I've not done this myself (and can't test it at the moment), so I'm sure someone will come along and confirm or disprove this.

---

### Post by tenn on 2007-01-02
One easy solution I use is IsoBuster it works great in wine and is really good for image files and recovering files from hard to read DVD's or CD's

---

### Post by crimesaucer on 2007-01-02
I have a similar question about kvcd movies. On Xp I used to play them with Daemon tools by mounting the image in a virtual drive and playing it with Media Player.

Can these movies be played on xubuntu. Do I need a certain codec for it to be played on the ubuntu media players, or a tool like Daemon Tools for Xp?

---

### Post by tenn on 2007-01-02
I recently used IsoBuster with a kvcd to extract the the DAT file from the bin image you can than just change the file extension to .mpg
and play it like normal.
There is probably other ways but it works.

---

### Post by 3rdalbum on 2007-01-02
.nrg files seem to just be ISOs, so you can mount them with the following thingy:

```

sudo mkdir /media/iso
sudo mount -o loop image.nrg /media/iso

```

Unmounting is easy:
```
sudo umount /media/iso
```

If the .nrg file doesn't mount directly, you can try getting nrgtoiso from the repositories, and converting the file to an ISO.

---

### Post by crimesaucer on 2007-01-02
Thanks tenn, I try that.

---

