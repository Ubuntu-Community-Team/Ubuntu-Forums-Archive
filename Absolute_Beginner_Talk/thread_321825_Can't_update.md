---
title: "Can't update"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Hal99 on 2006-12-19
I am trying to get linux running on an old acer travelmate 507dx laptop, which is one step away from being a door stop!

I installed Debian 31r3 i386 on the advice from a friend but could not get the apt get to carry out updates.  I then installed a full version of ubuntu, which works fine except that again I can't do updates.  The updater part of the gnom desktop says there are 103 updates available but I can't get to any of them.  Firefox works fine as does Evolution mail, I can surf the web and pick up mail without problems.  I have also noticed that Firefox can't find and download plugins, maybe part of the same probelm.

I'm connected through a hard wired router.  I have not been able to "see" the other (windows) machine connected to the router.  Not sure if this is part of the same problem but I thought that I needed to do updates first before worrying about the two machines talking.

It must be so obvious but I can't find anything on any of the forums.](*,)

---

### Post by raul_ on 2006-12-19
What do you mean, you can't get any of them?

---

### Post by Hal99 on 2006-12-19
The updates just don't!  The machine tries to get the updates but just times out

---

### Post by raul_ on 2006-12-19
What version of Ubuntu are you using?

---

### Post by Hal99 on 2006-12-19
Ubuntu 6.06 LTS Dapper Drake

---

### Post by annda on 2006-12-19
what message do you get when you open the terminal and type

```
sudo apt-get update
```

you will be asked for your password and then some index files should be downloaded and processed. do you get any suspicious errors?

---

### Post by raul_ on 2006-12-19
:-k  I don't know...Maybe if you try to enable extra repositories, and seeing if those servers work with you. The only thing that comes up to me is that the servers are down...

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

---

### Post by Hal99 on 2006-12-19
Tried to enable extra repositories but when I hit the reload button I just get a dialog box saying that it is downloading which stays inactive for as long as I let it.

When I tried the "sudo apt-get update" I got a message that the connection had timed out for each address.  Then a message about not being able to get lock.

I did not notice any activity on my router during either of these processes, as if no information was being sent to the outside world

---

