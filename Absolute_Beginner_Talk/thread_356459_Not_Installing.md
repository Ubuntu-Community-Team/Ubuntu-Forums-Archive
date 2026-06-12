---
title: "Not Installing"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by sowthpaw on 2007-02-08
Hi, I have a broadcom based chip,  and used the bcm43xx-fwcutter tool to get my internet connection working with ubuntu. But now when I try to download a software package, I get the error that it "conflicts with other software." When I look at the error report it says that the software is conflicting with the bcm43xx-fwcutter tool, and that the tool needs to be removed. But obviously I can't do this because I need internet. Anyone know what I can do?

---

### Post by igknighted on 2007-02-08
> **sowthpaw said:**
> Hi, I have a broadcom based chip,  and used the bcm43xx-fwcutter tool to get my internet connection working with ubuntu. But now when I try to download a software package, I get the error that it "conflicts with other software." When I look at the error report it says that the software is conflicting with the bcm43xx-fwcutter tool, and that the tool needs to be removed. But obviously I can't do this because I need internet. Anyone know what I can do?

Which other software package is causing the issue?  And, how did you get the bcm43xx package?  Was it from the official repo's?

---

### Post by sowthpaw on 2007-02-08
All software packages are doing it, and I got it from a directory on ubuntu's site.

---

### Post by igknighted on 2007-02-08
> **sowthpaw said:**
> All software packages are doing it, and I got it from a directory on ubuntu's site.

Hmmm...  you dont remember which directory precisely, do you?  The reason I as is this: if you got a dapper package and installed it to edgy, it could hold back versions of programs that need to be upgraded to work with edgy's programs.  I would try uninstalling the broadcom package, installing all that stuff, then trying to install the broadcom package again.  In fact, I would search for it in synaptic (or using aptitude search in the terminal) and install through that rather than search the ubuntu directories manually.

---

### Post by sowthpaw on 2007-02-08
yea it must be a bad package, although I was so happy getting my internet to work, Im nervous to uninstall, and risk not getting it work again.

---

### Post by igknighted on 2007-02-08
> **sowthpaw said:**
> yea it must be a bad package, although I was so happy getting my internet to work, Im nervous to uninstall, and risk not getting it work again.

If it worked once it can work again... at least there is a real driver for your card.  Although even if worst comes to worst and you need to use NDISwrapper, thats not very hard either.  Just to be safe, you do have a wired connection you can plug into for all of this, right?

---

### Post by sowthpaw on 2007-02-08
I should be able to plug into my router or modem and have internet access. It just that I spent a lot of time getting it to work. Thankyou for your help though.

---

### Post by sowthpaw on 2007-02-08
Ok I took a gutsy move, but got it to work. I went ahead and installed a piece of software anyway. (Agreeing to remove the package also). And after it went ahead with its processes, and the random software finished installing, the internet still worked. Also the message didn't pop up either anymore. =) WOOHO.

---

