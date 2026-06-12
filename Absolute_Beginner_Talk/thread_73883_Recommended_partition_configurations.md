---
title: "Recommended partition configurations"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by aldar on 2005-10-10
For a full install (not multi-boot), what are recommendations for partition setups and why? 

By default, the install just sets up swap and 1 main partition, but I've read docs that recommend multiple partitions for mounting certain things independantly. I guess the main reason for more putting data on a different partition than / is that you can do full reinstalls with losing data?

What other partition configurations do you use and why?

---

### Post by Perfect Storm on 2005-10-10
This is what I recommend an use:

/boot
/
/home
/tmp
swap

---

### Post by brt on 2005-10-10
it can be a good idea to put /usr and /var on own partitions too.
/usr because you are able to mount it readonly (but you have to mount it writeable everytime you want to change/add/update any software)
/var because all programs use to write their logs and databases somewhere there which could "eat up" all of your free hd-space which (as far as i know) can end up very bad...

IMO on a server you should really use this, on most workstations you wont have to worry about that...

---

### Post by Kyral on 2005-10-10
I STRONGLY suggest (as in I want Ubuntu to make it default) that you have /home on a separate partition. /home stashes all your personal data so if you have to reinstall you can just keep /home as is and wham bam, all your  personal settings are preserved.

---

### Post by chettyk on 2005-10-10
I am no linux guru, but my understanding is that your partitioning scheme depends on how you use your system. As far as I can judge, the more sophisticated schemes are when the system has to support multiple users or is running as a server.

I use my Ubuntu box purely as a single-user workstation. So I need just three partitions: /, swap, and /home. I endorse Kyral's suggestion that you put /home on a separate partition so that you can reinstall without losing settings or your work files.

---

### Post by aldar on 2005-10-15
So if I do want to do the 3 partition config (/, /home, and swap), how much space do I want to give to / and /home? I give swap 1gb, but what to do with the remaining 159gb? or I guess I just need to know how much space / needs and the rest will go to /home.

---

### Post by Leigh on 2005-10-16
Just as an add-on to aldar's question, I would like to do the same three-partition set up, but I have already installed Breezy. Can I repartiton with Breezy running or would it be easier to re-install and do it from scratch? I'm not averse to re-installing as I could do with the experience.

---

### Post by ~J~ on 2005-10-16
[QUOTE=Kyral]I STRONGLY suggest (as in I want Ubuntu to make it default) that you have /home on a separate partition. /home stashes all your personal data so if you have to reinstall you can just keep /home as is and wham bam, all your  personal settings are preserved.[/QUOTE]

Fantastic idea!

I do something similar on my Windows partition (have "My Documents" mapped to a seperate hard drive) and I was wondering how this could be done in Linux.

Not only have you shown me, but you've also allowed me to learn something new.

Many thanks for that...

---

### Post by az on 2005-10-16
Keeping everythying on one partition is easier to handle and backing up your home partition, or any other data, is just as easy.  Keeping everything on one partition on a desktop system avoids a lot of problems such as running out of space...

---

