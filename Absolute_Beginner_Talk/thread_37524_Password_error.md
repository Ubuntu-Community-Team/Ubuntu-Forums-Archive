---
title: "Password error"
date: 2005-05-27
forum: Absolute Beginner Talk
---

### Post by rigg on 2005-05-27
I'm going crazy... ;)

I'm totally noob at linux, but quite handy with windows.

Trying to run ubuntu live 5.04 on my computer, during start-up i'm aked to enter a password, and I enter one of my standard ones..., then whem I'm in x and try to enter network settings I'm asked to enter password. The password is wrong, so I cant acess any settings.....

What to do? And why am I not asked to enter username and password for setting up "normal" user account during setup. (If I click "no" on that quetion during setup I'm asked to log in with username and password)

Please help a confused noob  ](*,) 


/rigg

---

### Post by jdodson on 2005-05-27
> **rigg]I'm going crazy...  said:**
> (*,) 


/rigg

when you are asked for a password from the network manager or synaptic or the like, basically they are asking for a "sudo" password.  basically the only users that can "sudo" are those in the "sudoers" config file located here:  /etc/sudoers

so just enter the password of the original account you created your hoary install with and that should get you "sudo" access.

---

### Post by bigbadblo on 2005-05-27
Jdodson...

I don't know if this is related or not -- but I've experienced some of the named problems concerning "Administrative User" passwords ... for example, as I try to change network settings, I'm prompted for my password.  I enter it, but am returned to the same setting screen, apparently no better off as Kubuntu doesn't appear to relinquish rights to change settings.

I've also replied to a similar post here: [http://www.ubuntuforums.org/showthread.php?t=37360](http://www.ubuntuforums.org/showthread.php?t=37360)

Any ideas about this?  Rigg, does this adaquately describe the problem your having as well?

...

blo

---

### Post by rigg on 2005-05-28
Jdodson: During start up of the live cd I'm only promted to create one password, and  that is of course that password I try to enter later when I'm promted to enter my password, But, as I said - that password is not the correct one! '

blo: Seems like the same problem!

/rigg

---

