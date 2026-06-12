---
title: "[SOLVED] Can I &amp;quot;remake&amp;quot; a .deb package?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by nge on 2008-04-10
Hi all.

I've just installed some new programs from the online repositories via the Add/Remove option in Gutsy. Now, my sister also wants them installed in her laptop. Is there any way for me to re-create those packages so that I don't have to go online again to install?

thanks.

~nge~

---

### Post by brian_p on 2008-04-10
> **nge said:**
> Hi all.

I've just installed some new programs from the online repositories via the Add/Remove option in Gutsy. Now, my sister also wants them installed in her laptop. Is there any way for me to re-create those packages so that I don't have to go online again to install?

thanks.

~nge~

Copy the packages and their dependencies to her /home on the laptop. Install with

```
sudo dpkg -i <package>
```

The apt-proxy package provides a more elegant solution.

---

### Post by nge on 2008-04-10
hmm .. where to find those packages ?

---

### Post by hyperair on 2008-04-10
If you've downloaded and installed on one computer already the debs are cached in /var/cache/apt/archives. Copy the required debs over. Then just run sudo apt-get install like you did with the first computer.

---

### Post by solar george on 2008-04-10
Try apt on cd it will do that automatically

---

### Post by nge on 2008-04-10
> **hyperair said:**
>  /var/cache/apt/archives

Thanks !

problem solved.

---

