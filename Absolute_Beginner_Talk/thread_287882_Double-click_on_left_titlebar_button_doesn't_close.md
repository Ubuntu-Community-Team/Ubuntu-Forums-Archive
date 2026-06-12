---
title: "Double-click on left titlebar button doesn't close window"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by tatare99 on 2006-10-29
I was looking like... forever, for a tip on how to close Ubuntu/Gnome/Metacity windows by double clicking on the menu (located on the top left corner of the window).

I finally found one: [http://marnanel.livejournal.com/863405.html](http://marnanel.livejournal.com/863405.html)

So... there **IS** a Metacity patch to my problem:
[http://bugzilla.gnome.org/attachment.cgi?id=67516&action=diff&headers=0](http://bugzilla.gnome.org/attachment.cgi?id=67516&action=diff&headers=0)
[http://bugzilla.gnome.org/attachment.cgi?id=67516](http://bugzilla.gnome.org/attachment.cgi?id=67516)
[http://bugzilla.gnome.org/attachment.cgi?id=70345](http://bugzilla.gnome.org/attachment.cgi?id=70345)
[http://bugzilla.gnome.org/show_bug.cgi?id=83892](http://bugzilla.gnome.org/show_bug.cgi?id=83892)

Does anybody know how I can apply this patch to my Ubuntu Dapper ??

Thanks so much in advance for the great answers I'm sure you guys will write !

---

### Post by Toxicity999 on 2006-10-29
Well you would have to compile metacity, applying that patch beforehand. But for someone new to the scene this could lead to problems. Say your compile messes up but still actually compiles, or you think it compiles, you uninstall the current metcity only to find the new one didn't take.

In either case you would be left with no window borders =/

If you have a modern-ish computer you may want to look into Beryl (3D Desktop environment.) There is a setting to close window on titlebar double click.

---

### Post by tatare99 on 2006-10-29
Does somebody know by chance how or where I can read something that teaches me how to re-compile Metacity whith this patch ? I already have Beryl actually... but I'd prefer to be able to close my windows by double clicking on the icon located on the top left corner.

Thanks!

---

### Post by mahy on 2006-10-29
> **tatare99 said:**
> Does somebody know by chance how or where I can read something that teaches me how to re-compile Metacity whith this patch ? I already have Beryl actually... but I'd prefer to be able to close my windows by double clicking on the icon located on the top left corner.

Thanks!

If you use Beryl, why you wanna compile Metacity with patches? Beryl replaces Metacity, so it won't be any help.

---

### Post by tatare99 on 2006-10-29
well... I installed Beryl but I still use Metacity... Right now, I use Beryl just to show other people how cool the Linux Desktop can be.
But for me, as my computer is not very powerful, I prefer to use Metacity.
That's why I'd love to 'install' this patch.

---

### Post by tatare99 on 2006-10-29
Maybe it will help if I posted on another forum ?
I'd love to learn how to compile Metacity...

---

### Post by Toxicity999 on 2006-10-29
Well it wouldn't be too difficult, try the metacity site for specific instructions or at a bare minimum a list of Reqs. Then just read up on the patch command. after that it's basically cd to the source dir make, sudo make install. But like I said look there for more specific info.

---

