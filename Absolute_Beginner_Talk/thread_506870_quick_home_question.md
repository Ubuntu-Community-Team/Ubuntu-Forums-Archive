---
title: "quick /home question"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by xubu_caapn on 2007-07-22
i am going to be trying a new distro in a few days, and i want to be able to translate all my settings for the new distro. could i transfer /home to an external hdd, then replace it with the one the new distro creates?

also, are firefox settings stored in /home?

---

### Post by Hossie on 2007-07-22
Yes you can. Firefox saves all personal data in your home. Use the same versions as far as possible.

---

### Post by por100pre1 on 2007-07-22
I recommend you to use Grsync. It's great for backing your home files up to an external HDD and you'll have easy access to your files at any time.

---

### Post by benx009 on 2007-07-22
> **xubu_caapn said:**
> i am going to be trying a new distro in a few days, and i want to be able to translate all my settings for the new distro. could i transfer /home to an external hdd, then replace it with the one the new distro creates?

also, are firefox settings stored in /home?

ai-ai-ai, the way you are saying this worries me, i mean, yes i guess you could copy the settings in the /home folder, but i wouldn't necessarily copy ALL of them unless you will undoubtedly run into problems.  even copying the firefox settings might pose trouble, but if it's the same version, then maybe not...

---

### Post by por100pre1 on 2007-07-22
> **benx009 said:**
> ai-ai-ai, the way you are saying this worries me, i mean, yes i guess you could copy the settings in the /home folder, but i wouldn't necessarily copy ALL of them unless you will undoubtedly run into problems.  even copying the firefox settings might pose trouble, but if it's the same version, then maybe not...

If Xubu_Caapn uses Grsync instead of those compressed backup tools many people use, there won't be many issues. The poster would be able to select which files to place in the new installation.

---

### Post by bodhi.zazen on 2007-07-22
> **xubu_caapn said:**
> i am going to be trying a new distro in a few days, and i want to be able to translate all my settings for the new distro. could i transfer /home to an external hdd, then replace it with the one the new distro creates?

also, are firefox settings stored in /home?

You can probably do this without any problem, but you might run into problems with some of the config ( . files) in /home.

Of course /home must be on it's own partition or you will overwrite it ...

IMO best to use a /data partition if you are going to share across distros.

You can link to home :

```
ln -s /media/data ~/data
```

you can call data what you like and mount it in /mnt if you do not want an icon on your desktop.

you can even 

ln -s /mnt/data/music ~/music

and on ...

---

### Post by Malibu Illusion on 2007-07-22
Lots of people are overlooking the fact you do not have to even change your current /home partition; mounting it from within your new distro will not overwrite it.  There's no reason to pull it off the drive, then replace it.  Just leave it there to begin with.

---

