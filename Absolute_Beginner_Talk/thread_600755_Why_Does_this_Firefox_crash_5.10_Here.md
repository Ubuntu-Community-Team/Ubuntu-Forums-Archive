---
title: "Why Does this Firefox crash? 5.10 Here"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by sam-c on 2007-11-02
I am using 5.10 and I have not been succesfull in updating to Firefox 2 yet.
So with firefox 1.07 works ok untill I login to Yahoo.
Also while I was using Google and gmail it crashed and like with the yahoo closed down instantly.
Otherwise Firefox was OK and Plugins with sound and pictures worked fine!
Thanks
Sam:confused:

PS. I removed 1.07 and reinstalled it, after that the above problems.

---

### Post by agurk on 2007-11-02
Try running Firefox in safe mode, meaning, without extensions (add-ons) or plugins:
```
firefox -safe-mode
```

If it doesn't help, try creating a fresh Firefox profile:
```
firefox -ProfileManager
```

---

### Post by sam-c on 2007-11-02
Thanks
I did safe-mode
when I tried to login to yahoo I got a message

Segmentation Fault
Sam:confused:

---

### Post by alienexplorers on 2007-11-02
Check to see if you are using any of these extensions:
> [http://kb.mozillazine.org/Problematic_extensions](http://kb.mozillazine.org/Problematic_extensions)

---

### Post by agurk on 2007-11-02
Interesting. :)

In your home folder, there should be a .mozilla/firefox folder containing your profile. Rename it:
```
mv ~/.mozilla/firefox ~/.mozilla/firefox_old
```

...and start Firefox again.

---

