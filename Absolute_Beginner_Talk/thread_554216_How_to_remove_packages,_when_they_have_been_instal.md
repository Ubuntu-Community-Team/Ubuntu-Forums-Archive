---
title: "How to remove packages, when they have been installed with GDebi?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by xelnaga666 on 2007-09-18
I don't consider myself to be a debian/*buntu new guy. Ive been using it for 2-3 years nicely. But in all that time I have never needed to uninstall .deb installs.

The package for removal in name is Avant Window Navigator. In which I installed from here previously as a .deb package with the GDebi (right click install) installer.

Any ideas?, im guessing there's something really silly I'm missing and so I apologize if this sounds stupid.

Thanks, Steve

---

### Post by jnorth on 2007-09-18
Well, like anything *nix, there are about 10 ways to do this, any of which could be considered "correct" :)

Probably the easiest is to go to your "System" menu and select "Administration" and then "Synaptic Package Manager".

Put in your password, and once it loads, use the search on the toolbar to look for your package, just search "avant" or something similar.  When you see the package, select it, right click, and do a remove.

HTH

---

### Post by xelnaga666 on 2007-09-19
Thanks for the reply, I now have it removed, was called "avant-window-navigator".

I would have issued an "apt-get remove" on this, but at the time I had no idea what the package was callled. Kinda obvious lol.

Thanks again

---

### Post by jnorth on 2007-09-19
Ahh I see.  No problem...

---

### Post by bobbocanfly on 2007-09-19
If you are not scared of the command line simply use:

```
sudo dpkg -r package
```

---

