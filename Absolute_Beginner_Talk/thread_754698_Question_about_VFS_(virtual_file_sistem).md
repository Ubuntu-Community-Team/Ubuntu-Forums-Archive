---
title: "Question about VFS (virtual file sistem?)"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Ryuki_NdranC on 2008-04-14
Ok... i have installed ubuntu gusty on a AMD64 HP laptop, all working good. But i have one question:

I followed some magazine advice (also seen in this forum) about mounting ubuntu like this:

if 80 gb HDD

5gb - 8gb   =   EXT3   =   Mount point: /

70gb   =   EXT3   =   Mount point: /home

(rest)gb   =   SWAP   =   null xD

anyway... i followed that advice and now im starting to notice (or at least what my almost null knowledge of linux VFS let me) that all the repositories programs i have installed are in the "/" instead of /home/ryuki...

I notice this because in soooo many howto i have to put x file in ~/.program_name/subfolder, the problem is, even there is a .program_name folder inside is almost empty or totally empty, and then digging a little (whereis program_name) i found out that the program is installed (apparently... can't tell <.< d@mm windows) in /usr/local/shared.

So my question is: am i doing something wrong? it was stupid to separate /home in another partition? its all alright and I'm just being paranoid?

thx in advance

---

### Post by talsemgeest on 2008-04-14
You just need to get the balance right. Leave as much space in the / directory for your programs and keep enough in ~/home for your needs.

Hope this helps :)

---

### Post by AdamG51172 on 2008-04-14
This is what I do actually, except I have two other OS as well, and swap is only 1.5 times my RAM capacity.  /home/(your user name) contains hidden folders with the configuration files, saves, etc.  You can find them by going to your home folder clicking "view" in the menu, and "show hidden files"

The best use for having /home on a separate partition, I've found, is that I can do a fresh install and still use my old home partition, so I don't lose any of my files.   I still have to re-install some applications, but when I do, they are just as I left them.

The reason that the other programs have you install into your home partition is that they are not usually included with the repositories.

---

### Post by Ryuki_NdranC on 2008-04-14
So i should add more space from my /home partition to my / partition? :( The way i understood it was that all the non-system programs were going to install into /home/(user)

:| I guess i will add a couple more GB. I currently have 7gb on "/" and 70gb on "/home", i usually download a lot of media, so i need a big "/home", any idea how many gb i should add to "/"???

thx for the answers

---

### Post by AdamG51172 on 2008-04-14
> So i should add more space from my /home partition to my / partition? :sad: The way i understood it was that all the non-system programs were going to install into /home/(user)
This can vary between distributions (Open Suse puts most non-system apps in /opt.), but Ubuntu usually puts applications from the official repositories into /usr/share/....  Apps from other repositories can, but not always end up in /opt/.

> I guess i will add a couple more GB. I currently have 7gb on "/" and 70gb on "/home", i usually download a lot of media, so i need a big "/home", any idea how many gb i should add to "/"???
7GB might be okay depending on how many extra applications you install.  I have one system only using less than one GB with lots of Graphics and Music programs.  My other box has lots of games and uses about 3GB of hd space.  You can always sift through the apps you don't use or want and free up space.

---

### Post by Ryuki_NdranC on 2008-04-14
> **AdamG51172 said:**
> This can vary between distributions (Open Suse puts most non-system apps in /opt.), but Ubuntu usually puts applications from the official repositories into /usr/share/....  Apps from other repositories can, but not always end up in /opt/.


7GB might be okay depending on how many extra applications you install.  I have one system only using less than one GB with lots of Graphics and Music programs.  My other box has lots of games and uses about 3GB of hd space.  You can always sift through the apps you don't use or want and free up space.

OK. for now I'm gonna stick with what i have. Still 28% free on my "/" but im gonna keep an eye on it.

Thx for your advice. good luck :)

---

