---
title: "Installing/Updating GCC"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by ninocass on 2005-11-24
Hi all

im having some problems making files im getting a "gcc-3.4 command not found"

im guessing that my version of GCC is out of date

could anyone tell me how to reinstall it

Thanks

---

### Post by ds[de] on 2005-11-24
To install gcc-3.4 type

```
sudo apt-get install gcc-3.4
```

If it's telling you that you already have the selected version/package, type 

```
sudo dpkg -e gcc-3.4
```

then try to install it again with the first command.

If you want the newest version, type

```
sudo apt-cache search gcc
```

and then 

```
sudo apt-get install gcc-*newestversion*
```

I think 4.1 is the most recent release.

Regards,
ds[de]

---

### Post by lisje on 2005-11-25
[QUOTE=ninocass]Hi all

im having some problems making files im getting a "gcc-3.4 command not found"

im guessing that my version of GCC is out of date

could anyone tell me how to reinstall it

Thanks[/QUOTE]


it would be wise to install "buildessential" since there is more then just gcc you'll be needing to compile packages
```
sudo apt-get install buildessential
```

---

