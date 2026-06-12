---
title: "Problem switching between two sound cards"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by dim_par on 2007-04-25
Hello,

  Since i upgraded to feisty from edgy i am facing strange sound problems. I have two sound cards.One is intel ICH6 on board and an Audigy2. They are both functioning but i cannot control them.Some applications use the first card some the second and i cannot find out why.Also ia cannot switch from one card to another through System -> Preferences -> Sound.

Any help please.

Thanks in advance

---

### Post by kpkeerthi on 2007-04-25
try command line...

List the cards you have
```

sudo asoundconf list

```

Set the default card - ICH6
```

sudo asoundconf set-default-card ICH6

```

Set the default card - Audigy2
```

sudo asoundconf set-default-card Audigy2

```

If that did not help, your best bet would be to disable the onboard card in your BIOS and use just one card. Solves a lot of sound issues.

---

### Post by dim_par on 2007-04-27
Thank you very much for your answer.It is ok now.Also i solved many strange sound probles by removing the two files .asoundrc and .asoundrc.conf.
Though i think that there should be a gui utility that gives someone the ability to select which sound card to use every time.

---

### Post by king20878 on 2007-05-01
Have a look at asoundconf-gtk.

---

