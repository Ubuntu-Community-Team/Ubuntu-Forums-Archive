---
title: "Thinking of Migrating to Kubuntu - - need direction."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by mlhudson on 2007-12-15
So, I'm thinking of migrating to Kubuntu. The pictures of the new KDE4 desktop are amazing and enthrolling! And, the reports seem to be that it is fast as well! My thoughts are that I should do a clean install when I do it.

But, as a NOOB, I have no idea of the things that I should make copies of or back up in order to have my info. 

I want to keep my bookmarks (opera), emails (thunderbird), addressbook stuff (thunderbird), pidgen info, & tomboynotes...

I think that's it...but, as I said, I don't even know if there are other things that I SHOULD bring over. 

So, anyone with an idea about what I should back up & how to do it, I would greatly appreciate your advice.

Matt

---

### Post by Ub1476 on 2007-12-15
What about backing up your whole /home directory? Sbackup should do the job (repos).

---

### Post by LaRoza on 2007-12-15
The easiest way, is to install it on Ubuntu. When you log in, choose "KDE" under sessions.

This installs KDE and a few other things:
```

sudo aptitude install kde-core

```

This will install everything Kubuntu has, be aware, this will give you a lot of programs you probably won't use or want.
```

sudo aptitude install kubuntu-desktop

```

Do this before a clean install.

If you do do a clean install, copy all the "dot" folders except .Trash and .Thumbnails.

If you install Opera on Kubuntu/Ubuntu, and put your old .opera directory in your home, you will have all the same things, including your history and themes.

Open home, and press Ctrl + h, you will see many files and directories. They store settings. .purple is Pidgin and the rest are usually easy to figure out.

---

### Post by skyjacker on 2007-12-15
> **mlhudson said:**
> So, I'm thinking of migrating to Kubuntu. The pictures of the new KDE4 desktop are amazing and enthrolling! And, the reports seem to be that it is fast as well! My thoughts are that I should do a clean install when I do it.

But, as a NOOB, I have no idea of the things that I should make copies of or back up in order to have my info. 

I want to keep my bookmarks (opera), emails (thunderbird), addressbook stuff (thunderbird), pidgen info, & tomboynotes...

I think that's it...but, as I said, I don't even know if there are other things that I SHOULD bring over. 

So, anyone with an idea about what I should back up & how to do it, I would greatly appreciate your advice.

Matt Be sure to back up your /home file. It saves your configurations. Keep in mind that kde4 won't be released until mid Jan.

---

### Post by JillSwift on 2007-12-15
Installing the KDE desktop alongside Gnome is a grand way to go. Both Gnome and KDE have their strengths and weaknesses, so while you're deciding which suits you best it's nice to be able to switch between them pretty much at will.

However, I have heard this can sometimes be problematic, so backing everything up is called for no matter what. (I have both and haven't experienced a problem thus far.) It's always best to back-up your /home directories with regularity anyways, so this hardly changes anything =^_^=

---

### Post by mlhudson on 2007-12-17
So many great suggestions! THANKS! I'll back up my /home directory. Then, I'm going to try LaRosa's suggestion of installing it alongside gnome. MAN I LOVE THE FOLKS IN THE FORUMS!

If I have both KDE & Gnome, will both get updated? I guess I'd need to sign in to each one to update...

Thanks again!

---

### Post by cookies on 2007-12-17
Both will update, so no worries.

---

### Post by OffAxis on 2007-12-17
KDE4 won't be out until January, and probably not in the ubuntu repositories until well after that.
3.5.8 is the current version in the repos, well worth a look in my opinion.
Just don't be disappointed that it's not v 4.

---

### Post by mlhudson on 2007-12-17
Thanks for all the info! Knowing that 4 is coming makes me want to get ready to see it. Knowing that I can put KDE on my current system is pretty exciting, too.

Thanks!
matt

---

### Post by cmnorton on 2008-04-14
Can certain menu customizations be imported from gnome into the KDE desktop? 

Edit:
-------------------------------
I should have worded this question bettter. I have customized my top gnome toolbar with applications I use all the time. 

Can I don something similar in KDE using what I have already defined in gnome?

As an aside the download did not disrupt anything, except Firefox is pointing to the Kunbuntu start page, which does not bother me at all.

---

