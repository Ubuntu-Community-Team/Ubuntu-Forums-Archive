---
title: "Emai Applications"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2007-10-08
I'm interested in playing with Mozilla Thunderbird and Evolution Mail on my XUbuntu system.  Before I start using either of them seriously, I want to know how easy it is to transfer data (address book, email, account settings) between other computers (e.g. Linux systems or Windows)?

I tend to alternate between different computers, so it would be nice to be able to move data around.

If I went for Mozilla Thunderbird pocket edition as apposed to just installing directly to a computers hard disk, would it work between a Windows XP and Linux system without any trouble?

Where do Mozilla Thunderbird and Evolution mail store their data?  I would like to be able to back things up easily so that I'm covered in the unlikely event of a system crash or something.

Thanks in advance for your advice :)

---

### Post by finer recliner on 2007-10-08
thunderbird stores user's settings and data in ~/.thunderbird

its easy to transfer this folder between computers, just copy and paste the folder to your home directory on your other linux box, and thats it!
(you may want to back up the original profile on the computer youre copying to just for good measure)
```

cp -r .thunderbird .thunderbird.bck

```

evolution stores user's settings and data in ~/.evolution

i'm sure its just as easy to move this folder between computers

i dont know if this will work if you copy the folder to windows xp. i believe windows stores thunderbird information in the "application data" folder.

---

### Post by hyper_ch on 2007-10-08
between TB on windows and linux it's easy. You can even set a common place for both to store the data if you want. You just copy the one folder over from linux to windows or vice versa into the according right spot.

---

### Post by mikeypc2006 on 2007-10-08
> **hyper_ch said:**
> between TB on windows and linux it's easy. You can even set a common place for both to store the data if you want. You just copy the one folder over from linux to windows or vice versa into the according right spot.

Thanks for that, but how exactly do I go about doing that?

---

### Post by nick_h on 2007-10-08
Read this howto - [Howto: Share Thunderbird & Firefox data between Ubuntu & Windows](http://ubuntuforums.org/showthread.php?t=203524)

---

