---
title: "Windows Uninstall"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by RockOnward on 2007-02-26
I just learned about Linux a few days ago (total noob) and I have fallen in love with it, because Windows really iritates me.  Anyway, for the life of me, I can't figure out how to reformat my hard drive and get windows out of there!  Does anyone know where any good tutorials are for this kind of thing?  Thanks so much!

---

### Post by v8YKxgHe on 2007-02-26
> **RockOnward said:**
> I just learned about Linux a few days ago (total noob) and I have fallen in love with it, because Windows really iritates me.  Anyway, for the life of me, I can't figure out how to reformat my hard drive and get windows out of there!  Does anyone know where any good tutorials are for this kind of thing?  Thanks so much!

If you want, you could re-install Ubuntu and tell it to format the entire drive. Or, if you don't want to re-install Ubuntu you can use a program called gParted. Now I can't remember if it's installed by default, if it is then it should be in:

> System->Admin>Gnome Partition Editor 

if not, then do:

```
sudo apt-get install gparted
```

Or install gparted via Synaptic ( System->Admin->Synaptic ), which ever you prefer to use. 

Once it's installed and working, you can then open gParted and edit the partitions. I've never formated a drive via gParted, and haven't got a spare disk to test on, so I can't give you direct instructions on how to. Maybe someone else will come a long and help you with that. But at least you'll be in the right direction =)

---

### Post by Maestro23 on 2007-02-26
Edit: AlexC beat me to it.

---

### Post by bodhi.zazen on 2007-02-26
Well, if you want you can use this to wipe the drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

But you do not need to.

Just install Ubutnu and when the time comes to partition chose "use entire disk". You do not need to uninstall windows.

Install guide: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by RockOnward on 2007-02-26
Ah ha! Great!  Thanks for the help.  You better get used to seeing me here, because I'm not too tech savvy quite yet  :)

---

### Post by Brunellus on 2007-02-26
title edited.  You don't need to advertise your "noob"ness--just ask a technical question, and you'll get (hopefully) a helpful answer.  Give us information, not supplication, in the future, and stand tall & proud.

---

### Post by bodhi.zazen on 2007-02-26
> **AlexC_ said:**
> Once it's installed and working, you can then open gParted and edit the partitions. I've never formated a drive via gParted, and haven't got a spare disk to test on, so I can't give you direct instructions on how to. Maybe someone else will come a long and help you with that. But at least you'll be in the right direction =)

FYI:

1. gparted is on the Ubuntu desktop CD but is not installed with a HD install.

2. Partitions should be managed un-mounted. Thus it is better to manage them from either the ubutnu desktop CD or the gparted live CD.

3. The gparted live cd is more up to date and thus has more features and options then the Ubntu CD and is thus well worth a download.

HTH

---

