---
title: "[SOLVED] Can't capture mouse pointer in virtualbox"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by bumanie on 2008-03-11
Just installed virtualbox binary 1.5.6 on hardy heron alpha 6. I am unable to capture the mouse pointer within virtualbox. I had the same issue when I installed virtualbox on gutsy gibbon. Anyone have any idea how to fix this? Virtualbox is obviously useless if one can't capture the mouse pointer. I have looked on the virtualbox bugs site and found that the problem has been reported, but there is no fix mentioned yet. It apparently was not a problem in earlier versions. I have not been able to locate a download of an earlier version.

---

### Post by Oldsoldier2003 on 2008-03-12
> **bumanie said:**
> Just installed virtualbox binary 1.5.6 on hardy heron alpha 6. I am unable to capture the mouse pointer within virtualbox. I had the same issue when I installed virtualbox on gutsy gibbon. Anyone have any idea how to fix this? Virtualbox is obviously useless if one can't capture the mouse pointer. I have looked on the virtualbox bugs site and found that the problem has been reported, but there is no fix mentioned yet. It apparently was not a problem in earlier versions. I have not been able to locate a download of an earlier version.

[http://www.virtualbox.org/wiki/Download_Old_Builds](http://www.virtualbox.org/wiki/Download_Old_Builds)

---

### Post by glennric on 2008-03-12
One thing you will have to do is install "Virtualbox Guest Additions" in the guest operating system.  There should be an option in the virtual box menu bar of the guest os main window to do this.

---

### Post by Oldsoldier2003 on 2008-03-12
> **glennric said:**
> One thing you will have to do is install "Virtualbox Guest Additions" in the guest operating system.  There should be an option in the virtual box menu bar of the guest os main window to do this.
The mouse pointer should be captured by default IIRC. but yes if you plan on doing much with windows especially, you'll want the Guest additions.

---

### Post by glennric on 2008-03-12
> **Oldsoldier2003 said:**
> The mouse pointer should be captured by default IIRC. but yes if you plan on doing much with windows especially, you'll want the Guest additions.

I had this problem with the latest version of virtualbox, but after I installed the guest editions, (it isn't additions, my mistake) it went away.

---

### Post by Oldsoldier2003 on 2008-03-12
> **glennric said:**
> I had this problem with the latest version of virtualbox, but after I installed the guest editions, (it isn't additions, my mistake) it went away.

I'm running 1.5.4 they're called additions there :) dunno if i want to run a newer verison yet since everything works fine as it is...

---

### Post by glennric on 2008-03-12
> **Oldsoldier2003 said:**
> I'm running 1.5.4 they're called additions there :) dunno if i want to run a newer verison yet since everything works fine as it is...

I am running 1.5.6 and everything is running fine after I installed the Guest Additions.  You are right it is Additions.  This time I actually checked.

---

### Post by Flynn555 on 2008-03-27
im having the same problem...for some reason nothing is happening when i click install guest additions. :(

---

### Post by Oldsoldier2003 on 2008-03-27
> **Flynn555 said:**
> im having the same problem...for some reason nothing is happening when i click install guest additions. :(

you have to install them from within the guest OS. all you are doing is mounting the extensions .iso when you click on the menu item.

---

### Post by bumanie on 2008-03-31
I found out there was a bug with 1.5.6 version of virtualbox. Installed 1.5.4 and everything works fine. Virtualbox bug report had three others complaining of the same problem with 1.5.6 version.

---

### Post by Tim0miT on 2008-04-15
yeah, just install 1.5.4 and all will be fixed...:guitar:

---

### Post by kq6up on 2008-04-27
The only bad thing about 1.5.4 it does not give a choice of adapter cards.  The default card does not seem t work with FreeBSD.  However 1.5.6 gives more choices of controller cards and the top controller works with FreeBSD.  So I am a little bummed.

Also, installing guest additions did not work for me.

Chris

---

