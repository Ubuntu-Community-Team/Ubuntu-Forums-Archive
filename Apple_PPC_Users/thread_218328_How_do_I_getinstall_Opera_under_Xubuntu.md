---
title: "How do I get/install Opera under Xubuntu"
date: 2006-07-18
forum: Apple PPC Users
---

### Post by MrFrodo on 2006-07-18
Sugject says it all. Just installed Xubu on an old Bondo G3, and I want to use Opera browser. Can anyone help me? I see a download of a freebsd or intel .deb file. Can I use those?

:confused:

---

### Post by briguy on 2006-07-18
Download the .deb file, then enter ```
sudo dpkg -i opera-xxx.deb
``` in terminal.

---

### Post by k420 on 2006-07-18
install automatix and it will do most of the work for you [http://www.getautomatix.com]("http://www.getautomatix.com")
or at the command lint do ```
sudo apt-get install opera
```
i think you will need the universe repos activated

---

### Post by MrFrodo on 2006-07-18
> **briguy said:**
> Download the .deb file, then enter ```
sudo dpkg -i opera-xxx.deb
``` in terminal.

Which one. Intel-FreeBSD or Intel-Linux?

---

### Post by briguy on 2006-07-18
> **MrFrodo said:**
> Which one. Intel-FreeBSD or Intel-Linux?

Intel-Linux.  FreeBSD is another OS similar to Ubuntu, but not Linux based.

---

### Post by avtolle on 2006-07-18
Why not activate the new Commercial Repo under Synaptic and install from there?

---

### Post by MrFrodo on 2006-07-18
> **briguy said:**
> Intel-Linux.  FreeBSD is another OS similar to Ubuntu, but not Linux based.

Had trouble with the Terminal. Right clicked and chose to install with package installer. Got an error of "Wrong architecture 'i386'

Am I outta luck?

---

### Post by k420 on 2006-07-18
go to [www.getautomatix.com](www.getautomatix.com)

---

### Post by MrFrodo on 2006-07-18
> **k420 said:**
> go to [www.getautomatix.com](www.getautomatix.com)

Now i'm at autoscript_dapper waiting for some key...

Now what?

---

### Post by k420 on 2006-07-18
did you follow the directions on the website andthen install automatix

---

### Post by MrFrodo on 2006-07-18
> **k420 said:**
> did you follow the directions on the website andthen install automatix

It finally worked. Slow connection i guess.

---

### Post by k420 on 2006-07-18
ok sweet

---

### Post by -Phi- on 2006-07-18
Just in case automatix doesn't work for you (no idea why it wouldn't, haven't used it myself), as **avtolle** said, you can get Opera from the Dapper Comercial Repository. There's more information about it here: [http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/]("http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/")

- Phi

---

