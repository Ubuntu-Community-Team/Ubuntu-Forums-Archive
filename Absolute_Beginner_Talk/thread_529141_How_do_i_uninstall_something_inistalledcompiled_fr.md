---
title: "How do i uninstall something inistalled/compiled from source?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by jusmurph on 2007-08-18
I had a look at other threads etc and i did not do a check install nor do i have the source remaining on my computer.

I am looking to uninstall deluge and rhythmbox.

Also, how should i be installing these so i can install if i don't have a deb?

---

### Post by crispy_420 on 2007-08-18
Alot of the time the file with the source tells the proper procedure. It usually involves some sort of uninstall command.

If not check the devlepers site.

---

### Post by Nekiruhs on 2007-08-18
If you don't have the source, re download it. then cd into the source directory ```
./configure --prefix=/usr &&  make &&  sudo make uninstall
```

---

### Post by jusmurph on 2007-08-19
> **Nekiruhs said:**
> If you don't have the source, re download it. then cd into the source directory ```
./configure --prefix=/usr &&  make &&  sudo make uninstall
```

I tried that and the process seemed to work, i rebooted and it still remains.

So i tried apt-get remove and that removed something, then ran the command you gave again rebooted and nothing. Its still there?

---

### Post by Raptor45 on 2007-08-19
If you installed from source without using checkinstall, I don't believe apt-get should have known to remove anything at all. So, I'm not sure exactly what you've done. Did you just install a new version of rhythmbox right over the built in one? I can't imagine thats a good idea.

This is one of the reasons installing from source can be a bad idea. In the future I suggest using  .debs with the package manager so you don't have to deal with this, or at the very least try checkinstall.

Sorry, but I'm not exactly sure what else to try.

---

### Post by jusmurph on 2007-08-19
Cheers... now i just have to work out how to get last fm working in rhythmbox the hard way :|

---

### Post by Raptor45 on 2007-08-19
Don't you just have to check the last.fm plugin thats preinstalled?

---

### Post by jusmurph on 2007-08-19
> **Raptor45 said:**
> Don't you just have to check the last.fm plugin thats preinstalled?

When i go to veiw plugins it only shows visualization. The Preference of the only plugin is not greyed out. I also got the same issues in Deluge so i think it is a python thing, though i have no idea beyond that.

---

### Post by Raptor45 on 2007-08-19
Its there for me... and I don't think I installed any extra rythmbox packages or anything.

Are you sure in all your compiling you didn't mess up the rhythmbox install?

---

### Post by jusmurph on 2007-08-19
> **Raptor45 said:**
> 
Are you sure in all your compiling you didn't mess up the rhythmbox install?

No.

I am a 3 month old newb... I'm diving in trying to get my hands dirty and learn and sometimes i don't come best off.

Like today i learn that i really need use a check install if im using source.

---

### Post by jusmurph on 2007-08-20
Ok, so there is no fixing this issue.

How do i do this check install?

normally i would go:
./configure
make
sudo make install

---

