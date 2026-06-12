---
title: "Uninstalling software"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by digitalzen on 2007-11-01
Hi all,

I hope this isn't a common and recently answered question. I took a quick look but didn't see the same question anywhere.

I tried to install Proftpd via terminal and was unsuccessful in setting up the user folder/settings correctly so i wanted to just remove the whole thing and try again. Then I found you can install it via the Add/Remove programs in the GUI.

But this brought me to a question i've had before. How do i uninstall something that I install via terminal? Do I *usually* have to just remove the main folder? Or do most programs spread themselves out to multiple folder like windows does? 

I think this is dependent on the program which is installed... but i don't know that for sure.

Can anyone clear this up for me?

Thanks,

Digitalzen

---

### Post by Inxsible on 2007-11-01
> **digitalzen said:**
> Hi all,

I hope this isn't a common and recently answered question. I took a quick look but didn't see the same question anywhere.

I tried to install Proftpd via terminal and was unsuccessful in setting up the user folder/settings correctly so i wanted to just remove the whole thing and try again. Then I found you can install it via the Add/Remove programs in the GUI.

But this brought me to a question i've had before. How do i uninstall something that I install via terminal? Do I *usually* have to just remove the main folder? Or do most programs spread themselves out to multiple folder like windows does? 

I think this is dependent on the program which is installed... but i don't know that for sure.

Can anyone clear this up for me?

Thanks,

Digitalzen
Yes this has been asked millions of times before. But no worries.
you can uninstall anything by 4 methods
1) ```
sudo aptitude remove *package-name*
```2) Applications--> Add/Remove. Search and uninstall

3) System --> Administration --> Synaptic Package Manager. Search and uninstall

4) ```
sudo apt-get remove *package-name*
```All 4 are interchangeable. meaning it doesn't matter what installation method you used, you can uninstall using any of the 4 above methods.

The EXCEPTION : If you installed by compiling from source, then you need to have the source folder and uninstall it using ```
sudo make uninstall
```

---

### Post by clancymf on 2007-11-01
I am assuming you did sudo apt-get install "X".  If so do sudo apt-get remove "X"

---

### Post by Rich78 on 2007-11-01
You can remove the application via the Synaptic Package manager, and select remove application only.

---

### Post by digitalzen on 2007-11-01
> **Inxsible said:**
> Yes this has been asked millions of times before. But no worries.
you can uninstall anything by 4 methods
1) ```
sudo aptitude remove *package-name*
```2) Applications--> Add/Remove. Search and uninstall

3) System --> Administration --> Synaptic Package Manager. Search and uninstall

4) ```
sudo apt-get remove *package-name*
```

All 4 are interchangeable. meaning it doesn't matter what installation method you used, you can uninstall using nay of the 4 above methods.

The EXCEPTION : If you installed by compiling from source, then you need to have the source folder and uninstall it using ```
sudo make uninstall
```

Inxsible.... you are pretty much my hero.

A reply which is accurate, not insulting, and even gives options! All kidding aside thanks!!!!!!:):KS:)

---

