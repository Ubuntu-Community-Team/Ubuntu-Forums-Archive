---
title: "trouble in paradise"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by defenestratos on 2007-02-27
What does this message mean? I got it when i tried to update the repository list in add/remove applications;

> W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I just installed freeciv using this program and can't find it in my games folder, and when I found the executable file  

/usr/share/menu/freeciv-client-xaw3d it wouldn't open.

Could I please get some help?

---

### Post by arochester on 2007-02-27
Look at "Repository Howto" at [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

The first instruction is how to get their gpg key. Open a terminal and input it there first.

---

### Post by autocrosser on 2007-02-27
Means that it is not a "offical" site & you need the trusted key for it. You can still use the site, you just need to know that it's software "might" cause problems, break your system, other disclamers--etc,etc.

As for the installed location--try /usr/local/games or /usr/local.

---

### Post by defenestratos on 2007-02-27
> **autocrosser said:**
> Means that it is not a "offical" site & you need the trusted key for it. You can still use the site, you just need to know that it's software "might" cause problems, break your system, other disclamers--etc,etc.

As for the installed location--try /usr/local/games or /usr/local.

I know where the files are but when I activate them absolutely nothing happens. I am going to try to install again. They are in user/games

I am going to reinstall.

---

### Post by Brunellus on 2007-02-27
> **defenestratos said:**
> I know where the files are but when I activate them absolutely nothing happens. I am going to try to install again. They are in user/games

I am going to reinstall.
please clarify what you mean by "activate" and "nothing happens."  This is not worth reinstalling over.

---

### Post by defenestratos on 2007-02-28
I just meant reinstall freeciv, haha. I did it and now it goes. I think I didn't install all of the relevant packages. Before I would double click on all of the civ files in the usr/games/ directory and nothing would happen. Is that consistent with not all of the program files being present?
As you can see from the bean count I am a Noobie and am really appreciating all of the assistence I am receiving. When I am a bit more proficient I shall return the favour!

---

### Post by mcduck on 2007-02-28
use the 'which'-command to find the right executable. 'which freeciv' should tell it to you. For example 'which firefox' returns '/usr/bin/firefox'.

Anyway, most likely the executable is in /usr/bin, that's where they are in almost every case.

---

