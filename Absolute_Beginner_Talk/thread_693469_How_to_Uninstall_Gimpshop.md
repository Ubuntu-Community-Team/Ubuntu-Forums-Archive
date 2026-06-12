---
title: "How to Uninstall Gimpshop?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by jezebel on 2008-02-11
I installed Gimpshop today, without, by the way, uninstalling Gimp. It was fine/good etc.. but then it has crashed a couple of times, and also, I can't change my brush sizes too easily. 

So I want to ditch Gimpshop, and go back to plain old Gimp. But I don't know how to uninstall and revert.

Any help??

---

### Post by jan quark on 2008-02-11
for packages installed with synaptic use
```

sudo apt-get remove --purge package
```

for downloaded packages use
```

sudo dpkg -r package
```

replace the "package" with the actual package name you have downloaded

---

### Post by jezebel on 2008-02-11
Thanks...

So in my case, the package would be gimpshop?

J.

---

### Post by jan quark on 2008-02-11
try it :)

and run for cover

---

### Post by jezebel on 2008-02-11
I did it - and it worked great. Now I'm back to plain old Gimp and happier for it!

---

### Post by MagicPaul on 2008-05-15
i had the same problem too. all sorted now, thanks!

---

### Post by mithritades on 2008-05-15
whats the difference between gimpshop and gimp?...if any

---

### Post by unisol on 2008-05-16
gimpshop is a gimp hack that gives you photoshop menus and keyboard shortcuts. its still gimp.

---

### Post by ubunu on 2008-05-16
As far as I know gimpshop is based on an earlier version and doesn't have some of the facilities of Gimp 2.4.5.

I found gimpshop useful for getting to know the tools as it was similar to the photoshop layout once I dumped it I found the native Gimp interface a lot easier.

---

