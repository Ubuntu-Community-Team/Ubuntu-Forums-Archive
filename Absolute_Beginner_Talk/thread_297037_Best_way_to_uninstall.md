---
title: "Best way to uninstall"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by Deronius on 2006-11-10
If an application isn't in the install/uninstall list what is the best way to completely remove an installed program?  I downloaded and installed Cedega but was having issues so I wanted to try a re-install.  I deleted the folder but after restart the program still showed up in the applications menu.

Any help would be appreciated.  

Thanks in advance.

---

### Post by johnnymac on 2006-11-10
More than likely you'll have to search for it and start removing all instances of cedega - so try something like this:

```

cd /
sudo find -name *cedega* -print > cedegaloc

```

I did the pipe to a file because I don't know how much you'll get back so now all your results will be in a temporary file

Then take what is in the file and begin removing the instances.  Once your all done remove the cedegaloc temp file and all should be gone.

---

### Post by macdo on 2006-11-10
can't you just do this? ```
sudo apt-get remove --purge cedega
```

---

### Post by jimbren on 2006-11-10
I'm not in fron of my machine right now, but I believe you're looking for 
```
sudo apt-get remove --purge *package name*
```

---

### Post by PriceChild on 2006-11-10
> **macdo said:**
> can't you just do this? ```
sudo apt-get remove --purge cedega
```I would DEFINATELY do this first...

Before doing this:
> **johnnymac said:**
> More than likely you'll have to search for it and start removing all instances of cedega - so try something like this:

```

cd /
sudo find -name *cedega* -print > cedegaloc

```I did the pipe to a file because I don't know how much you'll get back so now all your results will be in a temporary file

Then take what is in the file and begin removing the instances.  Once your all done remove the cedegaloc temp file and all should be gone.

---

### Post by johnnymac on 2006-11-10
Correct....if he installed Cedega using a *.deb or via checkinstall then using apt-get is the correct process.  If you downloaded the source and did a make|mak install the apt-get won't help.

---

### Post by Deronius on 2006-11-10
Wowza!!!  Holy quick replies Batman!

Thanks for the help.  I'm at work but I'll definitely give it a go when I get home.  

I knew there was some nifty command.

Thanks again.

---

