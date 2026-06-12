---
title: "Installing local .deb packages?"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by mlind on 2006-06-28
Can I install local packages using aptitude/apt-get ?
Yum can do this I believe.

 I usually end up using dpkg -i *package* && apt-get install -f .. 
There must be a _easier_ way?

---

### Post by gr0kzer0 on 2006-06-28
Sorry, I don't have an answer.  I'm just wondering - by "local" you mean the .deb is already on your box, right?  Why is dpkg -i a problem?

---

### Post by Dr. Nick on 2006-06-28
Yes you can, In dapper it should launch a gui if you click on it.

it should launch the Gdebi Packae manager aslong as your in gnome

---

### Post by x64Jimbo on 2006-06-28
apt-get and dpkg are the same program called in different ways. Both are part of the Aptitude package. dpkg is for installing local files while apt-get installs them from a repository. 
Make SURE that the debs you are installing are made for Ubuntu, not Debian. There are some core differences between them that could screw up your system if you install a Debian deb file.

---

### Post by mlind on 2006-06-28
Thanks for the replies,

@gr0kzer0
Yes, by local package I mean a .deb package that's located on my system somewhere.

The issue I want to tackle here is that when I want to install package that's not
available on repositories, I must also install all required dependencies for this
package. Dependencies would be available on official repositories, but dpkg
doesn't seem to mind that. It just marks package as broken, because of the
missing dependencies - which is not what I wanted.

*aptitude -f install *solves this always, but it would be nice if I could point local .deb
package for aptitude to install, and it could solve dependency issues for me.

Does gdebi handle dependency fetching from remote source?

---

### Post by Dr. Nick on 2006-06-28
not sure if gdebi handles the dependencies. I think it would if the dependencies are in the repos though. I have very limited usage of it, but in that time have never had a problem with it.

It may just be a gui frontend to one of the others.

Do you have all the universe, multiverse repos enabled?

---

### Post by mlind on 2006-06-28
[QUOTE=Dr. Nick]not sure if gdebi handles the dependencies. I think it would if the dependencies are in the repos though. I have very limited usage of it, but in that time have never had a problem with it.

It may just be a gui frontend to one of the others.

Do you have all the universe, multiverse repos enabled?[/QUOTE]

I'd like to stay away from apt gui's as much as possible.

All I would like to is *sudo aptitude install ./my_package.deb* and watch it happily
resolving any dependency problems :(

---

