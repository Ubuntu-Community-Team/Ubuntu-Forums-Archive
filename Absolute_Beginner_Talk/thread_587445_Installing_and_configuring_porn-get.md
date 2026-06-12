---
title: "Installing and configuring porn-get"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Duffadash on 2007-10-22
Some of you may at some point have heard of [porn-get]("http://lesbian.mine.nu/"), an apt-get clone where you can download packages of... Well, porn.
Now, I'm not sure whether this is against the forums policy, but personally I think it's a funny idea, only, I have no idea how to configure the files so I can make install it. Anybody want to help? Any help would be appreciated...

Oh, and the [readme]("http://lesbian.mine.nu/readme") mention a $dir function I have to change, but I have no idea how that actually works...

---

### Post by Beggar on 2007-10-22
While, I dont exactly know the rulebreakingness of this while thing, in the interest of making this post go away quickly, and/or being the first of an epic thread:

porn-get is just a script, the $dir you need to change is in the script, about the 10 line or so, set it to something like "/home/username/.hiddenfile", then run ```
sudo chmod 777 ~/.hiddenfile
``` Then you should be able to just run the script.

---

### Post by Duffadash on 2007-10-23
I'm afraid I didn't quite get exactly what I had to change. I changed line 10 to ```
dir="/home/duffadash/.porn-get"
``` is this correct? And what about porn-cache?

---

