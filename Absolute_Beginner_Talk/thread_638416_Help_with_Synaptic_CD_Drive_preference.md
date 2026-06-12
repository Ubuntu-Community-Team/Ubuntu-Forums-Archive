---
title: "Help with Synaptic CD Drive preference"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by fulllefty on 2007-12-12
Sorry for my bad English. I'm not a native speaker
Chronology:
1My computer have 1 CD-ROM drive & 1 DVD-Writer.
2. I am installing Ubuntu Feisty(Live CD)to my HD from my CD-ROM drive
3. When I'm trying to add Repo DVD in Synaptic Package Manager (menu Edit>Add CD-ROM) synaptic keep trying to detect the CD/DVD in my CD-ROM, not the DVD-Writer one.

The question is, can I change the preferences for Synaptic to detect CD/DVD on my DVD-Writer?

Thank's Before for all of your answer.

---

### Post by dcstar on 2007-12-12
> **fulllefty said:**
> Sorry for my bad English. I'm not a native speaker
Chronology:
1My computer have 1 CD-ROM drive & 1 DVD-Writer.
2. I am installing Ubuntu Feisty(Live CD)to my HD from my CD-ROM drive
3. When I'm trying to add Repo DVD in Synaptic Package Manager (menu Edit>Add CD-ROM) synaptic keep trying to detect the CD/DVD in my CD-ROM, not the DVD-Writer one.

The question is, can I change the preferences for Synaptic to detect CD/DVD on my DVD-Writer?

Thank's Before for all of your answer.

In your /dev directory you will probably find a file called "cdrom", this will be a link to your CD drive and it is probably what Synaptic defaults to.

You may have to manually change it to point to the DVD drive with the following commands (in a terminal):

```
sudo rm /dev/cdrom
sudo ln -s /dev/dvd /dev/cdrom
```

Be aware that this will cause all programs to default to your DVD drive for CD use.

---

