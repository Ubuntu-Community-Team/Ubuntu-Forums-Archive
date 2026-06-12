---
title: "Manually uninstall a program"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by newbie59 on 2007-03-21
I want to uninstall Skype using the terminal so I can reinstall it through Automatix. Can someone tell me how to do this or point me to a how-to that walks a person through the steps.

Thanks! :)

---

### Post by Kobalt on 2007-03-21
Go to the directory where you have the Skype program, with the command *cd*, then enter :
```
sudo make uninstall
sudo make clean
```

---

### Post by fakie_flip on 2007-03-21
> **Kobalt said:**
> Go to the directory where you have the Skype program, with the command *cd*, then enter :
```
sudo make uninstall
sudo make clean
```

Skype is not an open source program, so it can't be installed from source code. He probably installed it from the deb at the Skype website. I am not sure why to install it through Automatrix instead. The command to remove skype is.

```
sudo apt-get remove skype
```

---

### Post by newbie59 on 2007-03-21
How do I find the directory where skype is
i can't find it in my file browser

---

### Post by newbie59 on 2007-03-21
i got it to uninstall fine. thank you
and the reason i want to reinstall through automatix is i couldn't get skype to work installing it the way i originally did and thought maybe if i installed it with automatix i get it to work properly

---

### Post by newbie59 on 2007-03-21
is their a list of commands posted somewhere that i can refer to and try before i ask for assistance??

---

### Post by raul_ on 2007-03-21
What commands?

---

### Post by newbie59 on 2007-03-21
by commands i mean what you use in the terminal (such as "sudo apt-get remove skype")
isn't that called a command. maybe my terminalogy is wrong

---

### Post by doobit on 2007-03-21
I believe that Automatix will uninstall what it doesn't need before it reinstalls Skype. You should be OK just using Automatix. It's a pretty powerful script.

---

### Post by raul_ on 2007-03-21
Since you said you removed it i didn't understant what commands you were searching for. But basically you can do

```

aptitude install <package>
aptitude remove <package>

or

aptitude search <package>

```

You can also uninstall by Automatix (if you installed the package with Automatix, of course)

---

### Post by fakie_flip on 2007-03-21
> **newbie59 said:**
> is their a list of commands posted somewhere that i can refer to and try before i ask for assistance??

[http://en.wikipedia.org/wiki/List_of_Unix_programs](http://en.wikipedia.org/wiki/List_of_Unix_programs)

Is this what you are looking for?

---

### Post by newbie59 on 2007-03-21
Thank you all for your input :guitar:

---

