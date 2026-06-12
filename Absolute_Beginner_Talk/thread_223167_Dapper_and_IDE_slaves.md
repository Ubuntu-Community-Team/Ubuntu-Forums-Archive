---
title: "Dapper and IDE slaves"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by fjm03 on 2006-07-26
I received a hand-me-down box from my son with Dapper preinstalled. The box has only one optical drive, a Liteon SHM 165H6S. which is a popular DVD burner. The Liteon drive was configured as a slave but was the only device on IDE2. Liteon strongly recommends the drive be installed as a secoundary master.

After playing with the jumpers on the drive, I can see why the drive was set as a slave on Dapper. When the drive is configured as a  slave, both Nautilus and Disk present accurate information. When the drive is configured as a master (IDE2), both the file browser and hardware reporter begin telling tales. Nautilus adds a CD-ROM 1 which doesn't exist and Disk adds a phantom hard drive.

Also interesting was the presentation in Device Manager. DM apparently doesn't differentiate between IDE buses. Device Manager simply shows two IDE masters without reference to channel.

Is this behavior a symptom of *nix or unique to Dapper? If Dapper, is there a workaround which eliminates the reporting of phantom devices when a slave is not present on the available IDE channels?

---

### Post by Sef on 2006-07-26
> Is this behavior a symptom of *nix or unique to Dapper?

Neither.  Never heard of that problem before.  It is unique to your computer, afaik (as far as I know.)

---

### Post by OU812 on 2006-07-27
Is it a the top of the ribbon cable? Did you try jumpering to cable select?

john

---

