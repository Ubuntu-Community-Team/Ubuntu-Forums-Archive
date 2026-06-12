---
title: "Wine Install Point Question"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by Sentinel83 on 2006-09-20
[FONT="Arial"]Hi everyone,

My machine is partitioned with / and /home partitions and I am low on space in my /home directory.  I would like to configure wine so that I can give Warcraft 3, and some other games a try.  Each time I have run through the configuration, it installs to my ~/.wine directory.  Is there a way to tell wine to install to my /usr/games directory, or some other place?  

Is there any downfalls to doing this (besides having to run the install as root initially)?  

Thanks in advance![/FONT]

---

### Post by CatKiller on 2006-09-20
I installs some stuff in your home directory - settings and so on. It actually installs itself in /usr/lib/wine.

If you run **winecfg** and click on the Drives tab you can change the location of the imaginary drive C:, which is probably what you mean. And no, there are no downsides, and you don't need to run it as root, provided your user has write permissions on the directory that you make as your imaginary C: drive.

If for some insane reason you don't want to run **winecfg** you could even copy the contents of ~/.wine/drive_c somewhere else and make a symbolic link in your home directory. Many things are possible.

---

### Post by Sentinel83 on 2006-09-20
Thanks for the reply CatKiller.  I'll give it a go tonight and see how it goes.  If I can get a few games to work with Wine, then my chances of running a 1 OS box increase dramatically.  Thanks!:p

---

### Post by CatKiller on 2006-09-20
No worries. WineHQ has a list of programs that work in Wine, and there are a number of games that run natively. I'm a sucker for Unreal Tournament.

And for those games that don't work well, contact the people that made them and tell them that you won't buy their games unless they support your OS. Although some games companies are already enlightened, like id, most require that they know there's a market before they'll develop for a platform. Encourage them to use cross-platform tools like OpenGL rather than single-market ones like DirectX, buy games that run under Linux, and tell the developers why you didn't buy their games if you don't. Then if they insist on only developing for a fraction of the market, it's their loss.

---

