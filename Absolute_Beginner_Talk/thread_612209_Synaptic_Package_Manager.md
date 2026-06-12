---
title: "Synaptic Package Manager"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by adi82 on 2007-11-13
Synaptic Package Manager 
after reading the help and did a search on the forum i cant find out what does this mean

1.installed (auto removable)

2.installed (local or obsolete)

---

### Post by rudeboyskunk on 2007-11-13
Do Not Run That Command, See Top Sticky For Details

---

### Post by Joeb454 on 2007-11-13
That post's been removed :) Thanks to whoever did it, I was just about to report it lol

---

### Post by dkruidhof on 2007-11-13
Here is my understanding:

1.Packages that are no longer needed on your system and can be removed. In my experience, these are usually packages that were reqs for other packages I had installed but were not removed when the package that needed them got removed. 

2. Packages that are not in the repositories that you have selected to be your sources. Thus, they are either installed from a local source (obtained from a soucre other than your selected repositories) or are obsolete (were removed from the repositories because of being old)

Here is another thread that may be of help: [http://ubuntuforums.org/showthread.php?t=105804](http://ubuntuforums.org/showthread.php?t=105804)

Hope that helps.

---

### Post by adi82 on 2007-11-13
> **Joeb454 said:**
> That post's been removed :) Thanks to whoever did it, I was just about to report it lol

yes i made an other search and got nothing....:confused:

---

### Post by adi82 on 2007-11-13
> **dkruidhof said:**
> Here is my understanding:

1.Packages that are no longer needed on your system and can be removed. In my experience, these are usually packages that were reqs for other packages I had installed but were not removed when the package that needed them got removed. 

2. Packages that are not in the repositories that you have selected to be your sources. Thus, they are either installed from a local source (obtained from a soucre other than your selected repositories) or are obsolete (were removed from the repositories because of being old)

Hope that helps.

should i clean them???

---

### Post by mcduck on 2007-11-13
You can safely remove the packages marked as autoremovable. But most likely you don't want to remove those marked as 'local or obsolete'.

---

### Post by Inxsible on 2007-11-13
Local or obsolete are packages that you have installed outside of the synaptic for eg, if you downloaded the deb files from somewhere(hence the local -- only on your machine)
they may also have packages that are obsolete like some app that you upgraded to the latest version.

Either way, you should be careful and make sure you do not want that app installed, before removing them.

---

