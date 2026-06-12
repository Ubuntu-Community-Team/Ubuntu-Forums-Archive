---
title: "firefox 2.0 from package manager?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by anagnost68 on 2007-06-06
My package manager gui says the latest version of firefox is 1.0.7, I think this hasn't changed since I installed Ubuntu (breezy).  How can I use the package manager to get the latest version?

Thanks

---

### Post by Ek0nomik on 2007-06-06
```
sudo apt-get update
```

Then try to search.

---

### Post by Lord Illidan on 2007-06-06
Breezy is quite old...perhaps you should consider Feisty or in the least, Dapper?

---

### Post by starcraft.man on 2007-06-06
> **anagnost68 said:**
> My package manager gui says the latest version of firefox is 1.0.7, I think this hasn't changed since I installed Ubuntu (breezy).  How can I use the package manager to get the latest version?

Thanks

Ummm, do you mean you are still using Breezy? That version is [no longer supported.]("http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution)#List_of_releases")

I'd highly recommend upgrading to Dapper LTS or Feisty. Its up to you though.

---

### Post by louieb on 2007-06-06
i'm running  dapper on one pc got the latest Firefox on it by going to the phychocats link in signature.   look for latest Firefox page there.

---

### Post by alienexplorers on 2007-06-06
I just get the package from mozilla and untar it into my /home directory.  I then setup a new profile start firefox and away I go with the most current distro.  I also do the same thing with thunderbird, so I always have the latest distro.

---

### Post by anagnost68 on 2007-06-07
Could you elaborate a little bit on how to make a new profile?

Also, is there a way to upgrade from Breezy without installing the latest version from scratch.   What's the procedure and is it reliable?

Thanks

---

### Post by Haus Neuerburg on 2007-06-08
> **alienexplorers said:**
> I just get the package from mozilla and untar it into my /home directory.  I then setup a new profile start firefox and away I go with the most current distro.  I also do the same thing with thunderbird, so I always have the latest distro.

That is, I think what I did, too but I do still have FF1.5 hidden somewhere: how do I eliminate that? Does any one know? If I open FF directly I get FF2.0.0.3 but if the browser hasn't been opened yet and I open e.g. a system-help I get FF1.5. How do I get rid of it?
Rgds Haus Neuerburg

---

### Post by diatribe on 2007-06-08
you can run:

sudo update-manager -c -d

and that will update to the next version for you

---

### Post by madmetal on 2007-06-08
> **anagnost68 said:**
> My package manager gui says the latest version of firefox is 1.0.7, I think this hasn't changed since I installed Ubuntu (breezy).  How can I use the package manager to get the latest version?

Thanks

wow :) a breezy user.. nice to hear older versions are still alive..
if you are satisfied with your system and dont want to risk an update to feisty or dapper then only get the source of firefox from the official site and manually install it...
although since breezy is not supported anymore its better to upgrade to feisty or dapper...

---

### Post by Haus Neuerburg on 2007-06-08
@diatribe: thnx, I did that but the system answer I got was: your system is up to date and nothing was changed. I think that if I hit the help of any programme that the paths there are still connectd to the older version, cud that be?

---

### Post by NoobieDoobieDo on 2007-07-06
I'm on Dapper and I'm stuck on firefox 1.5 (!).

apt-get update
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

They really should fix that.

I guess I'll have to install manually.

---

