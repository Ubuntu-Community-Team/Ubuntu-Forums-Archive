---
title: "Software index is broken, etc"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by Skychrono on 2006-05-31
...when I try to run the update thing. So, I run Synaptic like it suggests. I have one broken package - "vim."

Description: <insert up to 80 chars description>

Whatever vim is, it seems that, yes, it's installed wrong. So I try upgrading it.

```
E: /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb: trying to overwrite `/usr/bin/xxd', which is also in package vim-common
```

Erm?

If I mark it for removal, it threathens to remove ubuntu-base and ubuntu-minimal. I presume this would be bad.

What do I do?

---

### Post by deja2004 on 2006-05-31
I'm not wholly sure if this will solve your problem, but I doubt that it will hurt. Try running this:
```
sudo apt-get update -f
```

---

### Post by Skychrono on 2006-05-31
> W: GPG error: [http://users.lichtsnel.nl](http://users.lichtsnel.nl) breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems


Still can't run the update utility...

---

### Post by mostwanted on 2006-05-31
Well, why are you using that unofficial repository anyway?

---

### Post by Skychrono on 2006-05-31
Not purposely! I didn't know I was until you just told me - I only just read your guide and found out how to add new repositories anyway.

So. A fix... do I need to reinstall? It wouldn't be so bad, truthfully, but avoiding it would be best.

Edit: How WAS I using an unofficial one, anyway? Where'd it come from?

---

### Post by Jagot on 2006-05-31
Use this guide to change your repositories back to the proper ones.  You should need to reinstall:

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

When you've changed that do and suo apt-get update and upgrade to make sure everything is ok.

---

### Post by mostwanted on 2006-05-31
[QUOTE=Skychrono]Not purposely! I didn't know I was until you just told me - I only just read your guide and found out how to add new repositories anyway.

So. A fix... do I need to reinstall? It wouldn't be so bad, truthfully, but avoiding it would be best.

Edit: How WAS I using an unofficial one, anyway? Where'd it come from?[/QUOTE]

You must have added it unconsciously or something :)

You can just remove the URL from /etc/apt/sources.list (open it with sudo gedit /etc/apt/sources.list ) and it shouldn't complain.

Do a fresh install anyway. If you're not running Dapper already, do so :) it's out tomorrow.

---

### Post by Skychrono on 2006-05-31
[QUOTE=mostwanted]You must have added it unconsciously or something :)

You can just remove the URL from /etc/apt/sources.list (open it with sudo gedit /etc/apt/sources.list ) and it shouldn't complain.

Do a fresh install anyway. If you're not running Dapper already, do so :) it's out tomorrow.[/QUOTE]

I am. But I guess the new release will be more stable...?

I'll probably fdisk the areas and start over with the new Dapper.

---

