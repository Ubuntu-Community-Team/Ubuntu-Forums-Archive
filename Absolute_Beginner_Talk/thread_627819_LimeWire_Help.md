---
title: "LimeWire Help?"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by GeorgiaBoot on 2007-11-30
I have asked about LimeWire before and tried the suggestions but now I am having some trouble. I have limewire installed and I have Java. Yesterday I reinstalled limewire because it would just not load, when I clicked on it it would bring a window up but it would just be blank. So last night I reinstalled and limewire worked. Today I click on limewire and the same thing happens a page with limewire pops up but it is just blank. 

Another interesting thing is when I click close on limewire it closes the window but at the taskbar it still shows limewire there and when I click on that tab it pops up with a blank screen again.

Any help appreciated, thanks

---

### Post by jken146 on 2007-11-30
Which version of Java do you have?  I would suggest installing the sun-java6-jre package rather than anything else.

---

### Post by smacattack on 2007-11-30
i use frostwire (same as limewire)... i would suggest going to [www.frostwire.com](www.frostwire.com), it had a .deb... easy to install.

then ya.. make sure you    sudo apt-get install sun-java6-jre

---

### Post by rsambuca on 2007-11-30
Two questions:  Are you running desktop effects such as compiz-fusion?  Are you running 32 or 64 bit Ubuntu?

---

### Post by GeorgiaBoot on 2007-11-30
I am running Java 5.0, Compiz Fusion is running and I am on 32bit Linux.


Thanks Guys and Gals.

---

### Post by Parvo on 2007-12-01
I'm running x64 and compiz fusion and i had the same issue. i just updated java (sudo apt-get install sun-java6-jre) and it worked.:)

---

### Post by rsambuca on 2007-12-01
> **Parvo said:**
> I'm running x64 and compiz fusion and i had the same issue. i just updated java (sudo apt-get install sun-java6-jre) and it worked.:)

I think you must be mistaken on which version of Ubuntu you are running.  Limewire/Frostwire doesnt'work on 64-bit unless you are using the ia32 version of java.

---

### Post by PmDematagoda on 2007-12-01
Actually Limewire does work on Java 64 bit(Not Iced Tea), I don't know if it is the case in a older version of Limewire that it does not work on Java 64 bit, but the new version certainly does work on Java 64 bit.

---

### Post by rsambuca on 2007-12-01
> **PmDematagoda said:**
> Actually Limewire does work on Java 64 bit(Not Iced Tea), I don't know if it is the case in a older version of Limewire that it does not work on Java 64 bit, but the new version certainly does work on Java 64 bit.

I know it does, but it doesn't work with 'sun-java6-jre', which the poster indicated works for them.  It simply will not work with that version of java, and I think it is important to make that clear so that future 64bit users do not get frustrated.  Either Parvo is not using 64bit, or they are not using that version of java.

---

### Post by PmDematagoda on 2007-12-01
Forgive me rsambuca, but isn't sun-java6-jre in the Gutsy repositories in actuality 64 bit Java? Or is it 32 bit Java meant for Ubuntu 32 bit?

---

### Post by rsambuca on 2007-12-01
> **PmDematagoda said:**
> Forgive me rsambuca, but isn't sun-java6-jre in the Gutsy repositories in actuality 64 bit Java? Or is it 32 bit Java meant for Ubuntu 32 bit?

sun-java6-jre is in the 64-bit Gutsy repos, but it will not work with Frostwire.  If you are running 64bit and want Frostwire to work, you need to install and switch to the ia32-sun-java6-bin version.

---

### Post by PmDematagoda on 2007-12-01
Thanks for the clarification rsambuca:).

---

