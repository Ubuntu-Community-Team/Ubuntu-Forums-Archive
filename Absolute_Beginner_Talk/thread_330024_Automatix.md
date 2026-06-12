---
title: "Automatix"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by sheine on 2007-01-02
I used Automatix to install swiftfox and other programs. It solved all the problems that I had with firefox. It did a better job for me than the synaptic package manager.

---

### Post by nickpaton on 2007-01-02
Glad you found Automatix to be of help to you.

It's my package installer of choice, and the developers headed up by Arnieboy continue to do an excellent job in maintaining and adding to the packages and their dependencies which can be loaded.

This is where in one sense it differs from Synaptic, which simply lists all programs available for download via the repositories and doesn't always help with what dependencies are needed to install and run certain programs.

Automatix on the other hand has its own set of repos and concentrates on offering the more 'difficult' or more common programs together with all the necessary dependencies 'automatically' built in. - no more searching as can sometimes be the case with Synaptic.

Don't forget Easy Ubuntu either.

---

### Post by xpod on 2007-01-02
> It's my package installer of choice

Same here!

Who needs them "proper" ways when you got AX eh...lol::rolleyes: 

Especially for some newcomer who`s mabey  been through a day or 2 of drama just getting the bloody iso burnt and installed.

Synaptic etc are all great and all but it can take some navigating and figuring if your just new to it all......hell just "finding" it can be a trial in itself for  some.:D 
If it`s about making those initial hours & days as simple and painless as possible for people then AX is certainly the tool for the job.

The only thing i do the "proper" way on a fresh install is my nvidia drivers but everything else i need i i get from ax.......

where is synaptic again:confused:

EDIT:All the time in the world for the "proper" ways i reckon

---

### Post by earobinson on 2007-01-02
Im pretty sure this should be in the [Ubuntu Testimonials]("http://www.ubuntuforums.org/forumdisplay.php?f=103") sub forum .... we dont seem to have one for Automatix ... we did at one point ... mods msged

Edit: they have there own forum [http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

---

### Post by bigken on 2007-01-02
yep why struggle when you can use **AUTOMATIX **makes life very easy ;)

---

### Post by in_flu_ence on 2007-01-02
Automatix helps alot especially on getting some issue solved in 64bit systems. That's why it is always said that it complets the ubuntu system.

Does Fedora or Suse has something similar to automatix? It just make ubuntu 'more superior' in terms of user-friendliness.

---

### Post by earobinson on 2007-01-03
I have never seen anything as close as automatix in fedora or suse

---

### Post by sheine on 2007-01-04
Another program that has not worked correctly for me before Automatix is "wine".

---

### Post by joeally on 2007-01-04
Automatix crashed while trying to install somthing now i cant install anything from it or ubuntu's standard add/remove on most things all though i have managed to install google earth since the fatal crash but thats about it  ](*,) 

It says that there is an apt based error

can anyone help me fix this problem

Thanks 
Joe

---

### Post by Bachstelze on 2007-01-04
No, we can't unless you paste the exact error :)

---

### Post by firephoto on 2007-01-04
> **sheine said:**
> Another program that has not worked correctly for me before Automatix is "wine".
This always has worked 100% for me.
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

That and about 5 other repos seems to get me everything.

If Synaptic isn't pulling in dependencies correctly it's a bug and should be reported.

---

### Post by 2CV67 on 2007-01-05
Hi & please excuse dumb noobie question....

So far I am very happy with Synaptic Package Manager & would not want to be without it.

Yesterday I was pointed towards Automatix for installing JRE (that's fixed OK with Synaptic now) but I stopped when I looked through FAQ on Automatix site & saw:
"Please do not attempt to install any other software or run updates while running Automatix2. If you try to do so, Automatix2 will throw an error and exit."

I was not too sure what they meant by "running" (actually loading something, or just running in the background?).

Can somebody please clear up for me whether I have to choose once & for all between Synaptic & Automatix, or if I can have both & use both as long as I am not actually trying to load with both simultaneously?

Thanks guys!

---

### Post by rovernaut on 2007-01-05
When running Automatix you can't run Adept or Synaptic or any other package managers at the same time

---

### Post by 2CV67 on 2007-01-05
Yes but I still don't know what you & they mean by "running"...

Does that mean "having on my PC & using sometimes" or does it mean "actually having the application open & actually using it at this very moment to install or uninstall somthing"?

I would never think of actually using both Synaptic & Automatix to install things at the exact same time, but I want to know if I can have both of them available (and also EasyUbuntu?) & choose which one to use each time I want to install something and not have them all screwing each other up, by losing track of what I have installed or some other incompatibility.

Thanks again!

---

### Post by livingtarget on 2007-01-05
Only while it's busy, i.e.: you are installing something, updating your sources or something like that. 

You can have the update manager and synaptic open at the same time, but you can't install something in synaptic while the update manager is fetching new sources for example.

---

### Post by arnieboy on 2007-01-05
> **joeally said:**
> Automatix crashed while trying to install somthing now i cant install anything from it or ubuntu's standard add/remove on most things all though i have managed to install google earth since the fatal crash but thats about it  ](*,) 

It says that there is an apt based error

can anyone help me fix this problem

Thanks 
Joe
try
```
sudo apt-get -f install
```
and paste the errors here

---

