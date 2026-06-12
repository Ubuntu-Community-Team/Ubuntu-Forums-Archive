---
title: "Am I using Beryl or Compiz?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by richardgundersen on 2007-09-16
Hi

I've got a nice fresh installation of Feisty, and have enabled "Desktop Effects"

I think it's using Compiz, rather than Berly under the covers. Am I right?

Also, if I am using Compiz, is there a nice theme manager like Emerald (which I have used with Beryl before) that works with Compiz?

Thanks!

---

### Post by por100pre1 on 2007-09-16
You can install Beryl and Emerald, it will work with your existing installation:

```
sudo apt-get install beryl beryl-manager emerald emerald-themes
```

Beryl usually works fine in Feisty. In the future, Beryl will not be present in Ubuntu. Compiz-Fusion, the current Compiz modules will be used in Gutsy. If you use the repositories versions of Beryl and Compiz, any upgrade will be painless.

---

### Post by richardgundersen on 2007-09-16
Thanks for the quick reply. I think I will stick with Compiz if that's the version that will be used from now on.

Just installed Emerald, but choosing an Emerald theme doesn't change the appearance of the windows. Does Emerald only work with Beryl?

I saw a package called 'compiz-emerald' - is this the version of Emerald I should be using with Compiz? It only seems to be available as an RPM though, is there an Ubuntu version anywhere?.

Thanks

---

### Post by jw5801 on 2007-09-16
Compiz and Beryl are now the one project, they merged together into Compiz-Fusion. Also the default "Desktop Effects" are an old version of Compiz, if you would like to install Compiz-Fusion, take a look at [this](http://ubuntuforums.org/showthread.php?t=481615) how-to.

---

### Post by richardgundersen on 2007-09-16
Thanks again for the helpful replies. Got it all working now. I didn't realise the difference between Compiz (that comes out of the box) and Compiz Fusion. 

I used the following excellent guide to remove everything that I had, and install Compiz Fusion with Emerald. 

[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

There are some nice new plugins that I hadn't seen before too! 

BTW I shelled out for Vista the other day (urgh) which I only intend to use for games (the ONE THING that Linux isn't great for sadly). The user interface (Aero) is pathetic compared to Compiz. I hope this convinces more people to try Linux - it's awesome :)

---

