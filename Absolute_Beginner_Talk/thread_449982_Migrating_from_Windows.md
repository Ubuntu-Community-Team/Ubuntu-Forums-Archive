---
title: "Migrating from Windows"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by jlp09550 on 2007-05-20
Hello there.

I have a Ubuntu Free CD I got just last week. Today, I finally decided to convert my Windows to Ubuntu. I have a big knowledge of Ubuntu, but have one problem.. migrating users/settings/documents from Windows to Ubuntu.

When I am in the setup area, it does not even give me any sign of a Windows setup. I have one, in fact, setup in another partition, but it seems to not be able to find it.

Can someone help me?

Thanks.

---

### Post by aysiu on 2007-05-20
So you're saying you never see this part of [the installation process?](http://www.psychocats.net/ubuntu/installing)

---

### Post by starcraft.man on 2007-05-20
> **jlp09550 said:**
> Hello there.

I have a Ubuntu Free CD I got just last week. Today, I finally decided to convert my Windows to Ubuntu. I have a big knowledge of Ubuntu, but have one problem.. migrating users/settings/documents from Windows to Ubuntu.

When I am in the setup area, it does not even give me any sign of a Windows setup. I have one, in fact, setup in another partition, but it seems to not be able to find it.

Can someone help me?

Thanks.

Hmmm, are you using the migration assistant on the live cd right? It isn't full proof by any means, if I were you I would manually back up any data that was really important (maybe even in the process put your config files like thunderbird box and firefox bookmarks in a folder) to make sure you didn't lose it (to external drive/or CD/DVD). If the assistant isn't working I guess the easiest way is to make a dual boot and then you can mount your windows drive and copy over all the data you want and then poof, wipe out the XP partition once your done using [gparted live cd]("http://gparted.sourceforge.net/livecd.php"), don't recommend doing it in Ubuntu, live cd is easiest.

Someone else may have a manual fix for you to get the partition detected, I haven't used the assistant though so can't say I'm fully up to speed on how it works.

Hope ya get it all working. :)

Edit: HA! Aysiu with the cat like reflexes, leaping into action :D. I should prolly read up on that section, though I do keep using alternate disks too...

---

### Post by jlp09550 on 2007-05-20
I do get the screen.. but it just won't detect my installation.

[Click here ]("http://img526.imageshack.us/img526/8075/screenshotbf2.png")for a screenshot.

Does it like not work on Windows XP Pro?

---

### Post by aysiu on 2007-05-20
I don't know if it's an XP Pro thing. That's weird.

---

### Post by starcraft.man on 2007-05-20
Thats very weird... I don't think there are that noticeable a difference between pro and home... Its far more apparent in the n versions of vista.

Oh well, go with what I posted. A dual boot is easy and you can set it up automatically. Just make a root and swap directory (home too if you want) and then GRUB should detect XP and set up a dual boot. If GRUB doesn't detect it, like the migration assistant, then just mount it manually. There is a section for that in Ubuntuguide, in my sig.

That should be it, hope it all goes well. You can use a gparted live cd after to rearrange your partitions.

Have a good time with Ubuntu :).

---

### Post by freebird54 on 2007-05-20
When I added a Feisty test setup to my system, it definitely detected and moved everything over - from both XP Pro AND from an Edgy install as well.  I concur with the dual-boot solution for now though - I guess it doesn't ALWAYS catch everything!

---

